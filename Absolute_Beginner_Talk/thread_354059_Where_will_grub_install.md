---
title: "Where will grub install?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by mr.v. on 2007-02-05
I have a computer I'm planning on installing Ubuntu on. Here's how things are configured. Oh /dev/hda1 I have Windows2000

I'm planning on installing ubuntu on a 20GB partition on /dev/hdb1
However, I just went through the manual partition but it doesn't specify where grub is to be installed. I REALLY don't want it to wipeout the MBR on /dev/hda but rather install it on the MBR of /dev/hdb I will then specify using bios to boot /dev/hdb first. I want to leave /dev/hda alone completely. I don't want to hit the next button in case I can't specify later.

So my question...where is grub going to go?

Will it ask me? Will I need to download the alternate install cd? Should I disable /dev/hda in the BIOS until after the install...then manually add it back to /etc/boot/menu.lst to boot it?

Thanks for the help. The alternate install CD seems to be for people with advanced grub configs (to say the superblock etc)...that's not really me. I just want to know which drive's MBR it will install to. If it's /dev/hda and not the drive that ubuntu will be installed on, then I guess I'll go ahead and download the alternate CD.

---

### Post by TAfricanski on 2007-02-05
Well I installed from the live CD and after repartitioning I was asked where I wanted GRUB to be installed. I specified fd0 and now my computer starts under Linux only with the diskette in the floppy. I think this is the best option ;) If the diskette is out, it just boots normally XP.

---

### Post by kebes on 2007-02-05
If you do a standard Ubuntu install, grub will be placed automatically in the MBR of the first drive. So you're going to need to run grub manually.

When you run the Ubuntu installer, you can cancel the step where it wants to install grub. I think if you do this, the rest of the system is already installed. (Or, you could do the setup with the Alternate CD, where it's easier to switch to a manual install mode and skip the grub step.)

In any case, you need to skip the grub installation during the install. Then in a LiveCD session, go to a terminal and use the commands "[grub]("http://www.die.net/doc/linux/man/man8/grub.8.html")" or "[grub-install]("http://www.die.net/doc/linux/man/man8/grub-install.8.html")" to install grub exactly where you want it. For instance:
grub-install /dev/hdb

This will install it to the MBR of hdb. You can also go "grub-install /dev/hdb1" to install it to a particular partition, but this is not the normal way of doing it. You can find more information about how to use it here:
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)


Hope that helps.

---

### Post by TAfricanski on 2007-02-05
Just curious... Did I do something strange in order to install GRUB during install on fd0 without having any MBR on my hard drive altered?

---

### Post by mr.v. on 2007-02-05
> Just curious... Did I do something strange in order to install GRUB during install on fd0 without having any MBR on my hard drive altered?

I'm using 6.06.1 Desktop CD...maybe the 6.10 installer has the option?
Or maybe you're using the Alternate CD?

---

### Post by kebes on 2007-02-05
> **TAfricanski said:**
> Just curious... Did I do something strange in order to install GRUB during install on fd0 without having any MBR on my hard drive altered?

I'm not sure. I'm working from memory here... but as I recall in the standard Ubuntu installer, it just says "Will now install grub" without options. Look at the screenshots here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I don't think it gives you any options. Of course, it's slightly different between the standard and alternate install disk, and between Dapper and Edgy installs.

---

### Post by Duck2006 on 2007-02-05
6 of 6 will give you where you want to install grub. You change (hd0) to (hd1) and grub will install to the MBR on hd1

---

### Post by mr.v. on 2007-02-05
> 6 of 6 will give you where you want to install grub. You change (hd0) to (hd1) and grub will install to the MBR on hd1

hrm. 5/6 was setting up my partitions and 6/6 was just a display of what would be formatted or not. I didn't ever see anything about grub. I went ahead like a crazy person but actually the installer+computer froze at 83% and I had to hold the power button to get a response (not even virtual terms would come up). I took that as a sign and downloaded the alternate cd (fortunately it didn't get to installing grub I guess =)

So I ran through the text based install on the alternate...I specified grub to install into /dev/hdb and it did that fine. I rebooted after install. Grub loaded but nothing would boot...neither the windows entry nor ubuntu.

So after the briefest of coronaries I booted with the alt-cd again and went to a shell...man that shell is useless...there's no vi/vim/emacs/joe or jed. I found nano to edit, but then tried to mount /dev/hdb1 but it said "no device" with both -t ext3 and -t ext2. Then I figured something was amiss with this shell/cd since it wouldn't mount /dev/hdb1

I went back to my old Slackware install CD, booted, and went to the prompt and was able to mount /dev/hdb1
Looking at /dev/hdb1/boot/grub/menu.lst the problem was readily apparent.

Grub was installed to the MBR in /dev/hdb like I said...but the BIOS reverses the drive order so these two were out of sync. Apparently the Ubuntu installer didn't realize what was going on (Fedora Core 6's installer did on my home computer which has this same config and set everything up just right).

So I simply changed Windows which had a root (hd0,0)  to rootnoverify (hd1,0) and remapped hd1 and 0.

I set the linux kernels back to root (hd0,0). rebooted and everything works...(for now =)

---

### Post by marx2k on 2007-02-05
> **TAfricanski said:**
> Well I installed from the live CD and after repartitioning I was asked where I wanted GRUB to be installed. I specified fd0 and now my computer starts under Linux only with the diskette in the floppy. I think this is the best option ;) If the diskette is out, it just boots normally XP.

Don't lose that floppy! ;)

---

