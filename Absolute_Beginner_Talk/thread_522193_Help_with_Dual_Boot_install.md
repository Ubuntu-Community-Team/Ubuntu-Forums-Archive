---
title: "Help with Dual Boot install"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by movienut50 on 2007-08-10
I have 2 hard drives and this is the way I want my system to be:

drive 1: /dev/hda1  for windows xp (ntfs)

drive 2: /dev/hdb1  for Ubuntu Linux (ext3)
             /dev/hdb2  Linux swap
             /dev/hdb3 shared partition (fat32)

The problem I'm having is that Linux install installs GRUB in my MBR on drive 1.

I tried to get around this by unpluging drive 1 while installing Ubuntu on drive 2. I also changed the boot.ini  on drive 1 (c:\Boot.ini) for windows to allow for booting of Ubuntu or Windows.
To do this I used System Rescue CD and did the following:
mkdir /mnt/osshare
mount -t /dev/hdb3 /mnt/osshare
dd if=/dev/hdb1 of=/mnt/osshare/ubuntu.bin bs=512 count=1
rebooted into windows xp and copied the ubuntu .bin to the c:\
added this line to the boot.ini file= C:\ubuntu.bin=”Ubuntu Linux”

Windows Xp boots fine and so does Ubuntu if drive 1 is unplugged, but when I have both drives active and try to boot into Ubuntu I get a blank screen and blinking cursor.

I am very new at linux so can someone please help me solve this

---

### Post by carloslosgrande on 2007-08-10
[FONT="Comic Sans MS"]Hi, have a look at this site;>  [http://www.psychocats.net](http://www.psychocats.net) has lots of stuff relating to what you're trying to do.
Also, a related, and just as good, site; > [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)[/FONT]

---

### Post by Hospadar on 2007-08-10
You could just unplug drive 1 whilst instlling linux.  I've always found this to be the easiest way to get the mbr to go where I want it to.
Edit: my bad, i see you already did this, so try going right below first.

Also, I would suggest if you go this route, that if you are using ide drives on the same cable, that you plug the ubuntu drive with grub in it into the master plug on the cable (it's usually the middle plug) often drives won't woot right if the mbr you are trying to use is on the slave plug.

Ideally, You will then boot into grub every time, and if you want to use windows, you can select it from there.

---

### Post by mike102282 on 2007-08-10
> **Hospadar said:**
> You could just unplug drive 1 whilst instlling linux.  I've always found this to be the easiest way to get the mbr to go where I want it to.

Also, I would suggest if you go this route, that if you are using ide drives on the same cable, that you plug the ubuntu drive with grub in it into the master plug on the cable (it's usually the middle plug) often drives won't woot right if the mbr you are trying to use is on the slave plug.

The master plug is on the end not the middle.

---

### Post by lgambett on 2007-08-10
If you use the alternate install CD then during the installation you will be asked where you want to put the MBR. I love the alternate install CD....

---

### Post by MindRiot on 2007-08-10
First of all, I don't understand your post.

If Windows XP is installed on drive 1, then it should be impossible to load Windows XP if you have it unplugged.

What is wrong with installing Grub to drive 1?

I don't think you can chainload Windows XP if Grub isn't installed in the mbr of the drive with Windows XP.

---

### Post by acaby on 2007-08-11
First of all on the issue of how to connect the master and slave drives you need to go to this url as it explains this situation perfectly:[http://www.mikeshardware.com/howtos/howto_connect_ide_hd.html](http://www.mikeshardware.com/howtos/howto_connect_ide_hd.html)

On the second issue I found that using super grub solves the problem of booting from 2 drives.
I have win98/Ubuntu on drive 1 and Ubuntu Ultimate on drive 2. As previously stated in several posts you need to unplug your primary drive and just install your Ubuntu ISO on the secondary.
and reconnect your primary.
Next you need to get a copy of Super Grub i.e. sqd-current.iso (just google it and it will appear) burn it to a cd and boot from it. It will give you options under the menu item "Special Boot" just follow the prompts and you should be ready to rock and roll. Be advised that You must ALWAY's use the CD Boot if you have the intention of using the second drive. If not then boot as usual from primary and use the Grub installed in your MBR.

Hope this helps
Arthur

---

### Post by movienut50 on 2007-08-11
Thanks for all the info. Now I just have to decide which way I need to go

---

### Post by jingo811 on 2007-08-11
I dunno about your hardware intentions.  But when it comes to the Dual Boot install part try my guide.  You can become my guniea pig :)
[http://virtualseafarer.com/renaissance/allsparks/index.html#intro](http://virtualseafarer.com/renaissance/allsparks/index.html#intro)

Make your complaints in this thread when you're finished.
[http://ubuntuforums.org/showthread.php?t=521310](http://ubuntuforums.org/showthread.php?t=521310)

---

### Post by movienut50 on 2007-08-11
OK let me ask another question. Since if I unplug the power from my XP drive Ubuntu boots perfectly & when I plug the drive power back in and XP boots like it should is ther nothing that I can put in my "boot.ini" file that will let me pick Ubuntu and it boot?

---

### Post by confused57 on 2007-08-11
> **movienut50 said:**
> OK let me ask another question. Since if I unplug the power from my XP drive Ubuntu boots perfectly & when I plug the drive power back in and XP boots like it should is ther nothing that I can put in my "boot.ini" file that will let me pick Ubuntu and it boot?

You might try connecting your Ubuntu drive as master, Windows as slave...then add an entry to your menu.lst to boot Windows:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

You could also boot first to your Ubuntu drive connected as slave, then add an entry to boot your Windows drive.

---

### Post by movienut50 on 2007-08-11
Thanks everyone for all the help. I'm booting up normally now.

The fun part of learning linux starts now!

---

