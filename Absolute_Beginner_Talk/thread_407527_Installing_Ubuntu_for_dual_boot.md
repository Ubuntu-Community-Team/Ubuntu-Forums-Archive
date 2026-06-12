---
title: "Installing Ubuntu for dual boot"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Bubby on 2007-04-12
Hello everyone,

This will be the very first time I have tried to install & use any form of Linux, so please be gentle in your responses :)

I have my system ready for installation as far as I can tell.  I have Vista Ultimate booting right now off my primary HD which I have just partitioned to make room for Ubuntu.  Am I right in saying I can now just install Ubuntu onto this empty partition and, once installed, my system will show an option screen at boot-up so I can choose between Vista & Ubuntu?

Thanks for your time :D

---

### Post by caffienefree on 2007-04-12
Yes. However, you may need to repartition the space you made available into a linux filesystem, and make a second for swap. The LiveCD installer will take care of this when it walks you through it. A boot menu called GRUB will be installed, which gives you the choice between ubuntu and vista when you boot up.

---

### Post by justleen on 2007-04-12
IF you have created a parition to use for ubuntu, you will have to add a swap partition during setup.

If you created free space, you can select " use available free space"  and the setup wil do it for you.

---

### Post by Bubby on 2007-04-12
Ok, that's great thanks guys.

Will try this out when I get home from work.  Looking forward to it :)

---

### Post by AndyCooll on 2007-04-12
The link in my signature is a good place too start.

---

### Post by Stickee on 2007-04-12
I'm a n00b at this as well, and just did this yesterday.  Here's a brief, very simple description of the steps that I took (with useful links): [http://jms.suite505.com/?p=15](http://jms.suite505.com/?p=15)

Everything's working so far.

:)

---

### Post by delilahjed44 on 2007-04-12
> **Stickee said:**
> I'm a n00b at this as well, and just did this yesterday.  Here's a brief, very simple description of the steps that I took (with useful links): [http://jms.suite505.com/?p=15](http://jms.suite505.com/?p=15)

Everything's working so far.

:)

[COLOR="DarkRed"]Hey everyone, I accidentally re-installed Ubuntu 6.06 over 6.10, I am waiting for Feisty to come out, reboot into the highest kernel and download from Ubuntu... my question is....the process this person whet through, How can I do this after installation of Fiesty> its my understanding that once your in windows, you hardware works to that window, printer scanner, and once you open it Ubuntu it only see Ubuntu with printer and scanner working, as it works find now.  Oh and what about programs that would not work in Ubuntu, but once worked in windows xp, If I creat dual boot, does anyone know if they would then work in Windows xp when I dual boot? thank you, of course I would have to re-install them in XP

Sherri[/COLOR]

---

### Post by delilahjed44 on 2007-04-13
[COLOR="DarkRed"]Ok Sticky, thanks on this, I am not sure how this will be with Fiesty, I suppose like Ubuntu you can load it up to a disk, we shall see, I will just use NTFS for windows then and see what I can do with the remaining Partition, I have 512 MB of ram, so I hope I see my choices there.  Thanks again

Sherri[/COLOR]

---

### Post by merlinof2 on 2007-04-21
I may need a little assistance here too. 
I took a new 160Gb HD and installed 2K pro on the entire disk.  (I'm practicing to dual boot on my notebook).  I then installed Fiesty (7.04) and told it to resize the partition and use the free space for Ubuntu.
Everything seemed to work fine.  Installation went smoothly and Ubuntu runs perfectly.  Enabled the restricted nVidia drivers and edited the xorg.conf file to up the resolution to 1280x1024.  kewl !!!
But.  Winblows BSD's on boot muttering something about an "inaccessible boot device".  Now in the past I seem to remember that's booting to a partition that isn't marked as active to windows.
Has anyone got this configuration working?  I want to install Ubuntu on my notebook that already has XtraPoor installed on a 50Gb disk.  This could make immeasureably easier for me...
Thanks in Advance
don.m

---

