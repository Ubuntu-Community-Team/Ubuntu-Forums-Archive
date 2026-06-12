---
title: "More than 80s boot time!!! What's wrong in my bootchart?"
date: 2011-07-13
forum: Any Other OS
---

### Post by PC_load_letter on 2011-07-13
I'm running 64bit LinuxMint Katya (based on Ubuntu 11.04). Can the bootchart experts tell me what's taking so long, and what to do about it. Thanks.

Here (image too large to embed, size about 640k):
[http://img694.imageshack.us/img694/8053/lallkatya201107131.png]("http://img694.imageshack.us/img694/8053/lallkatya201107131.png")

---

### Post by oldfred on 2011-07-13
I have never learned to read boot charts.

You may want to remove the vga= entry in grub. 
vga=xxx is a deprecated boot option
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

VGA conversions:
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
# after changes to grub file always run this:
sudo update-grub 

Are you mounting a lot of NTFS partitions. That is always slower. Have you run chkdsk on all the NTFS partitions recently? That can help.

---

### Post by PC_load_letter on 2011-07-14
I'll follow your advice for the monitor. As for NTFS partitions, there are two virtual partitions on one of the two SATA hdds. They're not auto-mounted on login though. Anyway, thanks for the advice.

---

### Post by devil103 on 2011-07-15
I have a very similar bootchart with the same problema and I'm not even running Unity or Gnome! Just an XBMC mediacenter running on X!

I'll attach my bootchart as well and hopefully we can make something out of this and formulate a solution.

[(click) for bootchart](http://imageshack.us/photo/my-images/225/bootcharty.png/)

---

### Post by Mark Phelps on 2011-07-15
PC_load_letter: I'm not an bootchart-reading expert ... but in looking through the task list, I only see a few items that are unusual, like cairo-dock.

Speeding up boot is generally a process of getting rid of things you don't want loaded at startup.  In Windows, for example, I had a disk temp applet that took a LONG time to load -- delaying the desktop by more than a minute!  So, I removed it from the startup list, and now, load it manually.

I noticed a lot of "k" items, implying that you may be either running a KDE desktop, or launching kde-based apps.

Sorry, but nothing major jumped out that you can remove to shorten boot -- without losing functionality.

devil103: Your chart is way too small to read.

---

### Post by devil103 on 2011-07-15
> **Mark Phelps said:**
> PC_load_letter: I'm not an bootchart-reading expert ... but in looking through the task list, I only see a few items that are unusual, like cairo-dock.

Speeding up boot is generally a process of getting rid of things you don't want loaded at startup.  In Windows, for example, I had a disk temp applet that took a LONG time to load -- delaying the desktop by more than a minute!  So, I removed it from the startup list, and now, load it manually.

I noticed a lot of "k" items, implying that you may be either running a KDE desktop, or launching kde-based apps.

Sorry, but nothing major jumped out that you can remove to shorten boot -- without losing functionality.

devil103: Your chart is way too small to read.

You're quite right! I didn't notice the forums resized my image. I've uploaded the image to imageshack and edit my previous post! Thanks in advance

---

### Post by PC_load_letter on 2011-07-16
> **Mark Phelps said:**
> PC_load_letter: I'm not an bootchart-reading expert ... but in looking through the task list, I only see a few items that are unusual, like cairo-dock.

Speeding up boot is generally a process of getting rid of things you don't want loaded at startup.  In Windows, for example, I had a disk temp applet that took a LONG time to load -- delaying the desktop by more than a minute!  So, I removed it from the startup list, and now, load it manually.

I noticed a lot of "k" items, implying that you may be either running a KDE desktop, or launching kde-based apps.

Sorry, but nothing major jumped out that you can remove to shorten boot -- without losing functionality.


Thanks for your input, I do use Cairo-dock, and I have a few KDE apps, nothing major, just K3B and KTorrents. So maybe between these apps and the NTFS partitions, it explains the 80s boot. 

It's a far cry from the touted 10s in Maverick. I know there was a regression in Natty so it takes longer to boot, but from about 10s to more than 80s is a bit too much.

---

### Post by NightwishFan on 2011-07-16
> **PC_load_letter said:**
> It's a far cry from the touted 10s in Maverick..
Marketing. The 10s is targeted at lightweight machines with SSDs.

---

### Post by oldfred on 2011-07-16
Boot time for both my Desktop & laptop are 50-60 seconds. I consider that good as XP takes 4-5 minuters. So now I do not boot XP much.:)

Some minor tweaks are to make sure BIOS is not loading floppy unless you have one, that HD is first on boot list in BIOS, and review startup applications and turn off Bluetooth if you do not have it or any other startups that do not apply.

---

