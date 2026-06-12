---
title: "Did Kismet wreck my Ubuntu?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by cmdowns on 2008-03-29
Greetings Ubuntites! I am a total linux / Ubuntu noob. I'm running Ubuntu on an HP Pavilion laptop in a dual boot set up along side XP. I've recently installed Kismet and edited the config file to work with my Broadcom 4306 wireless card with the line "source=bcm43xx,eth1,eth1".

Last night, I got Kismet up and running for the first time. I can't say for sure if it's running optimally or even correctly. But I was pretty proud of myself for getting that far.

Now, when ever I boot up Ubuntu and try to connect to my own wireless network, it seems that I connect (get the two little green dots in my network icon), but then my system freezes up. My mouse arrow still moves as normal, but I can't click on anything, can't ctrl+alt+del to the shutdown menu, and my laptop's power button doesn't function. The only way I can shutdown the machine is my unplugging it and removing the battery.

Does anyone have any idea what might be wrong and what I can do to fix it?

Thanks in advance!

---

### Post by tgalati4 on 2008-03-29
Kismet (through the config file) puts the wireless card in a passive, receive-only mode.  It's a complicated application to set up correctly.  Not something for new users to hack on.

The Broadcom card uses either the crappy, reverse-engineered linux modules, or the better-working, Windows driver with ndiswrapper.

To repair, I would recommend booting with the Live CD, and run fsck on the drive and/or each of it's partitions:

>sudo fsck /dev/sda1

Then shut down, remove the disk, and reboot.

Don't use kismet until you are prepared to spend some time hacking and deal with associated down time.

---

### Post by cmdowns on 2008-03-29
tgalati4,
Thanks so much for the info. I'll try it as soon as I get home. In my efforts to learn linux and kismet, I've probably gotten ahead of myself. I just assumed the best way to learn was to jump in and start trying to use the app. On second thought, maybe I outta read that documentation after all.

Thanks again.

---

