---
title: "No Sound"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by andy_6590 on 2007-08-10
Hi I have posted quite a few threads on this subject but I am still not getting anywhere. Basically I have duel booted with Windows and in Windows I have sound but in Ubuntu 7.04 I do not. I have posted quite a bit of information on the following pages but if additional information is needed just post what you need and I will happily post the answers immediately. Could you please look at my others to see if you could help me please. 

[http://ubuntuforums.org/showthread.php?t=521801](http://ubuntuforums.org/showthread.php?t=521801)

[http://ubuntuforums.org/showthread.php?t=521689](http://ubuntuforums.org/showthread.php?t=521689)

[http://ubuntuforums.org/showthread.php?t=521226](http://ubuntuforums.org/showthread.php?t=521226)

Thank you for your time and help.

---

### Post by anewguy on 2007-08-10
Okay, first things first:)  Don't create anymore posts for this problem - just add a reply and bump it back to the top of the message list.  I check your 3 posts and each has something a little more/different in them, so we need to start at a basic question:

- have you ever had any sound in Ubuntu (what Windows does doesn't really matter right now)?  You know - did you ever hear the bongos when the log on screen came up, etc?

- if so, what did you change such that it stopped?

- also, in a terminal window, type lspci and post the output here.  I know this is in one of the other posts you made, but we need to keep everything in a single post if we're going to be able to help you:)

So, it's repeating some things you already did, but we need those things first before we start looking for answers:)

---

### Post by andy_6590 on 2007-08-10
Sorry about that just wanted to get it sorted. I have never had sound in Ubuntu, so its been a problem since install. The output of lspci is:

andrew@andrew-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
andrew@andrew-desktop:~$ 

Many thanks.

---

### Post by anewguy on 2007-08-11
Please paste the output of the following back here:

ls -al /dev/snd

I know you can specify a device for alsmixer in the command line, but what I don't yet is the device.  If I can get that figured out, perhaps we'll be able to start the mixer.:)

---

### Post by anewguy on 2007-08-11
I've done quite a bit of searching the net for your chipset and the various Linux distros.  Something I have come across more than once for you to try:

First off, change the blacklist so you're not blacklist the ...xp.. what file that you did in one of your other posts.

Second, do this in a terminal window:

sudo gedit /boot/grub/menu.lst

You should find an entry something like this in that file:

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a42ae918-d19e-4605-aea6-7114c5ee4164 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

on the end of the kernel line where it says "splash" add " noapic" so the tail end looks like this:  "splash noapic"

save the file, exit, and reboot your PC.

Now did it make any difference for your sound?

---

### Post by andy_6590 on 2007-08-11
In response to anewguy the output of ls -al /dev/snd was:

"andrew@andrew-desktop:~$ ls -al /dev/snd
total 0
drwxr-xr-x  2 root root      80 2007-08-12 01:57 .
drwxr-xr-x 12 root root   13960 2007-08-12 01:57 ..
crw-rw----  1 root audio 116, 3 2007-08-12 01:57 seq
crw-rw----  1 root audio 116, 2 2007-08-12 01:57 timer
andrew@andrew-desktop:~$"

Hope that helps.

In response to your other question I don't know how to change the blacklist if you would be kind enough to tell me I will do so. I entered sudo gedit /boot/grub/menu.lst in Terminal and change it to read "splash noapic" so now it reads this:

"title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d5c55d59-aa35-47e3-b86a-93b07084aa4e ro quiet splash noapic
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault"

I then saved the file and restarted but I still don't have any sound. Hope the information above helps. Thanks again.

---

