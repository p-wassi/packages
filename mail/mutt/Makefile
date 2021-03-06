#
# Copyright (C) 2006-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mutt
PKG_VERSION:=1.11.1
PKG_RELEASE:=1

PKG_SOURCE_URL:=ftp://ftp.mutt.org/pub/mutt/ \
		https://bitbucket.org/mutt/mutt/downloads/
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_HASH:=705141013662e53b78e49ed545360281f30a09ddda908f4de733277a60b1db05

PKG_MAINTAINER:=Phil Eichinger <phil@zankapfel.net>
PKG_LICENSE:=GPL-2.0+
PKG_LICENSE_FILES:=GPL

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/mutt
  SECTION:=mail
  CATEGORY:=Mail
  DEPENDS:=+libopenssl +libncursesw +terminfo +zlib
  TITLE:=Console mail client
  URL:=http://www.mutt.org/
endef

define Package/mutt/description
	Mutt is a small but very powerful text-based mail client for Unix
	operating systems.
endef

CONFIGURE_ARGS += \
	--includedir=$(PKG_BUILD_DIR)/. \
	--oldincludedir=$(PKG_BUILD_DIR)/. \
	--enable-pop \
	--enable-imap \
	--with-ssl \
	--without-idn \
	--disable-doc

define Package/mutt/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mutt $(1)/usr/bin/
endef

$(eval $(call BuildPackage,mutt))
