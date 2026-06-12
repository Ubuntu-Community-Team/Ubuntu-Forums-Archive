---
title: "Wireless Driver?"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Air_Scythe on 2008-04-16
Hello, and first of all thanks for the forums. When ever i login to ubuntu, i find that I have to enter my wep key, before it can connect to the internet. How ever when i go into system/administration/network tools and when i click on the drop box next to "Network device" i find there is something called "unknown interface (wmaster0)". I cant configure this device and im wondering if is is this device that is creating my problem.

---

### Post by neurostu on 2008-04-16
I'm not sure, as I have never encountered ta wmaster0 before. But i have to enter in my password everytime I want to log into my wireless router.

---

### Post by chazdraves on 2008-04-16
I'm afraid I couldn't tell you either what wmaster0 is, but I know I've got it as well. What I do know is that by default Ubuntu always asks for the password before logging in. If there's a setting in the GUI to disable this, I'm not aware of this. I'm sure there's a command you could set to run at start-up that would run that for you? Someone should know here.

Good luck!
- Chaz

---

### Post by hyper_ch on 2008-04-16
run a lspci (if it's a pci device) or lsusb (if it's a usb device) and post the output here.

---

### Post by raoufathar on 2008-04-16
I am also trying to use my "AR5006EG 802.11 b/g Wireless PCI Express Adapter".

No way i can find to get it done.

Somebody help me get my wireless drivers installed properly.

---

### Post by hyper_ch on 2008-04-16
> **raoufathar said:**
> I am also trying to use my "AR5006EG 802.11 b/g Wireless PCI Express Adapter".

No way i can find to get it done.

Somebody help me get my wireless drivers installed properly.

(1) Open a sepearte thread on your issue

(2) in that seperate thread post the output of
```

lspci

```

---

### Post by raoufathar on 2008-04-16
raouf@Kasheer:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Air_Scythe on 2008-04-17
Ok, i also have to enter my pword everytime, thanks for the help i thought there was something wrong with my ubuntu.

---

