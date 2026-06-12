---
title: "Macbook &amp; Suspend"
date: 2007-03-31
forum: Apple Intel Users
---

### Post by mustang on 2007-03-31
Being that we're getting close to the kernel freeze, I figured I should make this thread sooner rather than later. Some macbooks users (myself included) have NOT gotten suspend to work. It will suspend but it will not wake up.

I know atleast one other 1st generation macbook user, fredconn, is having the same problem as me. I've also heard 2nd generation macbook users say that their resume and wake works fine. 

Could macbook owners please check in stating their kernel version, macbook generation, and use of special tweaks (if any) employed to get suspend working. I'm currently using the fiesty beta, kernel version 2.6.20-13-generic. 

If no success comes out of this thread, would the next stage be to report a bug on launchpad?

edit: **solution on page 4**

---

### Post by fredronn on 2007-04-01
Thanks for starting the thread Mustang.

Using a first generation macbook myself I had very few issues with hardware support overall, Wifi was working from first boot, bluetooth, usb, everything fine. Suspend to ram did not work, including suspend to disk which seemed to halt during shutdown. Suspend to ram will put the machine into sleep, but fails to respond to any attempts to wake it up.

I had problems with suspend using the default kernel shipped with the feisty beta. I've also tried using an older kernel, 2.18 with mactel patches, without success.

---

### Post by david_edmundson on 2007-04-01
I have suspend fully functioning on my macbook (C2D). Running Feisty, no additional patches that I'm aware of.

When you say it doesn't resume, could you check what you mean. I used to have an issue where the backlight didn't come on. To all intends and purposes it seems to have just failed to resume, but in actual fact everything was working except the screen was too black to see it. Peering at the screen at several angles will help determine if you are suffering from the same issue. I know the registers for the backlight changed between version the Macbook 1&2.

---

### Post by siepo on 2007-04-01
I have an original Macbook, and with me sleep doesn't work either. It is not just the backlight staying off: the macbook is totally unresponsive, and an external screen stays black too.

Check [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635) for a bug report which you might want to add to.

---

### Post by Gen2ly on 2007-04-01
I haven't been able to make suspend work either.  I've tried the MacBook-Wiki's:
> sudo ln -bs /bin/true /usr/sbin/laptop-detect

to zero effect.  I was hoping that a kernel upgrade would do it.  I'm using the 2.6.20 kernel with the 2.6.20 mactel patches ( - 0003 jovdev.patch), and it doesn't work.  Is it possible that newer MacBooks are having wake from sleep troubles?  The Wifi Aetheros have someting to do with it?  I can tell you on mine it has to do with the screen - the computer actually wakes from sleep.  If I look very closely at my screen I can see the Enter Password dialog.  I type it in and then am able to shutdown.

---

### Post by Azathoth_ on 2007-04-01
It works by default in Feisty ;)

---

### Post by ronocdh on 2007-04-01
I'm still tinkering with my C2D MBP, but perhaps this'll help you guys: ```
sudo ln -bs /bin/true /usr/sbin/laptop-detect
```I lifted it from this guide: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by fredronn on 2007-04-01
> **ronocdh said:**
> I'm still tinkering with my C2D MBP, but perhaps this'll help you guys: ```
sudo ln -bs /bin/true /usr/sbin/laptop-detect
```I lifted it from this guide: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Nope, nothing wrong with laptop-detect.

---

### Post by mustang on 2007-04-01
> **fredronn said:**
> Thanks for starting the thread Mustang.

Using a first generation macbook myself I had very few issues with hardware support overall, Wifi was working from first boot, bluetooth, usb, everything fine. Suspend to ram did not work, including suspend to disk which seemed to halt during shutdown. Suspend to ram will put the machine into sleep, but fails to respond to any attempts to wake it up.

I had problems with suspend using the default kernel shipped with the feisty beta. I've also tried using an older kernel, 2.18 with mactel patches, without success.

No problem. I've tried a lot of different kernels with the mactel patches but to no success. 

> 
I have suspend fully functioning on my macbook (C2D). Running Feisty, no additional patches that I'm aware of.

When you say it doesn't resume, could you check what you mean. I used to have an issue where the backlight didn't come on. To all intends and purposes it seems to have just failed to resume, but in actual fact everything was working except the screen was too black to see it. Peering at the screen at several angles will help determine if you are suffering from the same issue. I know the registers for the backlight changed between version the Macbook 1&2.


Thanks for replying david. The backlight is absolutely dead---looking at from a different angle doesn't yield anything---it's shut off completely. I actually have to make an addendum to my original post and perhaps fredconn can confirm this---in addition to not waking up, the macbook is not suspending correctly---I can still hear the CPU fan (very light buzz). The hard drive and backlight DO turn off. 

> 
I have an original Macbook, and with me sleep doesn't work either. It is not just the backlight staying off: the macbook is totally unresponsive, and an external screen stays black too.

Check [https://bugs.launchpad.net/ubuntu/+s....20/+bug/92635](https://bugs.launchpad.net/ubuntu/+s....20/+bug/92635) for a bug report which you might want to add to.


Thanks for the link siepo. I think I'll post there and hopefully the devs pick it up. 

Dick & ronocdh: I tried that to no success. Doesn't seem to change anything for me. 

Azathoth_: I wish that were the case for everyone ;)

---

### Post by ronocdh on 2007-04-01
Mustang: in your info, you have yourself listed as a 6.06 user. Are you in fact running Feisty beta?

---

### Post by mustang on 2007-04-01
> **ronocdh said:**
> Mustang: in your info, you have yourself listed as a 6.06 user. Are you in fact running Feisty beta?

Yes :) 

That's just what I'm running on my PC

---

### Post by mustang on 2007-04-01
Quick question regarding posting a bug:

in another suspend bug thread on launchpad, a dev asks for:

dmesg
lspci -vv
lspci -vvn

Now I'm guessing he/she wants the output after we try to suspend the laptop? In that case, how I do retrieve that information considering I have to restart the laptop (since wake from sleep does not work). So won't dmesg and lspci get overwritten? Do I have to look in a certain log file?

Thanks

---

### Post by fredronn on 2007-04-01
> **mustang said:**
> Quick question regarding posting a bug:

in another suspend bug thread on launchpad, a dev asks for:

dmesg
lspci -vv
lspci -vvn

Now I'm guessing he/she wants the output after we try to suspend the laptop? In that case, how I do retrieve that information considering I have to restart the laptop (since wake from sleep does not work). So won't dmesg and lspci get overwritten? Do I have to look in a certain log file?

Thanks

I had an idea, perhaps you could try it (I'm not running feisty on the macbook now). Does the computer perhaps respond to SSH-logins when 'dead'? If that is the case you should be able to get something out of it.

And dmesg is logged in /var/log/dmesg or messages I think.

---

### Post by mustang on 2007-04-01
Yeah---looks like lspci is static so that's not problem. I'm just going to upload the dmesg log after a suspend and subsequent boot.

---

### Post by mustang on 2007-04-01
Alright bug posted: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635)

Cross your fingers everyone ;)

---

### Post by Gen2ly on 2007-04-01
> **fredronn said:**
> I had an idea, perhaps you could try it (I'm not running feisty on the macbook now). Does the computer perhaps respond to SSH-logins when 'dead'? If that is the case you should be able to get something out of it.

And dmesg is logged in /var/log/dmesg or messages I think.

Why bother with Fiesty.  It'll be released in a matter of days.

---

### Post by ronocdh on 2007-04-02
> Why bother with Fiesty. It'll be released in a matter of days.Matter of weeks, actually. ;) And really, why bother with any of this stuff? :-k 

Also, to throw in my seventeen cents, I just installed KDE and suspend works like a dream. I clicked suspend, shut the lid, waited about 10 or 15 seconds (the power light by the lid-unlock button was already "breathing"), then lifted in the lid. The screen was definitely off, not just displaying black, which was good. Computer didn't respond to spacebar or clicks or enter or anything--then I tapped the power button. Poof, login screen, back up in a jiff. :guitar:

---

### Post by mustang on 2007-04-02
> **Dirk.R.Gently said:**
> Why bother with Fiesty.  It'll be released in a matter of days.

April 19th. Kernel freeze date is April 6th. Why bother? So that I and other macbook owners can get suspend working with ubuntu and not have to wait until the next release.

---

### Post by mustang on 2007-04-02
> **ronocdh said:**
> Matter of weeks, actually. ;) And really, why bother with any of this stuff? :-k 

Also, to throw in my seventeen cents, I just installed KDE and suspend works like a dream. I clicked suspend, shut the lid, waited about 10 or 15 seconds (the power light by the lid-unlock button was already "breathing"), then lifted in the lid. The screen was definitely off, not just displaying black, which was good. Computer didn't respond to spacebar or clicks or enter or anything--then I tapped the power button. Poof, login screen, back up in a jiff. :guitar:

I doubt using KDE makes any difference. Are you using a first or second generation macbook?

---

### Post by ronocdh on 2007-04-02
Second. 2.16GHz C2D MBP Pro 15" 1GB RAM. I just flipped over to Linux and fired up GNOME to test the suspend there... not only did it work, but when I opened the lid, it prompted me with a login window. In KDE I had to strike the power button. :-k Not very scientific, I know. I'm going to wipe KDE and install it again, and I'll try to be a bit more regimented about recording my observations. I'll post if I find anything insightful.

Oh, and in case it's not clear, I'm using the i386 build of 6.10; I am not running Feisty on this hog, due to my inexplicable inability to run xserver off the live cd, even in safe graphics mode.

---

### Post by ronocdh on 2007-04-02
Additionally, I recall that tonight I did a ```
sudo apt-get install linux-restricted-modules
```and then in Synaptic I made sure I had the 686 packs... this bumped my kernel from generic to 386, which might be worth a shot if you guys haven't done that. Again, sorry not scientific! =D

---

### Post by mustang on 2007-04-02
> **ronocdh said:**
> Additionally, I recall that tonight I did a ```
sudo apt-get install linux-restricted-modules
```and then in Synaptic I made sure I had the 686 packs... this bumped my kernel from generic to 386, which might be worth a shot if you guys haven't done that. Again, sorry not scientific! =D

Appreciate the observations ronocdh but the problems have been with first generation macbooks. Every other generation and version macbook has had more luck.

---

### Post by fredronn on 2007-04-05
Just thought I'd bump this thread up a bit and mention that the following does not work:

I compiled the default ubuntu kernel 2.6.20 available in the repos with CONFIG_BLK_DEV_PIIX disabled. This was mentioned in the Gentoo forums, but did nothing to change the outcome.

Has anyone tried anything else? Have the devs commented on this issue at all?

Oh by the way, could anyone verify that this will work:
[http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00212.html](http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00212.html)

---

### Post by mustang on 2007-04-05
> **fredronn said:**
> Just thought I'd bump this thread up a bit and mention that the following does not work:

I compiled the default ubuntu kernel 2.6.20 available in the repos with CONFIG_BLK_DEV_PIIX disabled. This was mentioned in the Gentoo forums, but did nothing to change the outcome.

Has anyone tried anything else? Have the devs commented on this issue at all?

Oh by the way, could anyone verify that this will work:
[http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00212.html](http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00212.html)

Hi fredconn---it doesn't appear the devs have picked up the issue. I think we'll be out of luck for this release :(

I tried compiling the kernel without the PIIX driver as well but it didn't help. Furthermore, it disables your dvd/cdrom drive so I don't think that's a pragmatic solution. 

For what it's worth, our best option is probably following the gentoo wiki from start to finish using the old 2.6.17.* kernels. I personally think I'll keep fiesty just to do some work when I sit down for an extended period of time. Otherwise, I'll keep OSX up for everything else. 

Even if suspend gets fixed, I don't think power management is there yet. My macbook still gets hot and I still get 2.5 hours of battery lifetime as opposed to 4 with OSX.

---

### Post by benanzo on 2007-04-05
I'm running Feisty fully updated

2.6.20-13-generic

On a black MacBook Core Duo.  When I was running edgy I just linked to laptop-detect and everything was fine.  Now with Feisty, suspend works with the stock kernel, but it's a little flaky.  I have the best success with it if I don't change any of the peripherals from the time that I put it to sleep to when I wake it up.  For instance, if I have a USB mouse plugged in when I put it to sleep, I have a better chance of it waking up cleanly if it is plugged in when I wake it up.  I'm not sure if this is a problem, but I ALWAYS disable networking (right-click nm-applet uncheck Enable Networking) before I suspend it.  Also, I make sure that I maintain the same power state between suspend/wake-up times.  I make sure that if I put it to sleep with it plugged in then I wake it up plugged in.  If I'm leaving, I'll unplug it then put it to sleep and make sure that it's still unplugged when I wake it up.  Otherwise when I wake it up, it just sits at the blinking cursor for ~10 secs and then reboots.


Doing all this has made suspend to ram work ~90% of the time.  Also, if I boot-up then close the lid during to boot process, the backlight doesn't come on and I have to reboot.  Hibernate doesn't work at all.  I hit Hibernate (following all the same rules) and it just flickers then goes to the Locked Screen password dialog.  I have less use for Hibernate than Suspend to ram anyway, but I would still like it to work.

---

### Post by mustang on 2007-04-06
> **benanzo said:**
> I'm running Feisty fully updated

2.6.20-13-generic

On a black MacBook Core Duo.  When I was running edgy I just linked to laptop-detect and everything was fine.  Now with Feisty, suspend works with the stock kernel, but it's a little flaky.  I have the best success with it if I don't change any of the peripherals from the time that I put it to sleep to when I wake it up.  For instance, if I have a USB mouse plugged in when I put it to sleep, I have a better chance of it waking up cleanly if it is plugged in when I wake it up.  I'm not sure if this is a problem, but I ALWAYS disable networking (right-click nm-applet uncheck Enable Networking) before I suspend it.  Also, I make sure that I maintain the same power state between suspend/wake-up times.  I make sure that if I put it to sleep with it plugged in then I wake it up plugged in.  If I'm leaving, I'll unplug it then put it to sleep and make sure that it's still unplugged when I wake it up.  Otherwise when I wake it up, it just sits at the blinking cursor for ~10 secs and then reboots.


Doing all this has made suspend to ram work ~90% of the time.  Also, if I boot-up then close the lid during to boot process, the backlight doesn't come on and I have to reboot.  Hibernate doesn't work at all.  I hit Hibernate (following all the same rules) and it just flickers then goes to the Locked Screen password dialog.  I have less use for Hibernate than Suspend to ram anyway, but I would still like it to work.

Hi benanzo,

first off, thank you for posting. 

I tried what you said but with no luck. I tried with no peripherals, non-plugged in, and was sure to turn off networking. The laptop still doesn't fully turn off (I can still hear the fan). 

Regarding hibernate, it worked fine under edgy with the 2.6.17.* kernels but I have not had any luck with other kernel versions.

---

### Post by vh1 on 2007-04-12
I've got a 1.83 Macbook C2D running Kubuntu Fiesty with everything updated, and suspend doesn't work properly. `sudo pmi action suspend` suspends the machine fine, as far as I can tell. it brings down the network, the screen shuts off and all you can hear is a  very quiet fan

the sleep light turns on when you close the lid and turns off when its opened, but there's no way to actually resume the session, and you've got to give the computer a hard-reset

hibernate almost works too. `sudo pmi action hibernate` brings down the network, then goes to a VT, then back to my desktop with some output in konsole. luckily I can copy and paste it:

```
mike@lua:~$ sudo pmi action hibernate
Password:
There is already a pid file /var/run/dhclient.ath0.pid with pid 6481
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:17:f2:ed:e9:bb
Sending on   LPF/ath0/00:17:f2:ed:e9:bb
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.0.1 port 67
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 6382
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:17:f2:32:88:5a
Sending on   LPF/eth0/00:17:f2:32:88:5a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
ifdown: interface eth0:avah not configured
SIOCSIFFLAGS: Cannot assign requested address
ifdown: interface vmnet1 not configured
ifdown: interface wifi0 not configured
 * Shutting down ALSA...                                                 [ OK ]
/etc/acpi/hibernate.sh: line 39: echo: write error: No such device
Laptop mode disabled, not active.
Starting 915resolution: 915resolution.
Function not supported
Function not supported
Starting 915resolution: 915resolution.
ifup: interface ath0 already configured
ifup: interface eth0 already configured
Ignoring unknown interface eth0:avah=eth0:avah.
Ignoring unknown interface wifi0=wifi0.
Ignoring unknown interface vmnet1=vmnet1.
 * Setting up ALSA...                                                    [ OK ]
grep: /proc/acpi/fan/*/state: No such file or directory
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.
mike@lua:~$
```

also, I have no swapfile. my macbook has 1gb of RAM, and I haven't experienced any problems. and to enable one, I'd have to trash my current kubuntu install to get bootcamp to launch and give me the option of resizing the HFS+ partition. or pay for one of the HFS+ partitioning tools. could this be the problem?

it seems /etc/acpi/hibernate.sh checks for s2disk, which is in uswsusp, but that complains about my lack of swap space

---

### Post by mustang on 2007-04-12
> **vh1 said:**
> I've got a 1.83 Macbook C2D running Kubuntu Fiesty with everything updated, and suspend doesn't work properly. `sudo pmi action suspend` suspends the machine fine, as far as I can tell. it brings down the network, the screen shuts off and all you can hear is a  very quiet fan

Well then it's not suspending fine because the CPU should be turned off and the light should pulse when the lid is down (just  like in OSX).

> 
the sleep light turns on when you close the lid and turns off when its opened, but there's no way to actually resume the session, and you've got to give the computer a hard-reset

Well this is the identical problem first generation macbook owners are experiencing. I'm curious as to why suspend isn't working on your second generation macbook. It might be a gnome thing? Have you tried suspending with gnome?

> 
hibernate almost works too. `sudo pmi action hibernate` brings down the network, then goes to a VT, then back to my desktop with some output in konsole. luckily I can copy and paste it:

```
mike@lua:~$ sudo pmi action hibernate
Password:
There is already a pid file /var/run/dhclient.ath0.pid with pid 6481
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:17:f2:ed:e9:bb
Sending on   LPF/ath0/00:17:f2:ed:e9:bb
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.0.1 port 67
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 6382
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:17:f2:32:88:5a
Sending on   LPF/eth0/00:17:f2:32:88:5a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
ifdown: interface eth0:avah not configured
SIOCSIFFLAGS: Cannot assign requested address
ifdown: interface vmnet1 not configured
ifdown: interface wifi0 not configured
 * Shutting down ALSA...                                                 [ OK ]
/etc/acpi/hibernate.sh: line 39: echo: write error: No such device
Laptop mode disabled, not active.
Starting 915resolution: 915resolution.
Function not supported
Function not supported
Starting 915resolution: 915resolution.
ifup: interface ath0 already configured
ifup: interface eth0 already configured
Ignoring unknown interface eth0:avah=eth0:avah.
Ignoring unknown interface wifi0=wifi0.
Ignoring unknown interface vmnet1=vmnet1.
 * Setting up ALSA...                                                    [ OK ]
grep: /proc/acpi/fan/*/state: No such file or directory
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.
mike@lua:~$
```

also, I have no swapfile. my macbook has 1gb of RAM, and I haven't experienced any problems. and to enable one, I'd have to trash my current kubuntu install to get bootcamp to launch and give me the option of resizing the HFS+ partition. or pay for one of the HFS+ partitioning tools. could this be the problem?

it seems /etc/acpi/hibernate.sh checks for s2disk, which is in uswsusp, but that complains about my lack of swap space

I would think a swap file would be needed for hibernate (aka supend to disk) because there might be the case where the non-swap partition is full and the user requests a hibernate. But I'm not sure.

---

### Post by andersmusikka on 2007-04-15
I have a second generation macbook, running feisty. Neither suspend to ram nor hibernate (suspend to disk)  works for me.

When I try to use suspend (to ram), the screen goes blank, and the harddrive shuts down, but the CPU-fan keeps spinning, and the laptop continues to generate heat (presumably the CPU is still running). Closing the lid makes the led in the lower right corner come on, and opening it again makes it go out. The computer will not wake up (tapping keys, the touchpad, opening/closing lid or tapping the power button produces no effect at all).


Does anyone have any idea how to troubleshoot this kind of trouble? There is nothing in /var/log/messages from the suspend-attempts.

I'm running feisty, and dmesg thinks my kernel-version is:

Linux version 2.6.20-14-generic (root@rothera) (gcc version 4.1.2
 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Mon Apr 2 20:37:49 UTC 2007 (Ubuntu 2.6.20-14.2
2-generic)

I'm willing to spend some time troubleshooting this, but I don't know where to begin.

Anyone have any ideas?

---

### Post by Asgaard on 2007-04-17
^^ I see the exact same behavior on my 1st gen 1.83 white Macbook. I'm Leonardo Mosquera on Launchpad (and in real life too as a matter of fact). I think we'll get broader coverage if we concentrate any progress here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635)

---

### Post by mustang on 2007-04-25
Hi guys,

I just checked into the bug thread here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635)

and apparently two people were able to get suspend working by applying the patch found here:

[http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00198.html](http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00198.html)

> 
That was applied on the latest linux-source from Feisty, so the Ubuntu patchset. I've also applied it against the Gentoo patchset and vanilla sources and it fixes sleep on all three. Notably, some modifications may still be needed to get it to return from sleep, as the backlight generally doesn't want to turn on.


So to do this process, one would need to:

sudo apt-get source linux-image-2.6.20-15-generic, apply the patch found in the link above, and then compile? Would anyone mind giving that a go and reporting back?

---

### Post by ronocdh on 2007-04-25
> **mustang said:**
> Hi guys,

I just checked into the bug thread here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635)

and apparently two people were able to get suspend working by applying the patch found here:

[http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00198.html](http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00198.html)



So to do this process, one would need to:

sudo apt-get source linux-image-2.6.20-15-generic, apply the patch found in the link above, and then compile? Would anyone mind giving that a go and reporting back?
For anyone new to the thread, this pertains only to MacBooks with a Core Duo. (Made that mistake earlier!) As mustang has made clear, the other machines seem to be having much better luck.

---

### Post by Asgaard on 2007-04-26
> **mustang said:**
> Would anyone mind giving that a go and reporting back?

Will do later on when I get home.

---

### Post by mustang on 2007-04-28
Well I tried both the latest 2.6.21 vanilla kernel as well as the 2.6.15 feisty kernel. 

With the vanilla kernel, the patch didn't apply successfully since libata-core.c (the file the patch modifies) has been updated since 2.6.19.1 (the kernel the patch is intended for). So I manually edited it and then compiled. Gave the kernel a go but no luck :(. Tried suspending both via the standard suspend option presented in the "quit" screen and with s2ram. With the standard option, I get the same response I've been previously getting--screen turns off, hard drive turns off, cpu stays on, LED doesn't pulsate. With s2ram, I get the same results except the screen stays on. 

With the feisty kernel, I was getting an error during the .deb creation. There were no errors in the compilation process though. I should have saved the error message.

---

### Post by Asgaard on 2007-05-04
I just implemented the fix from the patch manually and I can confirm it WORKS. Done on 2.7.20.3-ubuntu1, current in feisty repositories as of today.

I'm fairly happy :) This is the first time I've ever got suspend to work on Linux.

---

### Post by mustang on 2007-05-04
> **Asgaard said:**
> I just implemented the fix from the patch manually and I can confirm it WORKS. Done on 2.7.20.3-ubuntu1, current in feisty repositories as of today.

I'm fairly happy :) This is the first time I've ever got suspend to work on Linux.

Hi Asgaard,

how did you apply the patch? Did you manually edit libata-core.c or did you the "patch" command? The patch posted on that website is for an older kernel so I don't think you could just directly patch a newer kernel.

Thanks

edit: **COOL!**

Finally got suspend reliably working. I just apt-get'd linux-source and edited the lines the patch would have. Wifi won't work---I downloded and compiled the wifi modules from madwifi. Alternatively, it might be better to load the modules from the working kernel.

Finally finally finally finally finally. All that's left is power management

edit2: can be quirky at time (ie suspending with power cord plugged in, waking on battery results in the led screen not turning on. This confirms benanzo's observations made earlier in the thread)

---

### Post by Asgaard on 2007-05-05
Yes I had hand edited libata-core.c.
Dang I hadn't noticed about the missing madwifi. I don't think loading the modules from the original kernel works because modprobe complains about a missing symbol, but then again I'm a dork when it comes to setting up a new kernel, so I could be doing something wrong.

But I can definitively trade surfing on the couch for not having to turn the damn thing on and off 2 times a day when I get to and from work.
Until I get around to compile madwifi anyway.

Anyone, what's the correct way to compile madwifi and set it up as a debian package, if we're  building via make-kpkg? --add-modules maybe?

---

### Post by mustang on 2007-05-05
Not sure here. I just did a make and a sudo make install.

---

### Post by mustang on 2007-05-05
For those of you who use a higher minimum speed for the fans to keep your macbook cooler, you'll notice that the fan speed's minimum gets reset to 1500RPM after waking up from a suspend.

To fix that, do:

```

sudo nano /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux 

```

And paste this line BEFORE the final "exit $RET" statement. 
```

echo 3000 > /sys/devices/platform/applesmc/fan0_minimum_speed

```

Replace "3000" with whatever minimum fan speed you want.

---

### Post by Leftmost Cat on 2007-05-05
I haven't tried hand-compiling madwifi, personally. My real hope in posting that information was that one of the Ubuntu devs would take a look at the problem and perhaps submit a fix. To date, though, it doesn't look like that's happening. I don't suppose anyone has any ideas for getting their attention on the matter. For a distro that's supposed to Just Work, I spent far too much time trying to get things working. Even if a patch couldn't be worked out for the Ubuntu sources anytime soon, it would be nice to have a way to install restricted modules for a hand-rolled kernel without having to download them and install them by hand.

---

### Post by ronocdh on 2007-05-05
> **Leftmost Cat said:**
> I haven't tried hand-compiling madwifi, personally. My real hope in posting that information was that one of the Ubuntu devs would take a look at the problem and perhaps submit a fix. To date, though, it doesn't look like that's happening. I don't suppose anyone has any ideas for getting their attention on the matter. For a distro that's supposed to Just Work, I spent far too much time trying to get things working. Even if a patch couldn't be worked out for the Ubuntu sources anytime soon, it would be nice to have a way to install restricted modules for a hand-rolled kernel without having to download them and install them by hand.
A Gentoo user complaining about too much customization! :popcorn: 

Seriously though, I think progress is being made. The madwifi chaps are working their asses off and putting out great releases; I've seen people get connectivity by trying the newer versions. It just takes time. Now, maybe not as much as configuring Gentoo, but that's another matter. ;)

---

### Post by Leftmost Cat on 2007-05-06
I'm not complaining about too much customization. I'm complaining about the amount of effort that has to go into making a "Just Works" distribution work and, indeed, the lack of customization. I'm typically not thrilled about installing a bunch of things outside of the package manager.

Additionally, the issue here isn't that I have madwifi drivers installed but they don't work. The issue is that the restricted modules don't work with a hand-rolled kernel and so installing madwifi drivers becomes more of an issue than it really should be. The best solution would be for the patch to be integrated into the kernel, but it seems like it may also be necessary to provide a way for users of the restricted modules to easily install them when they have a hand-rolled kernel.

---

### Post by eldepeche on 2007-05-06
> **Leftmost Cat said:**
> The best solution would be for the patch to be integrated into the kernel, but it seems like it may also be necessary to provide a way for users of the restricted modules to easily install them when they have a hand-rolled kernel.
Can't you use module-assistant to compile madwifi? That's how I did it on Debian Etch last year. If you compiled your own kernel, then you have the header files already, and  you just need to run 
```
# apt-get install madwifi-source 
# apt-get install madwifi-tools
# m-a prepare
# m-a a-i madwifi
```
Does this not work on Ubuntu?

---

### Post by thully on 2007-05-07
I have a first generation MacBook, and this suspend issue is driving me NUTS!
I'm trying to patch my kernel to make it work, and I'm not getting anywhere...
I got the changes made in the source code (basically stubbing out the ATA suspend), but
I can't for my life get the kernel to compile properly!  The instructions on the wiki for building
a kernel the "Ubuntu way" didn't work at all...  

Anyone have a clue on how to do this? I NEED madwifi with my kernel - it's my only way of getting online aside from sitting right next to my wi-fi router and satellite modem at all times - NOT something I really want to do...  Suspend to RAM is fairly essential to me - it's actually the main reason I dropped Linux on my ThinkPad 2-3 years ago.  I was hoping things would improve, but evidently it's still an issue.  If all else fails, I may just end up running in Parallels...

---

### Post by mustang on 2007-05-07
> **thully said:**
> I have a first generation MacBook, and this suspend issue is driving me NUTS!
I'm trying to patch my kernel to make it work, and I'm not getting anywhere...
I got the changes made in the source code (basically stubbing out the ATA suspend), but
I can't for my life get the kernel to compile properly!  The instructions on the wiki for building
a kernel the "Ubuntu way" didn't work at all...  

Anyone have a clue on how to do this? I NEED madwifi with my kernel - it's my only way of getting online aside from sitting right next to my wi-fi router and satellite modem at all times - NOT something I really want to do...  Suspend to RAM is fairly essential to me - it's actually the main reason I dropped Linux on my ThinkPad 2-3 years ago.  I was hoping things would improve, but evidently it's still an issue.  If all else fails, I may just end up running in Parallels...

Hi thully,

can you paste the output of where it goes wrong during kernel compilation? Does it stop when compiling libata-core.c or elsewhere? I followed the "ubuntu way" guide as well and on my second try, it worked. And when you say "stubbing out the ata suspend", you mean erasing every line from (and including)

```
rc = ata_host_request_pm(host, mesg, 0, ATA_EHI_QUIET, 1)
```

up to (and including)

```
 } 
```

the terminating curly brace for the "for" loop? And just to be sure, you are using the feisty sources right? I tried the same patch with the latest 2.6.21 kernel and it didn't work (probably because I didn't apply the mactel patches). But just to be on the safe side, I'd use the feisty sources.

Regarding wifi, it's fairly easy to get it working. Download the latest release of madwifi (borrow someone's ethernet or download it in osx and put it on some storage device), ./configure, make, sudo make install, modprobe ath_pci.

---

### Post by thully on 2007-05-08
I figured out what I did wrong - I did apt-get install linux-source instead of apt-get source linux-image-2.6.20-15-generic.  The latter command gave me the source needed for an Ubuntu-style build.  As far as the patch goes, I did basically what you said (except that instead of deleting the code or commenting it out I put it in an if(0){} as the original diff did - basically the same thing).  It's building now - I guess I'm actually taking advantage of dual cores as I type :)

As far as madwifi, I think I have an idea on how to build a brand-new restricted-modules package.  The wiki for kernel compilation talks about how to do it, and it seems fairly easy..  In the end, it looks like I'll have a kernel just a few bytes different from stock - which is a good thing...

I hope they get this fixed in the actual kernel soon - I remember applying a similar patch with my Thinkpad for suspend and it was annoying as heck...

BTW - I also installed Ubuntu in Parallels.  It works quite well - in fact, maybe better than native save for video performance.  I may just stick with a dual-boot, though - I only have a trial of Parallels and using Parallels almost feels like "cheating"

---

### Post by thully on 2007-05-08
I successfully built a kernel .deb + linux-restricted-modules (the latter took a bit of trial and error - some of the build scripts needed to be edited to only build for a "generic" kernel).  Now my system suspends perfectly!  No major problems - not even with the backlight - after resume...  Occasionally, I get a "fails to suspend" error, but this doesn't affect anything...  The only thing other than building the kernel debs that I did is the suggested suspend fix from the MacBook Ubuntu wiki page.

---

### Post by donpaco69 on 2007-05-09
could you maybe post your .deb with your kernel? would be very nice from you :D

---

### Post by JasonDill on 2007-05-09
Yes please, If you don't mind would you post your .deb's :)

---

### Post by thully on 2007-05-09
I'll try to get them up tomorrow - I have pathetic uplink (~128kbps) where I am now, so it would take several hours to get them all up.

---

### Post by thully on 2007-05-10
The .debs are posted for everything now (even source, to comply with the GPL). The only change made to the generic kernel is the change to libata-core.c which fixes suspend on first-gen Macbooks.

Get them at:

[http://www-personal.umich.edu/~thully/ubuntu-macbook/](http://www-personal.umich.edu/~thully/ubuntu-macbook/)

They work great for me, but YMMV.

---

### Post by vh1 on 2007-05-14
oh hey would you look at that!

installed the deb on a C2D and it took a little longer than expected (and the screen gets activated for a second), but it sure as heck went to sleep and woke up

---

### Post by donpaco69 on 2007-05-15
ok, i've also made my deb's from source, as you said, it works, but it takes about 10 seconds to sleep and the last one second the screen light come back, then fully sleep and the wake up is really nice, 1 little second, nearly as speedly as Mac OS!

for the moment i've one little problem with suspend to ram, maybe can someone explain me how to fix this:

on wake up, bluetooth just doesn't work anymore, it said: bluetooth adapter unplugged or something like this, so i've no BT mouse until i reboot :s

any idea?

---

### Post by vh1 on 2007-05-17
also, I can't seem to make my macbook go to sleep anymore

this started happening a couple of days ago. I close the lid and wait and wait, but it never goes to sleep.

no boot options have been changed or anything either. I'll look into this more in a bit, now is time for lunch

---

### Post by clcaus on 2007-05-22
EDIT:

I downloaded you DEB files and used sudo dpkg -i to install them. I rebooted. However, when I did uname -r after rebooting it still displays my old kernel version. How can I install this kernel version? My suspend works but I can't compile madwifi.

---

### Post by jameswfrost on 2007-05-26
Hi!

Could you confirm, with your .debs - do I need to install *all* of them?

I tried rolling my own kernel last night, but it didn't seem to fix the problem (and took *hours*).  :(

Thanks!

---

### Post by clcaus on 2007-05-26
I didn't install the docs or the source .debs. I installed the rest of them. Whether or not that was necessary, I don't know. Then I had to edit my grub.conf to make the new kernel available at startup.

---

### Post by thully on 2007-05-27
In order to use the new kernel, you have to make the new kernel the default in GRUB (by editing grub.conf) or select the new kernel on boot.

---

### Post by peterl on 2007-06-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/72287](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/72287) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **jameswfrost said:**
> Hi!

Could you confirm, with your .debs - do I need to install *all* of them?

I tried rolling my own kernel last night, but it didn't seem to fix the problem (and took *hours*).  :(

Thanks!

i used the image and the two headers (one of them's ~40k, so i guess you need at least the other one!). works for me, and i just compiled madwifi 0.9.30.13 which (i think) was released on 20070519.

has anyone had any luck with the backlight---either coming back on after suspend, or controlling using f1/f2? i've searched around all over the place! found this: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/72287](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/72287) but the .c file on there won't compile for me...

thanks for your help :)
peter.

---

### Post by gamblorius on 2007-06-25
Hi guys,

I was having suspend issues with an R1 MBP (with Feisty). I fixed it by following advice of a previous post on the issue and going to [this guide]("http://www.andybotting.com/wordpress/?p=176#comments"). Now, suspend to RAM works, although suspend to disk does not.

Cheers,
John

---

