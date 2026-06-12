---
title: "Ubuntu uninstall"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by master.zen on 2007-02-14
So I installed ubuntu on my windows media center pc. I've decided it's not my kind of OS so I tryed restarting pressing F12 to install windows media center again and it won't work so how do I uninstall ubuntu and get my old OS Back :\ Thanks

---

### Post by javaJake on 2007-02-14
OK, you need to put in your disk, and let it boot up. (If you can boot off of the Ubuntu CD, you know your BIOS is set correctly, and your Media Center CD should boot.) It'll say "Press any key" or something like that, so push a key. That should do it.

I'm not sure why you'd push F12 key to boot the installation, unless pushing F12 forces your BIOS to ask what to boot off of.

---

### Post by Spike-X on 2007-02-14
Did you wipe over your Windows installation when you installed Ubuntu? If so, you'll probably have to reinstall Windows from the install CD.

---

### Post by Maestro23 on 2007-02-14
[http://ubuntuforums.org/showthread.php?t=341933&highlight=uninstall+ubuntu](http://ubuntuforums.org/showthread.php?t=341933&highlight=uninstall+ubuntu)

---

### Post by master.zen on 2007-02-14
I dont have a windows cd my os is built in on the computer and sorry i was mistaken its F10 And thats suppost to be system recovery but it wont work

---

### Post by javaJake on 2007-02-14
> **master.zen said:**
> I dont have a windows cd my os is built in on the computer and sorry i was mistaken its F10 And thats suppost to be system recovery but it wont work

Hmmm... not sounding good. It might be that the CD has to be booted within Windows, which doesn't make a whole lot of sense, actually.

Are you sure there are no instructions about how to use this?

---

### Post by Maestro23 on 2007-02-14
> **javaJake said:**
> Hmmm... not sounding good. It might be that the CD has to be booted within Windows, which doesn't make a whole lot of sense, actually.

Are you sure there are no instructions about how to use this?

If he had is CD, sounds like he has a proprietary copy windows like that are shipped with Gateways, Dells, HPs, Compaqs, etc... Those can be a pain-in-the-backside for certain things.

Probably has a Recovery partition as well.

Did the OS come pre-installed on the HDD, but provide you no source disc?  If so, did it tell you to make some resuce discs?

---

### Post by master.zen on 2007-02-14
Did the OS come pre-installed on the HDD, but provide you no source disc? If so, did it tell you to make some resuce discs? yes it did come pre-installed with no disc and sadly no I never made a recovery disc

---

### Post by nodegamra on 2007-02-14
By any chance, do you have an hp sounds like it? when you installed Ubuntu did you selected the "use the whole drive" selection? If you did forget about getting MCE back. If it is an HP then the only thing you can do is to order the restore cd from the support page.
Hope this helps, good luck.

---

### Post by master.zen on 2007-02-14
> **nodegamra said:**
> By any chance, do you have an hp sounds like it? when you installed Ubuntu did you selected the "use the whole drive" selection? If you did forget about getting MCE back. If it is an HP then the only thing you can do is to order the restore cd from the support page.
Hope this helps, good luck.

Can I get a link? thanks for all the help guys

---

### Post by Dr Small on 2007-02-14
You have to press F10 (I think it is) when booting, go into the system recovery, and do a destructive recovery (for compaq) and then it should resinall Windows, because is has a recovery OS on another partition.
(Least ways, that's the way my Windows Media Center Addition Compaq PC is)

Dr Small

---

### Post by nodegamra on 2007-02-14
well what model do you have?

---

### Post by Dr Small on 2007-02-14
???
What do you mean what model? Is there a model number somewhere you want me to look for or something?

Dr Small

---

### Post by PurplePenguin on 2007-02-14
What's written below COMPAQ on the front of the computer?

---

### Post by haricharan on 2007-02-14
can you log into Ubuntu again and open up Applications->Accessories->Terminal and type the following
```
sudo fdisk -l
```
copy paste the output you get here...lets see if you still have the recovery partition!!!

---

### Post by highneko on 2007-02-14
> **master.zen said:**
> I dont have a windows cd my os is built in on the computer and sorry i was mistaken its F10 And thats suppost to be system recovery but it wont work
I have an hp computer too. Had a similar problem. We should ask for a warning when installing the partition. I deleted my recovery so I could have more space for Linux and kept Windows. I thought because I had restore disks it would work, but it didn't. I says it's gonna install then at disk#3 it said there's an error. A few months ago when I had the problem I took screen shots with my camera. I still have the recovery disks but because I deleted my windows partition windows won't work. If there's another reason why I don't know it. It's a similar problem I think. I'll attach some screen shots.

Lucky for me I had been using Linux for a year when this happened and actually hated windows. So I didn't care. It's a Microsoft way of getting every penny from you.

Your old media center partition should have had an option to burn recovery cds. They didn't help me, but they might for you.

Good luck, have fun.

---

### Post by Dr Small on 2007-02-14
> **PurplePenguin said:**
> What's written below COMPAQ on the front of the computer?
It doesn't have a COMPAQ sticker anywhere on the machine.
But, when it boots up, the first boot screen says Compaq.....

Dr Small

---

### Post by Dylnuge on 2007-02-14
Ok.

A model number or name is the name of the computer you purchased. For example, Presario, or Sattelite. That part is the name. The number is after it.

This information would be available with the documentation resources you recieved with your computer, or on the underside of your laptop, if not stamped or embedded on your system.

Now, one thing I notice is that your recovery may not work at all if it relied on a special, preset MBR to run. You don't need to understand what that means, I am just pointing it out for some of the more experianced members of the fourm, as they may be able to help you better then I am.

Here is what you can try:

Boot off the Ubuntu LiveCD.
Click Applications on the top of the screen.
Point to Accessories, then click Terminal.
In the screen that pops up, type the folowing command:
```
sudo su -
```
This will be the equivilent of running all commands as root.
Type this command
```
fdisk /dev/hda
command (m for help): p
```
Post the results.

If you completly destroyed your hard drive (chose to erase all and partition from there), you have three options.

1. Use Ubuntu-It may not be what you wanted, but Windows is gone, so is your recovery partition, and so is your recovery cd.
2. Purchase Windows Vista-The **Full** Version, not the upgrade. Just install that and your computer will run Windows again.
3. Contact Compaq. This may be a problem, since from my experiances with computer manufacturers, they don't really like it when you mess with your hard drive. Since your hard drive is hardware, they may consider it a violation of your warrenty.

If partitions show up, there is some hope.

Good luck

---

### Post by master.zen on 2007-02-15
New problem I have windows xp professional disc I try to install windows xp proffesional but when I do I get the blue screen to install it and then it sais loading kernal debugger or something and it loads for ever and doesn't do anything

---

### Post by master.zen on 2007-02-15
> **haricharan said:**
> can you log into Ubuntu again and open up Applications->Accessories->Terminal and type the following
```
sudo fdisk -l
```
copy paste the output you get here...lets see if you still have the recovery partition!!!

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by master.zen on 2007-02-15
b.u.m.p

---

### Post by GTBee on 2007-02-16
I had a similar issue- I had completely reformatted my hard drive and installed Ubuntu.  I like it but need to go back to XP for some admin and back up tasks.  I could not reinstall XP even with the right install disc- I kept getting a drive mounted error or some such.  

I ran Ubuntu from cd (don't know if this is necessary) and reformatted my hard drive to Fat32.  After reformatting I was able to install Xp using the same install CD.

Good luck

---

