---
title: "[SOLVED] USB access for VirtualBox"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by iainv on 2008-03-21
My scanner won't work with SANE (Xerox 4800), so i'm trying to get it running in VirtualBox.

I've installed an XP virtualbox which is running well, and have installed the proprietry scanner software, registered it via the internet from within the virtual machine, but can't get it to detect the scanner.

I've found this thread: [USB/VirtualBox on Feisty]("http://howto.landure.fr/gnu-linux/ubuntu-feisty-fawn-1/software-for-ubuntu-feisty-fawn/virtualbox-on-ubuntu-feisty-fawn") but it says: **Warning: only use this part of this article if you know what you're doing and if you encounter USB problems with VirtualBox**

Frankly, I don't know what i'm doing.

Is usbfs not configured in Gutsy (as it says it isn't in Feisty)?
Is this a "safe" thing for me to do?
Is it likely to screw up my other USB devices in Gutsy (I use ndiswrapper to load a usb wifi adaptor)?

Advice please!

Iain

---

### Post by Victormd on 2008-03-21
Are you using Feisty?
I had virtualbox installed under Gutsy and the USB worked fine. I don't recall doing anything that was on the link you posted, it was much simpler... I'm going to try to find it and let you know. I think it's related to the version that you have. If I remember correctly, the version that you install from the repos does not support USB, but you can download the non-ose version (but still free) from [www.virtualbox.org](www.virtualbox.org) and install that one that already comes with USB support... there, that's what I did... :)

---

### Post by maddog39 on 2008-03-21
Well as far as I know the USB support in those VMs doesnt support just any device. Ive never gotten my camera, printer, scanner, skype phone converter, etc to be recognized in a VM. Only my external hard drives and thumb drives have ever heen recognized. And Ive tried this on both VMWare and VirtualBox.

---

### Post by rustutzman on 2008-03-21
I believe you need to install the the guest extras in VirtualBox to enable the USB. At least that worked for me.

Russ

---

### Post by Victormd on 2008-03-21
> **rustutzman said:**
> I believe you need to install the the guest extras in VirtualBox to enable the USB. At least that worked for me.

that's right...

---

### Post by iainv on 2008-03-21
Thanks - i'll give this a go.

Iain

---

### Post by iainv on 2008-03-21
OK, so i've successfully installed the guest additions, and the mouse integration is now working, but still no USB recognition for anything, let alone the scanner - for example plugging a memory stick in loads the file browser in Ubuntu, but the Virtualbox XP doesn't detect it.

I'm running Gutsy.

Iain

---

### Post by rustutzman on 2008-03-22
In VB rt click on the USB connection at the bottom of the screen to enable the devices.

Russ

---

### Post by iainv on 2008-03-22
Cheers - i've got it sorted now.

The problem was a complicated one - for starters I was running the OSE version of VB, so I had to download the binaries and install those.
Then I had to update all the various files to enable usbfs to work properly, and VB could then see the USB devices but they were not available.
Lastly, having sorted out the group permissions, I had to add sudo /etc/init.d/mountdevsubfs.sh start to my startup session or the group access didn't work.

I now have my scanner working in XPVB!!!

Thanks everyone for all your help - the scanner was one of the last things that required a "proper" windows install. If I can get Quickbooks running in VB i'll be able to dump Windows permanently!

(You will then likely have lots of inane questions from me as I try to wipe Vista off my laptop!)

Iain

---

### Post by timjohn7 on 2008-03-23
I have a similar problem with all my USB devices.
Could you please descibe your last post actions in a step by step post so that I, a fellow newb, can implement them?
I'm sort of with you, but just to be safe...

---

### Post by iainv on 2008-03-23
No problem - the link below goes to an outline of what steps I took.

It worked temporarily, and then gave up again - but I seem to be having wider problems with my USB and no-one seems to be able to suggest anything to improve things!

Good luck - if it works for you please let me know,

Iain
[Step by step guide to USB in VirtualBox]("http://ubuntuforums.org/showthread.php?t=732100")

---

