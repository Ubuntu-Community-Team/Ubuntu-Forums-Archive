---
title: "Problem with rtl8723bs wifi SDIO on Android"
date: 2017-05-23
forum: Any Other OS
---

### Post by tepmehatop on 2017-05-23
[FONT=Verdana]Hello, and have a nice day![/FONT]
[FONT=Verdana]I have Freescale IMX6q sabresd. and Android 4.3 on it.[/FONT]
[FONT=Verdana]Trying to connect SDIO wifi rtl8723bs. All configuratoin i do from manual with rtl8723bs.[/FONT]
[FONT=Verdana]Compiling the driver as module, then put it system/lib/modules and load by insmod. No warning then i load the module, but wifi is not working.If execute the netcfg or ifconfig, there is no wifi.[/FONT]
[FONT=Verdana]One obscure thing: My driver consists only of:[/FONT]
**8723bs.ko**
[FONT=Verdana]Other drivers consist of:[/FONT]


**cfg80211.ko **
**compact.ko**


[FONT=Verdana]Where to get the cfg80211.ko and compact.ko for my driver? how to compile them?[/FONT]


[FONT=Verdana]Here is log:[/FONT]
[FONT=Verdana]> D/MtpServer( 2941): path: /storage/emulated/0/87238723bs2.ko parent: 0 storageID: 00[/FONT]> 
[FONT=Verdana]010001[/FONT]
[FONT=Verdana]I/wpa_supplicant( 3598): Successfully initialized wpa_supplicant[/FONT]
[FONT=Verdana]D/MtpService( 2941): updating state; isCurrentUser=true, mMtpLocked=false[/FONT]
[FONT=Verdana]D/MtpService( 2941): addStorageLocked 65537 /storage/emulated/0[/FONT]
[FONT=Verdana]D/MtpService( 2941): updating state; isCurrentUser=true, mMtpLocked=false[/FONT]
[FONT=Verdana]D/MtpService( 2941): starting MTP server in MTP mode[/FONT]
[FONT=Verdana]D/MtpService( 2941): addStorageLocked 65537 /storage/emulated/0[/FONT]
[FONT=Verdana]D/BluetoothAdapter( 2927): 1102533832: getState() : mService = null. Returning[/FONT]
[FONT=Verdana]STATE_OFF[/FONT]


[FONT=Verdana]The another problem is, then i trying to compile driver, i got warnings[/FONT]


[FONT=Verdana]> Building modules, stage 2.MODPOST 1 modulesWARNING: "cfg80211_del_sta" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_mgmt_tx_status" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "wiphy_apply_custom_regulatory" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "ieee80211_frequency_to_channel" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_rx_mgmt" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_new_sta" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_connect_result" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_unlink_bss" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "wiphy_new" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_put_bss" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_roamed" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_scan_done" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_ibss_joined" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_michael_mic_failure" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_disconnected" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_get_bss" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_inform_bss_frame" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "wiphy_free" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "__ieee80211_get_channel" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_ready_on_channel" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "wiphy_unregister" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "cfg80211_remain_on_channel_expired" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!WARNING: "wiphy_register" [/home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko] undefined!CC /home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.mod.oLD [M] /home/mark/Android/opt/kernel_imx/drivers/net/wireless/rtl8723bs/8723bs.ko[/FONT]


[FONT=Verdana]
step by step, go to driver folder[/FONT]
[FONT=Verdana]make clean[/FONT]
[FONT=Verdana]make[/FONT]


[FONT=Verdana]Here is my configuratoin of my makefile in driver:[/FONT]


[FONT=Verdana]```
ifeq ($(CONFIG_PLATFORM_FSL_IMX6Q), y)
```[/FONT]```

[FONT=Verdana]EXTRA_CFLAGS += -DCONFIG_LITTLE_ENDIAN[/FONT]
[FONT=Verdana]EXTRA_CFLAGS += -DRTW_USE_CFG80211_STA_EVENT -DCONFIG_IOCTL_CFG80211 [/FONT]
[FONT=Verdana]ARCH := arm[/FONT]
[FONT=Verdana]CROSS_COMPILE := /home/mark/Android/opt/prebuilts/gcc/linux-x86/arm/arm-eabi-4.7/bin/arm-eabi-[/FONT]
[FONT=Verdana]KSRC := /home/mark/Android/opt/kernel_imx[/FONT]
[FONT=Verdana]MODULE_NAME := 8723bs[/FONT]
[FONT=Verdana]endif[/FONT]

```

[FONT=Verdana]if i delete or comment the -DCONFIG_IOCTL_CFG80211 [/FONT]
[FONT=Verdana]the driver compile without any warnings.[/FONT]


[FONT=Verdana]I traed 3-5 different drivers drom github, but all they the same problem......[/FONT]


[FONT=Verdana]Hope for any tips, help from you[/FONT]
[FONT=Verdana]Thank's[/FONT]


[FONT=Verdana]Here my configs:[/FONT]

[FONT=Verdana]```
CONFIG_CFG80211=m 
```[/FONT]```

[FONT=Verdana]CONFIG_MAC80211_MESH=y [/FONT]
[FONT=Verdana]CONFIG_MAC80211=y [/FONT]
[FONT=Verdana]CONFIG_HOSTAP=y [/FONT]
[FONT=Verdana]CONFIG_RTL8723BS=m[/FONT]

```


[FONT=Verdana]BoardConfig.mk[/FONT]
```

[FONT=Verdana]BOARD_WIFI_VENDOR := realtek[/FONT]
[FONT=Verdana]ifeq ($(BOARD_WIFI_VENDOR), realtek)[/FONT]
[FONT=Verdana]WPA_SUPPLICANT_VERSION := VER_0_8_X[/FONT]
[FONT=Verdana]BOARD_WPA_SUPPLICANT_DRIVER := NL80211[/FONT]
[FONT=Verdana]CONFIG_DRIVER_WEXT :=y[/FONT]
[FONT=Verdana]BOARD_WPA_SUPPLICANT_DRIVER := WEXT[/FONT]
[FONT=Verdana]BOARD_WPA_SUPPLICANT_PRIVATE_LIB := lib_driver_cmd_rtl[/FONT]
[FONT=Verdana]BOARD_HOSTAPD_DRIVER:= NL80211[/FONT]
[FONT=Verdana]BOARD_HOSTAPD_PRIVATE_LIB := lib_driver_cmd_rtl[/FONT]


[FONT=Verdana]BOARD_WLAN_DEVICE := rtl8723bs[/FONT]
[FONT=Verdana]#BOARD_WLAN_DEVICE := rtl8192du[/FONT]
[FONT=Verdana]#BOARD_WLAN_DEVICE := rtl8192ce[/FONT]
[FONT=Verdana]#BOARD_WLAN_DEVICE := rtl8192de[/FONT]
[FONT=Verdana]#BOARD_WLAN_DEVICE := rtl8723as[/FONT]
[FONT=Verdana]#BOARD_WLAN_DEVICE := rtl8723au[/FONT]
[FONT=Verdana]#BOARD_WLAN_DEVICE := rtl8189es[/FONT]
[FONT=Verdana]#BOARD_WLAN_DEVICE := rtl8723bs[/FONT]
[FONT=Verdana]#BOARD_WLAN_DEVICE := rtl8723bu[/FONT]


[FONT=Verdana]WIFI_DRIVER_MODULE_NAME := "8723bs"[/FONT]
[FONT=Verdana]WIFI_DRIVER_MODULE_PATH := "/system/lib/modules/8723bs.ko"[/FONT]
[FONT=Verdana]WIFI_DRIVER_MODULE_ARG:= "ifname=wlan0 if2name=p2p0"[/FONT]


[FONT=Verdana]WIFI_FIRMWARE_LOADER := ""[/FONT]
[FONT=Verdana]WIFI_DRIVER_FW_PATH_STA := ""[/FONT]
[FONT=Verdana]WIFI_DRIVER_FW_PATH_AP:= ""[/FONT]
[FONT=Verdana]WIFI_DRIVER_FW_PATH_P2P := ""[/FONT]
[FONT=Verdana]WIFI_DRIVER_FW_PATH_PARAM := ""[/FONT]
[FONT=Verdana]endif[/FONT]
```
[FONT=Verdana]init.xxx.rc[/FONT]

```

[FONT=Verdana]service rtw_suppl_con /system/bin/wpa_supplicant [/FONT]
[FONT=Verdana]-ip2p0 -Dnl80211 -c /data/misc/wifi/p2p_supplicant.conf -e/data/misc/wifi/entropy.bin -N [/FONT]
[FONT=Verdana]-iwlan0 -Dnl80211 -c/data/misc/wifi/wpa_supplicant.conf [/FONT]
[FONT=Verdana]class main [/FONT]
[FONT=Verdana]socket wpa_wlan0 dgram 660 wifi wifi [/FONT]
[FONT=Verdana]disabled [/FONT]
[FONT=Verdana]oneshot [/FONT]


[FONT=Verdana]service rtw_suppl /system/bin/wpa_supplicant -iwlan0 -Dnl80211 [/FONT]
[FONT=Verdana]-c/data/misc/wifi/wpa_supplicant.conf [/FONT]
[FONT=Verdana]socket wpa_wlan0 dgram 660 wifi wifi [/FONT]
[FONT=Verdana]class main [/FONT]
[FONT=Verdana]disabled [/FONT]
[FONT=Verdana]oneshot[/FONT]
```
[FONT=Verdana]Set wifi.interface[/FONT]

```

[FONT=Verdana]PRODUCT_PROPERTY_OVERRIDES += [/FONT]
[FONT=Verdana]wifi.interface=wlan0[/FONT]
```
[FONT=Verdana]Apply wifi_realtek.c[/FONT]

```

[FONT=Verdana]ifeq ($(BOARD_WIFI_VENDOR), realtek) [/FONT]
[FONT=Verdana]LOCAL_SRC_FILES += ../realtek/wlan/libhardware_legacy/wifi/wifi_realtek.c [/FONT]
[FONT=Verdana]else [/FONT]
[FONT=Verdana]LOCAL_SRC_FILES += wifi/wifi.c [/FONT]
[FONT=Verdana]endif[/FONT]
```
[FONT=Verdana]wpa_supplicant_8[/FONT]


[FONT=Verdana]```
ifeq ($(BOARD_WIFI_VENDOR), realtek) 
```[/FONT]```

[FONT=Verdana]L_CFLAGS += -DREALTEK_WIFI_VENDOR [/FONT]
[FONT=Verdana]L_CFLAGS += -DANDROID_P2P [/FONT]
[FONT=Verdana]L_CFLAGS += -DCONFIG_ANDROID_4_2_PERSISTENT_IOT [/FONT]
[FONT=Verdana]Endif[/FONT]
```
[FONT=Verdana]Adding or Selecting Target Platform opt/kernel_imx/drivers/net/wireless/rtl8723bs/makefile[/FONT]

```

[FONT=Verdana]CONFIG_PLATFORM_FSL_IMX6Q = y [/FONT]
[FONT=Verdana]CONFIG_PLATFORM_I386_PC = n [/FONT]
[FONT=Verdana]CONFIG_PLATFORM_ANDROID_X86 = n [/FONT]
[FONT=Verdana]CONFIG_PLATFORM_ARM_S3C2K4 = n [/FONT]
[FONT=Verdana]CONFIG_PLATFORM_ARM_PXA2XX = n [/FONT]
[FONT=Verdana]CONFIG_PLATFORM_ARM_S3C6K4 = n [/FONT]
[FONT=Verdana]CONFIG_PLATFORM_MIPS_RMI [/FONT]
[FONT=Verdana]= n [/FONT]
[FONT=Verdana]CONFIG_PLATFORM_RTD2880B [/FONT]
[FONT=Verdana]= n [/FONT]
[FONT=Verdana]CONFIG_PLATFORM_MIPS_AR9132 = n [/FONT]
[FONT=Verdana]CONFIG_PLATFORM_MT53XX [/FONT]
[FONT=Verdana]= n [/FONT]
[FONT=Verdana]CONFIG_PLATFORM_RTK_DMP [/FONT]
[FONT=Verdana]= n[/FONT]
```
[FONT=Verdana]opt/kernel_imx/drivers/net/wireless/Makefile[/FONT]
[FONT=Verdana]```
obj-$(CONFIG_RTL8723AS) += rtl8723as/
```[/FONT]
[FONT=Verdana]opt/kernel_imx/drivers/net/wireless/Kconfig[/FONT]


[FONT=Verdana]```
source "drivers/net/wireless/rtl8723bs/Kconfig"
```[/FONT]

---

### Post by howefield on 2017-05-23
Thread moved to the "*Any Other OS*" forum.

---

