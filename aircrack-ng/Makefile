#
# Copyright (C) 2006-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=aircrack-ng
PKG_VERSION:=1.2-rc2
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://download.aircrack-ng.org/ \
		http://archive.aircrack-ng.org/aircrack-ng/$(PKG_VERSION)/
PKG_HASH:=ba5b3eda44254efc5b7c9f776eb756f7cc323ad5d0813c101e92edb483d157e9

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

PKG_MAINTAINER:=hashashin <gentoo.power@gmail.com>

include $(INCLUDE_DIR)/package.mk

define Package/aircrack-ng
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libpcap +libpthread +libopenssl +libnl-core +libnl-genl +zlib
  TITLE:=WLAN tools (without airmon-ng) for breaking 802.11 WEP/WPA keys
  URL:=http://www.aircrack-ng.org/
  SUBMENU:=wireless
endef

define Package/aircrack-ng/description
  WLAN tools for breaking 802.11 WEP/WPA keys
endef

define Package/airmon-ng
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+wireless-tools +ethtool +procps-ng +CONFIG_PCI_SUPPORT:pciutils +CONFIG_USB_SUPPORT:usbutils
  TITLE:=Bash script designed to turn wireless cards into monitor mode.
  URL:=http://www.aircrack-ng.org/
  SUBMENU:=wireless
endef

define Package/airmon-ng/description
  Bash script designed to turn wireless cards into monitor mode.
endef

MAKE_FLAGS += prefix=/usr \
	libnl=true \
	sqlite=false \
	unstable=false \
	OSNAME=Linux

define Package/aircrack-ng/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/* $(1)/usr/sbin/
	rm -f $(1)/usr/sbin/airmon-ng
endef

define Package/airmon-ng/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/airmon-ng $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,aircrack-ng))
$(eval $(call BuildPackage,airmon-ng))
