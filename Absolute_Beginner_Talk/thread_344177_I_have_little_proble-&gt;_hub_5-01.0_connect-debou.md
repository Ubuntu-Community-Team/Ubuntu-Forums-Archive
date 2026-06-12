---
title: "I have little proble-&gt; hub 5-0:1.0: connect-debounce failed, port 6 disabled"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by myoldryn on 2007-01-22
Hi!

I have a little problem. Whenever i boot up my pc, i get an error "hub 5-0:1.0: connect-debounce failed, port 6 disabled". 

i use kernel 2.6.20-5

[My pc](http://server-uk.imrworldwide.com/cgi-bin/b?cg=COM-complete&ci=siemensfujitsu&tu=http://www.fujitsu-siemens.com/Resources/173/1127099518.pdf)

---

### Post by carlosfocker on 2007-02-08
Do you have a external usb hub or any external usb devices.  If so, unplug on boot to see if the problem goes away.  Post back with results

---

### Post by aaxc on 2007-02-14
I have the same problem:

**Feb 14 17:43:18 aaxc kernel: hub 2-0:1.0: connect-debounce failed, port 6 disabled**

It happened on SuSE Enterpirse Server 10.0 when I added an external usb disk. After that I can't get USB ports to work .. I unplugged anything, but still no change .. any suggestions?

---

### Post by carlosfocker on 2007-02-27
So is this on a SUSE server or an ubuntu machine. What usb devices did you plugin

---

### Post by Loonis on 2007-05-06
Same problem here... But on a laptop and without having any usb-hub connected. Problem is this drain my battery. :(
Any idea how I can solve this?
/Linus

---

### Post by kaffemonster on 2007-05-20
Ditto - Connect-debounce failed etc. on my laptop with nothing plugged in to the usb ports. Wil try disabling USB in bios, to see if it helps.

Edit: It helps - sorta. I no longer get the "connect-debounce" error, but now my USB is dead (well, duh).

Gonna post a bug about this.

---

### Post by kaffemonster on 2007-05-20
Hmm... there is already a bug posted about this: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88530](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88530)

Good thing is, it's about the excact same laptop as mine: Fujitsu-Siemens Amilo Pro V3205 (nifty little thing btw).

A couple of solutions are suggested, but none worked for me. I already have the latest BIOS (1.20), and the "disable usb legacy support"-trick doesn't work. 

Seems to be a kernel problem - Linus, are you listening?!? :D

---

### Post by Cannaregio on 2007-09-24
Problem is still there, and will still be there with gutsy.
It's a bluetooth related kernel problem that annoys us Amilo users.

See
[https://bugs.launchpad.net/linux/+bug/88530]("https://bugs.launchpad.net/linux/+bug/88530")
and scroll down.

Let's hope the developers will fix it soon or later.

---

### Post by tomdawg07 on 2007-10-28
I have the same problem with my 7.04 Ubuntu dual-boot, I just get flooded with the connect-debounce errors and can't load the GUI. But I run a desktop machine, so it can't be Bluetooth!

---

### Post by hallgeir on 2007-11-18
Does anyone have an update on this?  I have the same problem with the same hardware and after hours of banging my head against the wall a reinstall is my only solution.

---

### Post by kimbledon on 2008-01-07
I have Amilo Pro V3205 and i'm having the same problem. It doesn't affect any other way but when I change my to one of my virtual ttys, I can't use the terminal so good. It floods the message all the time . Could this message be silenced or something because I don't have any other problems but the flooding.

---

### Post by jkarlsen on 2008-05-26
have the same problem, is there a fix for this yet?

(amilo pro v3205, ubuntu 8.04)

---

### Post by kaffemonster on 2008-05-26
> **jkarlsen said:**
> have the same problem, is there a fix for this yet?

(amilo pro v3205, ubuntu 8.04)


I dropped my Amilo Pro, broke the motherboard.

I am no longer seeing that error message...

---

### Post by Chad.S on 2008-07-05
I have the same problem. However, the issue has only affected one device so far : my zen mp3 player. My mouse, usb HD, etc. all work fine without this message.

I have the latest BIOS and have tried several solutions posted from the bug report post to try to get around this, but with no luck.

It works fine with my AsusEEE and Thinkpad T60 so I just sync with those :) Of course, the one I have this problem on is a Dell Inspiron 1420...you know, the ones that came with Ubuntu installed...lol. Pretty ironic IMO.

---

