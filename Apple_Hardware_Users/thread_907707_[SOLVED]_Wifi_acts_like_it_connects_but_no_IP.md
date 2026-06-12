---
title: "[SOLVED] Wifi acts like it connects but no IP"
date: 2008-09-01
forum: Apple Hardware Users
---

### Post by m.musashi on 2008-09-01
I have Hardy installed on a iMac G5 I believe (it was purchased in mid 2007). I have been running Ubuntu exclusively since buying it and OSX is not installed at all.

I have had wifi working on this. The issue is that it simply drops the connection after a while or sometimes "connects" but no IP. ifconfig will show that there isn't an IP when there must have been before because all was working fine. The only fix that I have found is rebooting or running sudo killall NetworkManager and then sudo NetworkManager. However, now this isn't really working either. After rebooting NetworkManager connects (the little green lights light up and then it shows 4 bars of signal strength) but again ifconfig shows no IP address for wlan0.

The odd thing is that NM will still show signal strength bars and if you disconnect and reconnect it will act like it does but still not get an IP. One though is that NM is just crashing but if so I would think that I would not be able to connect to a different network or reconnect but it will or at least used to. Now it doesn't seem to be working at all in that I can't get an IP at all even though it still looks connected. That doesn't seem how a program would act if it's crashed. I did have to use ndiswrapper for the driver to work and it's the same process everyone else uses when putting Ubuntu on a mac (i.e. I followed one of the popular how tos). I didn't do anything special other than that to get it to work.

One thought is that I don't have OSX running on it and from what I can gather macs need their mommy. It takes a long time to boot because it can't find an OSX partition and then times out and boots what it can find. I did some research and found something called rEFIt, I think. It is a boot loader for EFI based computers which I don't really understand but apparently a mac is one. Could this be at all related to the problem? If not, any ideas what's going on, why and how to fix?

Thanks.

---

### Post by cyberdork33 on 2008-09-01
> **m.musashi said:**
> I did some research and found something called rEFIt, I think. It is a boot loader for EFI based computers which I don't really understand but apparently a mac is one. Could this be at all related to the problem? If not, any ideas what's going on, why and how to fix?
If you have a G5 iMac then rEFIt will not work for you. It is only for Intel-based Macs.

---

### Post by m.musashi on 2008-09-01
> **cyberdork33 said:**
> If you have a G5 iMac then rEFIt will not work for you. It is only for Intel-based Macs.

My mistake. It's definitely an intel mac. I'm just not sure what the official model is. From /proc/cpuinfo

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz
stepping	: 6
cpu MHz		: 1000.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4332.21
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz
stepping	: 6
cpu MHz		: 1000.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4327.53
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:
```

and from lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
```

Any help with the wifi issue would be appreciated. I've been searching for quite a while for a solution and haven't had much luck. I just install the Wicd network tool in place of NetworkManager but it's not connecting either. I think I will reinstall the driver and see if that helps.

---

### Post by cyberdork33 on 2008-09-02
> **m.musashi said:**
> My mistake. It's definitely an intel mac. I'm just not sure what the official model is.
In that case, rEFIt will work fine, but you don't need it necessarily... (and it is really installed in OSX. What you want to do is 'bless' the ubuntu partition so that the EFI loader boots it by default without looking for other items. You will need OSX to do this (booting from your OSX install dvd will work. From the FAQ:
[http://ubuntuforums.org/showpost.php?p=5166788&postcount=21](http://ubuntuforums.org/showpost.php?p=5166788&postcount=21)

For information on determining your model version see the "Before You Post" link in my signature.

What windows driver did you use for ndiswrapper?

---

### Post by m.musashi on 2008-09-02
> **cyberdork33 said:**
> In that case, rEFIt will work fine, but you don't need it necessarily...

Okay, I installed this anyway. At the very least it's supposed to make Linux boot faster so that's a plus.

> For information on determining your model version see the "Before You Post" link in my signature.

What windows driver did you use for ndiswrapper?

It's an iMac 5,1. The driver I used came from these instructions:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

As for the driver I used step 2d which I believe installs bcmwl5.inf. I also noted that there may be a broadcom driver available but I'm not clear if it works for the BCM4328 or even how to install it if it does.

> Cisco#2(José Pagola)..it seems that broadcom launch a propietary 
driver that support the BCM-4328, [http://www.broadcom.com/support/802.11](http://www.broadcom.com/support/802.11)
/linux_sta.php, BTW bcm4328 is the PCI ID not the chip ID the real chip 
ID for this wifi card is bcm-4321(you can see this on this link 
[http://linuxwireless.org/en/users/Drivers/b43#unsupported](http://linuxwireless.org/en/users/Drivers/b43#unsupported), unsupported 
for bcm43xx linux-driver but not for the propietary), and bcm4321 based 
chip are suppoted for the propietary broadcom's linux-driver.

-from [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa) about halfway down

Exciting news if it's really a linux driver for this chipset.

Thanks for the help.

---

### Post by cyberdork33 on 2008-09-02
> **m.musashi said:**
> Okay, I installed this anyway. At the very least it's supposed to make Linux boot faster so that's a plus.well, blessing the ubuntu partition is likely the only speedup you will get.

> **m.musashi said:**
> It's an iMac 5,1. The driver I used came from these instructions:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

As for the driver I used step 2d which I believe installs bcmwl5.inf. I also noted that there may be a broadcom driver available but I'm not clear if it works for the BCM4328 or even how to install it if it does.They are all "broadcom" drivers, just distributed by various vendors. (and they are all named bcmwl5.inf). If the one you have seems to be working then stick with it. This is the same Dell driver that we have been using for awhile on these machines. If you feel adventurous you can try to replace it with the BootCamp driver.
I don't know why it does anything with wpa_supplicant. You shouldn't need to mess with that just network-manager. 

After attempting to connect via network-manager, you can check the end of 'dmesg' for information on the connection process. If it looks like the encryption is associating and all correctly, then it is likely a problem with your router / dhcp server not giving your machine an ip for some reason.

> **m.musashi said:**
> Exciting news if it's really a linux driver for this chipset
These cards (802.11n capable) are not supported by that driver yet. It does seem to work OK on older cards though.

---

### Post by m.musashi on 2008-09-02
> **cyberdork33 said:**
> well, blessing the ubuntu partition is likely the only speedup you will get.

The speedup is from rEFIt booting Linux without waiting for the mac to give up looking for a mac partition. In the past it took a good 20sec of sitting on a white screen before it would finally decide to boot Linux. Now it will boot in 5 secs or so. If you have a dual boot this is probably not an issue but for a Linux only Mac it seems to help.

Btw, I tried the "blesing" thing and I couldn't get it to do anything. I probably did something wrong. I followed [http://ubuntuforums.org/showpost.php?p=5166788&postcount=21](http://ubuntuforums.org/showpost.php?p=5166788&postcount=21).

> They are all "broadcom" drivers, just distributed by various vendors. (and they are all named bcmwl5.inf). If the one you have seems to be working then stick with it. This is the same Dell driver that we have been using for awhile on these machines. If you feel adventurous you can try to replace it with the BootCamp driver.
I don't know why it does anything with wpa_supplicant. You shouldn't need to mess with that just network-manager.

Well, then I'm not sure which driver. I keep searching for something newer than the dell one everyone points to but I guess in the end that is what I got. It works but it worked before too. Eventually I get the problem described in the OP. It works for a while and then starts to drop the connection even though NM still shows it connected. The computer just doesn't have an IP anymore.

> After attempting to connect via network-manager, you can check the end of 'dmesg' for information on the connection process. If it looks like the encryption is associating and all correctly, then it is likely a problem with your router / dhcp server not giving your machine an ip for some reason.

I solved this by just reinstalling the whole thing and adding the rEFIt for whatever that is worth. This is my third time to do this so I won't be surprised if in a few months it's starts to drop the connection again or fail to grab an IP from the router even though NetworkManager says it connected.

I'm not sure how this would be a router problem as no other computer in the house has a problem connecting including an eee running Ubuntu and my wife's dell laptop also running ubuntu (both wireless) and my desktop running Ubuntu but wired. Only this iMac has issues. My guess is it's something with the driver or the ndiswrapper implementation. I did see mention of a similar problem on the wiki

> Deng11: For me, the ndiswrapper -m command seems to be enough. 
Actually, putting ndiswrapper into /etc/modules made things worse for me 
(I couldn't get an IP address anymore via my WPA-secured connection after 
reboot - as usual, you mileage may vary, so just try what works best for you).

-from [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

Thanks for all the help. I think for now this is resolved but I won't be surprised if the same problem returns.

---

