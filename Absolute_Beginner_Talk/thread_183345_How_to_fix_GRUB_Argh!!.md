---
title: "How to fix GRUB? Argh!!"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by bigkahuna on 2006-05-27
I buggered up GRUB and need help fixing it.

I had a dual boot setup (Windows XP and Kantix/DebianSid) with GRUB as my boot manager.  I wanted to replace Kanotix with Ubuntu 5.10.  I started the HD installation, got as far as where it wanted me to format the partitions and I chickened out and aborted the installation.  Now GRUB is buggered and the system won't boot.  I booted off the Ubuntu live cd and my partitions are intact, it's just GRUB that's messed up.  How can I fix this?

I would like to get kanotix off the HD entirely and start with a freshly formated partition, but I don't know how to get rid of GRUB?

What do I do?  Help please!

---

### Post by Sef on 2006-05-27
Here's how:

[Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by tonyr on 2006-05-27
...and another one...
[URL="https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows"]
RecoveringUbuntuAfterInstallingWindows[/URL]

---

### Post by confused57 on 2006-05-27
You might consider booting up with the WinXP install CD, going into recovery mode, then entering "fixmbr"...this will restore your original Windows boot.ini

Once you have Windows "bootable",  then you can boot up with the LiveCD and use gparted to reformat the Linux partition...

Then you can install Ubuntu, I'd consider Dapper...of course the Ubuntu install CD can do the reformatting for you instead of using the LiveCD.

---

### Post by uzi09 on 2006-05-27
whao whao waho!

why would you make him format his linux partition????

it's just a matter of booting off a live cd, going to advanced installation, scrolling down to the part that installs Grub and reinstalling!

There is no need to make the poor guy format his whole partition!

---

### Post by bigkahuna on 2006-05-27
I'm still having problems:

hda1 is my windows partition
hda 5 is my linux swap partition
hda6 is my linux reiserfs partition

I follow the "restore grub" instructions and I got a "no boot partition defined" error.

---

### Post by confused57 on 2006-05-27
Here are instructions for dualbooting with Dapper:

[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

Here's a guide for dualbooting Breezy:

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)


Maybe I misunderstood, but I thought you wanted to reformat the Linux partition.  I personally would use the Ubuntu install CD to set up partitioning during install.

---

### Post by bigkahuna on 2006-05-27
UPDATE:
1.  I can't boot from my Windows install disk because the CD's that came with my computer (Sony Vaio notebook) only allows me to reformat and re-install original software... argh...
2.  I tried the "recovering windows after installing ubuntu" link and when I get to the "grub>" prompt I entered:  "find/boot/grub/stage1" and I get a "unrecognized command".  So I tried "find /boot/grub/stage1" and it says "File not found"... argh...

My linux partition was formatted in my first attempt, not a big problem.  I have several files I -really- don't want to loose on my windows partition and didn't get to back-up.  So that's my first concern  how do I get my system to boot to Windows again?

---

### Post by confused57 on 2006-05-27
Don't do this yet, someone may be able to confirm it; but you may be able to install Ubuntu on the Linux partition and the installer will overwrite your current grub menu to allow you to boot up Windows or Ubuntu.

Can you enter grub at all when your system is booting up, in Ubuntu you press "Esc" to enter the grub menu, I don't know anything about Kanotix.  If you can, there may be a "recovery" option like there is in Ubuntu that you can restore grub with?

---

### Post by bigkahuna on 2006-05-27
I'd really feel better if I were able to get these "critical" files off my notebook, so is there any fast/easy way to set up a network between my two computers?  I've got both my computers running Ubuntu 5.10 (one with HD install the other live CD), both are connected to my "Westell 327" router modem, and both are connected to the internet.  I guess I could email it from one computer to the other through the internet, but is there an easy way to just share a folder on the computer with the HD install?

---

### Post by uzi09 on 2006-05-27
try to throw in a live cd, mount ur windows drive and copy that stuff off of it

---

### Post by confused57 on 2006-05-27
See if there is anything in this thread that may help:

[http://www.ubuntuforums.org/showthread.php?t=180607&highlight=windows+boot](http://www.ubuntuforums.org/showthread.php?t=180607&highlight=windows+boot)

---

### Post by bigkahuna on 2006-05-27
[QUOTE=uzi09]try to throw in a live cd, mount ur windows drive and copy that stuff off of it[/QUOTE]
That's just what I did.  Since I was able to log onto the internet, I just emailed the files (about 50 mb total) from one computer to the other... kinda funny since they're about 12 inches apart ;)

I think I'll just play it safe / easy and just do a complete re-installation of Windows and then let ubuntu do it's normal install...  unless I find an easier way...

---

### Post by uzi09 on 2006-05-27
that's really odd the grub install didn't work.

perhaps you **could** try restoring the windows boot record (mbr) and then try to reintall grub over it again.

let us know what you come up with. btw, what exactly did it tell you when you tried to reinstall grub with the ubuntu cd?

---

### Post by bigkahuna on 2006-05-27
Well...  I was hoping I wouldn't have to do this, but looks like I've got to re-install windows and format my entire HD :(  I tried every bootable disk I have, and none of them allow me to run "fixmbr" (even tried my ancient Win95 boot disk, ha!).

I'd reformat and just install Ubuntu, dumping Windoze, but I've got 2 apps that -have- to run and they only install under windows (due to a copy protection scheme).  Oh well...

I'll be back when I'm done, I've got to figure out how to network these two puppies.  Thanks for the -fast- and helpful replies!!!

---

### Post by bigkahuna on 2006-05-27
Holy *%$#!  The Windoze restore disk didn't fix it!  Fortunately (whew!) I re-read the last post you suggested and saw the recommendation to stop the restore disk's progress and type "fdisk /mbr".  Wish I read that the first time.  At any rate, the system seems to be working now.  Next to re-install Ubuntu...

---

