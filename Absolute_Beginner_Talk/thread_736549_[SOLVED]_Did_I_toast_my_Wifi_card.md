---
title: "[SOLVED] Did I toast my Wifi card?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by drewster1829 on 2008-03-26
I was having trouble the other day on my Toshiba Satellite M55-S331 with the Wireless network card (Intel PRO/Wireless 2200BG).  It all started after I (foolishly) hibernated the thing one day, then rebooted.

Just after POST, it would give me "Device Conflict" Network Card Adapter something...device 06 socket 02 or something like that.  The wireless card quit working at this point, and the *only* thing I could seem to do to remove the message was take out the card.  I had just installed 1GB of RAM the day before, but removing the RAM chip didn't help any.

While trying to fix this, I accidentally toasted the partition table with the Toshiba Recovery disk (apparently when booting it, it sometimes gives no prompt or warning, but immediately formats the drive and starts copying it's MS Winblows and Bloatware to it), so I had to reinstall Ubuntu.

The old install was 7.04 upgraded to 7.10, and this time I tried 8.04 Beta.  I no longer got the conflict during boot (after re-installing the card), but it still wouldn't work in Ubuntu.

Here's the system log:
> 
dmesg | grep 2200
[   15.008000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   15.008000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   15.008000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   15.176000] ipw2200: dmaWaitSync Failed
[   15.176000] ipw2200: Unable to load boot firmware: -1
[   15.176000] ipw2200: Unable to load firmware: -1
[   15.176000] ipw2200: failed to register network device
[   15.176000] ipw2200: probe of 0000:06:02.0 failed with error -5


eth1 doesn't come up anywhere, and I figured it might be a problem with 8.04 Beta (silly me), so I reinstalled 7.10 with the alternate CD, but I get the exact same message.  I'm still using kernel 2.6.22-14-generic (I'm not sure which kernel it was when it was 7.04 upgraded to 7.10...)

Am I crazy?  Is the card toast?  Do I need to (heaven forbid) re-compile the kernel?  Also, an explanation of the "-1" code after "Unable to load boot firmware:" would be great, if anyone has it.  Thanks in advance!

---

### Post by ubrox on 2008-03-26
Hi,

Check your card in windows to make sure it is working. From the logs you sent, it does not look like its toast. 

You need to install linux-restricted-modules package

sudo apt-get install linux-restricted-modules

The card needs a firmware to function that is not distributed by ubuntu by defaut. 

Also check in System->administration->hardware drivers to see if you can enable the use of the restricted driver for your card.

Thanks,
Kalyan

---

### Post by ferdostar on 2008-03-26
Can you post the output of 
```
lshw -C network
```
and
```
ifconfig
```
```
iwconfig
```

---

### Post by Rocket2DMn on 2008-03-26
I have this card and it works out of the box in Feisty, Gutsy, and Hardy for sure.  It is possible the firmware got messed up and needs to be reloaded.  This can probably be done through windows, but I think it can also be done through Ubuntu.  When I did a test install of CentOS on a laptop with this card it told me I needed to install firmware to it, but I passed that up since it worked out of the box in Ubuntu, I didn't want to risk it.
If the card were really toast, you would probably be getting hardware related errors.

---

### Post by Whiffle on 2008-03-26
I'm pretty sure the firmware gets loaded from /lib/firmware every time the card gets activated.

I don't think its toasted though.  You said you hibernated and then rebooted, maybe the bios is confused for some reason.  

In this thread, someone had that error and turned off acpi and it worked;
[http://ubuntuforums.org/showthread.php?t=339693](http://ubuntuforums.org/showthread.php?t=339693)

I did a quick google search and theres quite a few hits for that error, you might try there too.

---

### Post by drewster1829 on 2008-03-26
> **ferdostar said:**
> Can you post the output of 
```
lshw -C network
```
and
```
ifconfig
```
```
iwconfig
```

```
drew@drew-laptop:~$ sudo lshw -C network
[sudo] password for drew:
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:a7:c3:45
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=24 mingnt=3
drew@drew-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:A7:C3:45  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fea7:c345/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:196472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:288098344 (274.7 MB)  TX bytes:10153006 (9.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

drew@drew-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

Like I said, no eth1. :)

Thanks for all the replies!  I did try Google, and most of them suggested installing drivers, firmware, and then recompiling the kernel with the installed modules, but they were for significantly older versions of Ubuntu.

Restricted drivers is enabled, but there were none found for the Wifi card (I think ipw2200 is an open-source driver, but the firmware for the card is proprietary).  I'll keep playing around with it.

---

### Post by drewster1829 on 2008-03-26
> **kalyanakrishna said:**
> Hi,

Check your card in windows to make sure it is working. From the logs you sent, it does not look like its toast. 

You need to install linux-restricted-modules package

sudo apt-get install linux-restricted-modules

The card needs a firmware to function that is not distributed by ubuntu by defaut. 

Also check in System->administration->hardware drivers to see if you can enable the use of the restricted driver for your card.

Thanks,
Kalyan

This did not fix it.  It worked fine with 7.04 (and the subsequent upgrade to 7.10) until I started getting the unexplained Device Conflict error from boot.  Thanks anyway! 

EDIT: I'll try Windows, just as soon as I find a LiveCD of XP. :) I swore off Windows 6 months ago.  I won't use it, even for troubleshooting (and the only valid copy I have is the restore disc, which I'm definitely *not* using.

Oh, that reminds me....the Wifi card doesn't work with the Ubuntu Live CD (any of them), either.  It used to (before I installed Ubuntu, six months ago).  Maybe it is a firmware problem...

---

### Post by drewster1829 on 2008-03-26
> **Whiffle said:**
> 
In this thread, someone had that error and turned off acpi and it worked;
[http://ubuntuforums.org/showthread.php?t=339693](http://ubuntuforums.org/showthread.php?t=339693)

I did a quick google search and theres quite a few hits for that error, you might try there too.

Disabling ACPI results in no change.  I get the exact same message when it tries enable the card.

I usually try Google extensively before resorting to posting in the forums, and *most* of the time, I can figure it out that way.  This was way over my head, however, and I couldn't seem to get it to work.

It looks like it might be a firmware problem...if I had another card to swap out, I could try that.  Now I'm curious. :)

---

### Post by drewster1829 on 2008-03-26
Okay, I'm an idiot. :)  It wasn't fully seated in the slot...but now I have the original problem at POST...

```
Resource Conflict - PCI Network Controller on Motherboard
Bus:06, Device:02, Function:00
```

I still get the error when it tries to load the boot firmware, but the code is -22 instead of -1.

Also, I seem to get this:

```
[   10.061472] PCI: Error while updating region 0000:06:02.0/0 (b8009000 !=a8009000)

```

Now, I've Googled the above message (Resource Conflict) before, but I couldn't find a definitive solution.  Maybe I'll just buy a PC Card Wifi adapter and keep my fingers crossed. :)

EDIT: lshw, ifconfig, and iwconfig are exactly the same.  The only difference is the error at post, the error while updating region, and the changing of the error code from -1 to -22:

```
dmesg|grep 2200
[   25.351533] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   25.351537] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   25.351657] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   26.090259] ipw2200: Unable to load ucode: -22
[   26.090315] ipw2200: Unable to load firmware: -22
[   26.090359] ipw2200: failed to register network device
[   26.090453] ipw2200: probe of 0000:06:02.0 failed with error -5

```

Oh, and I tried disabling ACPI again.  No difference.

---

### Post by Whiffle on 2008-03-26
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/42387](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/42387)

That sounds a little bit like what you might have.

---

### Post by drewster1829 on 2008-03-27
> **Whiffle said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/42387](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/42387)

That sounds a little bit like what you might have.

Wow, thanks!  I'll bet that's it (even thought it's for an older kernel version), since they said they weren't going to fix it.

Apparently, unplugging it and plugging it back in eventually fixed the power state, because I physically re-installed it (for probably the 4th or 5th time) just a second ago, and now it works fine.

:-)

---

