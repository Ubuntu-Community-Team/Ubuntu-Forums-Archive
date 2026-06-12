---
title: "complete noob. error code 21 grub"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by chikoo on 2006-04-21
Hey there. I am completely new to the Linux scene.

Here's the situation.

I installed Ubuntu, the latest version, onto a usb external hard drive. It installed just fine.

I then went to install the GRUB boot loader, and it asked me where I wanted to put it, and since my Windows XP is on my primary drive, I figured I might as well put GRUB on my primary drive so I can choose to boot between XP and Ubuntu. 

After the installation was complete, I took out the cd and booted up my computer again.

Instead of booting to a screen that I'm presuming says something like "Which OS would you like to use" or something like that, it gave me an Error Code 21.

I have no idea what's going on... it won't let me boot XP or Ubuntu... I can't find my XP cd to reset the MBR... I've tried re-installing the GRUB from the install CD and it's still not working... 


Can anyone help a noob out?

I have a knoppix live cd and a version of the ubuntu live cd as well. 

In the end, I just want to be able to boot to XP again.

---

### Post by Sianis on 2006-04-21
Hi!

I don't think it will be workink. The grub try read the menu.lst from your external drive, but if you didn't create a boot partition (/boot) to your first drive it won't works, cause the grub need files from the external drive and it cannot mount up it in boot time.

Was it clear? I don't know...

---

### Post by croak77 on 2006-04-21
I would look for your windows cd to fix the mbr. If you want to try to install ubuntu again, take a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

---

### Post by chikoo on 2006-04-21
I found my xp cd and when I get back home, i'm going to run the "fixmbr" option and then I will use that thread's instructions on how to install. thanks for the help croak!

---

