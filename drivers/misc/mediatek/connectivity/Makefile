#
# Copyright (C) 2015 MediaTek Inc.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#

# Connectivity combo driver
subdir-ccflags-y += -I$(srctree)/
subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/base/power/include
subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/clkbuf/src
subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/base/power/include/clkbuf_v1/$(MTK_PLATFORM)
subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/include/mt-plat/$(MTK_PLATFORM)/include
subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/include/mt-plat
ifeq ($(CONFIG_MTK_PMIC_CHIP_MT6359),y)
subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/pmic/include/mt6359
endif
ifeq ($(CONFIG_MTK_PMIC_NEW_ARCH),y)
subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/pmic/include
endif
subdir-ccflags-y += -I$(srctree)/drivers/mmc/core
subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/eccci/$(MTK_PLATFORM)
subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/eccci/
subdir-ccflags-y += -I$(srctree)/drivers/clk/mediatek/
subdir-ccflags-y += -I$(srctree)/drivers/pinctrl/mediatek/
subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/power_throttling/

# Do Nothing, move to standalone repo
MODULE_NAME := connadp
obj-$(CONFIG_MTK_COMBO) += $(MODULE_NAME).o

$(MODULE_NAME)-objs += common/connectivity_build_in_adapter.o
$(MODULE_NAME)-objs += common/wmt_build_in_adapter.o
$(MODULE_NAME)-objs += power_throttling/adapter.o
$(MODULE_NAME)-objs += power_throttling/core.o
ifeq ($(CONFIG_CONN_PWR_DEBUG),y)
    $(MODULE_NAME)-objs += power_throttling/test.o
endif

ifeq ($(CONFIG_MTK_COMBO), y)
    ccflags-y += -D CFG_CONNADP_BUILD_IN
endif

export CONFIG_WLAN_DRV_BUILD_IN=y

ifeq ($(CONFIG_WLAN_DRV_BUILD_IN),y)
# for gen4m options
export CONFIG_MTK_COMBO_WIFI_HIF=axi
export MTK_COMBO_CHIP=SOC2_1X1
export BT_PLATFORM=connac1x
export WLAN_CHIP_ID=6833
export MTK_ANDROID_WMT=y
export MTK_ANDROID_EMI=y
export WIFI_IP_SET=1
export MTK_WLAN_SERVICE=yes
export CONNAC_VER=1_0

# Do build-in for xxx.c checking
subdir-ccflags-y += -D MTK_WCN_REMOVE_KERNEL_MODULE
subdir-ccflags-y += -D MTK_WCN_BUILT_IN_DRIVER
endif

obj-$(CONFIG_MTK_COMBO) += common/
obj-$(CONFIG_MTK_COMBO_WIFI) += wlan/adaptor/
obj-$(CONFIG_MTK_COMBO_CHIP_CONSYS_6833) += wlan/core/gen4m/
obj-$(CONFIG_MTK_BTIF) += bt/mt66xx/wmt/
obj-$(CONFIG_MTK_COMBO_GPS) += gps/
obj-$(CONFIG_MTK_FMRADIO) += fmradio/
obj-$(CONFIG_MTK_CONNFEM) += connfem/
