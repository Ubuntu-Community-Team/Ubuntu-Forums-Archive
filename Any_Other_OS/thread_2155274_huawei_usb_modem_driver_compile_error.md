---
title: "huawei usb modem driver compile error"
date: 2013-06-17
forum: Any Other OS
---

### Post by deepclutch on 2013-06-17
[FONT=Tahoma][SIZE=3]I have a e303c huawei modem[SIZE=3]. it[SIZE=3] is already supporte[SIZE=3]d by [SIZE=3]kernel and Networkmanager[SIZE=3] automagically connects to net.

[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT]I am trying to install *Official* Huawei usb modem's Linux driver [SIZE=3]inorder to get "Mobile partner" dashboard[/SIZE]. it comes with a install command with contents like this:
[http://ur1.ca/ecs4v](http://ur1.ca/ecs4v)
installation procedure: [http://pastebin.com/njUZQLa9](http://pastebin.com/njUZQLa9)

[SIZE=3]Error[SIZE=3]:
```
[/SIZE][/SIZE][SIZE=3][SIZE=3][FONT=Tahoma][SIZE=3]
modprobe hw_cdc_driver FATAL: Module hw_cdc_driver not found. make[1]: *** [install] Error 1 make[1]: Leaving directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src' make: *** [install] Error 2  **Install NDIS driver failed.** The compiling environment is not all ready. Please check gcc, make and kernel buid(/lib/modules/3.5.2-1.fc17.x86_64/build) to be all installed? Now please enter any key to finish other installations.  NDIS is disabled, and only Modem can be used.[/SIZE][/FONT]
```
[/SIZE][/SIZE]
[FONT=Tahoma][SIZE=3]I am on fedora 17 with 3.5.2-1.fc17.x86_64 kernel and with kernel-devel,kernel-headers,kernel-modules-extra installed.

gcc matches the kernel. even "make" is latest.

however, if I try to install, script fails to compile **hw_cdc_driver** and throws below error messages:
[http://www.fpaste.org/19241/](http://www.fpaste.org/19241/)



please help. I have to reinstall usb-modeswitch and couple of other  packages to get the modem works every time I compile this huawei driver.  means, the dongle is supported by the kernel, but I want to use mobile  partner software which fails to load. any help. [/SIZE][/FONT]

---

