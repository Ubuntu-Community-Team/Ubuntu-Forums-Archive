---
title: "[Ubuntu server] Grub error"
date: 2009-05-29
forum: Apple Hardware Users
---

### Post by koetjesreep on 2009-05-29
Best,

I'm sorry, but i have looked everywhere on the forum but have not found any solution jet.

I have a Macbook Pro (dual core, 32bit) and want to install Ubuntu server on it.
The installation is running well, but at the point that Grub want's to install, i get a red screen and it says: fatal error installing GRUB.

From this point, the installation failed. 
What can i do?

---

### Post by cyberdork33 on 2009-05-30
what version of Ubuntu?

Check out the mactel installation instructions here:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by koetjesreep on 2009-05-31
Thank you for your reply, 
I have the lastest Ubuntu server version (32-bit).

All the manuals are for ubuntu desktop.

I have a macbook pro and want 1 OS, Ubuntu server.
But on the end of the installation i get the Grub error :(
From that point the laptop can't start properly and i have to begin from point one.

---

### Post by cyberdork33 on 2009-05-31
> **koetjesreep said:**
> Thank you for your reply, 
I have the lastest Ubuntu server version (32-bit).

All the manuals are for ubuntu desktop.

I have a macbook pro and want 1 OS, Ubuntu server.
But on the end of the installation i get the Grub error :(
From that point the laptop can't start properly and i have to begin from point one.
is there any reason you are installing the server edition on a laptop? If you are looking for a commandline system only, the normal version can do that for you.

you are likely going to have to install grub manually.
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

---

### Post by koetjesreep on 2009-05-31
I wan't a sort of NAS system. So a system that can download torrents and from usenet. Also i want a Web server (for php and mysql). Is the normal desktop version good for this?

I'm following this manual:
[http://samiux.wordpress.com/2008/08/12/howto-home-made-nas-server-with-ubuntu-8041-&#8211;-part-ii/](http://samiux.wordpress.com/2008/08/12/howto-home-made-nas-server-with-ubuntu-8041-&#8211;-part-ii/)

---

### Post by cyberdork33 on 2009-06-01
> **koetjesreep said:**
> I wan't a sort of NAS system. So a system that can download torrents and from usenet. Also i want a Web server (for php and mysql). Is the normal desktop version good for this?

I'm following this manual:
[http://samiux.wordpress.com/2008/08/12/howto-home-made-nas-server-with-ubuntu-8041-–-part-ii/]("http://samiux.wordpress.com/2008/08/12/howto-home-made-nas-server-with-ubuntu-8041-%E2%80%93-part-ii/")
well, you could start from a CLI system, or do a server install. Since you actually want to put a webserver on it, then the server edition might be easier to get things setup.

If you don't want to dedicate this machine to use as a server, it might be easiest to install this NAS-server in a VM like virtualbox. It would then run on your desktop and you can run it only when you need to. but to each their own...

I would suggest getting a copy of rEFIt and making a CD/USB drive that you can boot i needed:
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Now the issue that is going to cause you problems is the fact that your Mac has a GPT-formatted hard drive (which is normal for a machine with EFI instead of a BIOS), but GRUB is unable to use GPT. Thankfully, Apple created an emulated BIOS and legacy MBR-formatting for booting a "legacy OS" (i.e. bootcamp). However, if you are single-booting Linux, it might just be easiest to repartition your drive to the MBR style rather than deal with the GPT and syncing to the MBR. You can use gparted to do this.

---

### Post by koetjesreep on 2009-06-02
I isn't working.
Now i was testing gentoo (grub installed on it). But now isn't my keyboard working after installation.
Maby this things are not good for me :(

---

### Post by k49 on 2009-06-02
I just had the same error, and would appreciate some help! I installed the the desktop version, also on a MacBook (not pro) 5,1, hoping to dual boot with Mac OS X. I used the alternate CD, since I can't boot from the live CD.

Using rEFIt, I can get to a prompt that says "grub" (so clearly *something* got installed, but maybe not GRUB itself). I followed some instructions to type "find /boot/grub/stage1", but apparently this file does not exist.

Some other instructions involved booting from a live CD, but obviously that's not going to work (I'm currently using Mac OS X). I read something about a bug in which the Ubuntu installer wipes out the partition table, but according to rEFIt's partitioning tool that doesn't seem to have happened. The information I've found is quite confusing. Can anyone explain what's going on?

---

### Post by cyberdork33 on 2009-06-04
> **k49 said:**
> I just had the same error, and would appreciate some help! I installed the the desktop version, also on a MacBook (not pro) 5,1, hoping to dual boot with Mac OS X. I used the alternate CD, since I can't boot from the live CD.

Using rEFIt, I can get to a prompt that says "grub" (so clearly *something* got installed, but maybe not GRUB itself). I followed some instructions to type "find /boot/grub/stage1", but apparently this file does not exist.

Some other instructions involved booting from a live CD, but obviously that's not going to work (I'm currently using Mac OS X). I read something about a bug in which the Ubuntu installer wipes out the partition table, but according to rEFIt's partitioning tool that doesn't seem to have happened. The information I've found is quite confusing. Can anyone explain what's going on?
i wasn't aware that the LiveCD did not work on your hardware. Are you passing the noacpi kernel option?

---

