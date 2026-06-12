---
title: "dual booting xp and ubuntu"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by bradruca on 2008-01-13
hi everyone ive never had linux before and trying to get it installed w/windows xp still loaded. ive asked a couple of people and they all tell me this is the part they've never had a problem at. i have ubuntu installed good to go then it promps me to reboot i do and instead of going to the GRUB menu like it should xp just loads i switched the bios to boot off the hard drive (that was a suggestion but it was already done) tried my F keys to bring up my boot menu and its windows boot menu with no option for Ubuntu i donno whats going on everything went so smooth up to this point please help thanx!!!!!!!

Brad

---

### Post by overdrank on 2008-01-13
> **bradruca said:**
> hi everyone ive never had linux before and trying to get it installed w/windows xp still loaded. ive asked a couple of people and they all tell me this is the part they've never had a problem at. i have ubuntu installed good to go then it promps me to reboot i do and instead of going to the GRUB menu like it should xp just loads i switched the bios to boot off the hard drive (that was a suggestion but it was already done) tried my F keys to bring up my boot menu and its windows boot menu with no option for Ubuntu i donno whats going on everything went so smooth up to this point please help thanx!!!!!!!

Brad

Hi and do you have more than one hard drive? It maybe that the grub did not install.

---

### Post by sandysandy on 2008-01-13
please post output of [COLOR="Red"]sudo fdisk -lu
[/COLOR]
regards

---

### Post by bagguley on 2008-01-13
Brad

What disk did you use to install (ie live disk/altewrnative disk) and what version are you installing?

---

### Post by bradruca on 2008-01-13
im using a livecd ver. 7.10 i have 2 drives 160gb that has xp and 500gb that linux partitioned (pretty much split it in half)   as for the output of sudo fdisk -lu i aplogize i dont know where do i get that so i can tell you? thanks 

Brad

---

### Post by bagguley on 2008-01-13
[This]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/") may help you. You may need to make sure that CD is the primary boot device in your bios settings.

---

### Post by bagguley on 2008-01-13
Or you could always forget windows completely!

---

### Post by bumanie on 2008-01-13
To do a sudo fdisk -l you need to open terminal and type sudo fdisk -l and hit enter. Put in your password when prompted and cut and paste the output to the forum. You get to terminal Applications --> Accessories --> terminal (from the list).

---

### Post by Hawkhunter on 2008-01-13
Howdy Folks,this my first post so I will try to be helpful,and clear at the same time.
I just spent the last 3 days trying t install Ubuntu 7.10...in as many ways as are possible I think.
I ended up trashing the Boot thingy(?) for both drives as well.
In the end ,I had to reformat both drives for XP and Ubuntu and Reinstall.

I finally noticed that I had a Jumper installed on the First drive,which I think Bunged up the Grub Booter and Confused the whole process.

After I pulled the Jumper,Reinstalled XP,and used the Text only Installer CD...it booted up Perfect for me.

Praise be to the Gods!!
And especially to everybody Here on the Forums!!!!!!!!!!!!

I don't know if this will help,,,but I hope nobody has to go through what I just finished messing with about an hour ago.](*,)]
Thanks Everybody!!!!!

Hawk  :P):P
Thanks Everybody]!!!

---

### Post by Victormd on 2008-01-13
> **bradruca said:**
> hi everyone ive never had linux before and trying to get it installed w/windows xp still loaded. ive asked a couple of people and they all tell me this is the part they've never had a problem at. i have ubuntu installed good to go then it promps me to reboot i do and instead of going to the GRUB menu like it should xp just loads i switched the bios to boot off the hard drive (that was a suggestion but it was already done) tried my F keys to bring up my boot menu and its windows boot menu with no option for Ubuntu i donno whats going on everything went so smooth up to this point please help thanx!!!!!!!
Brad

First of all, backup all of your data...

A couple of options for you. Right now, based on what I read, your Master HD has your Windows installation and your Slave HD has your Ubuntu installation. Depending on your BIOS Version, you can set it up so it boots from the Slave HD. If you can do this, then do it and re-install Ubuntu and everything should be fine (Keep in mind that by doing this, now you have to set your boot drive as your slave). If your BIOS does not allow this, than you can physically switch your primary and slave drives (open up your comp. and move some jumpers around on your HDs). Doing this, you will temporarily loose your windows boot (switch back and you should have your windows boot back - this is theoretical, I've never done this, my BIOS lets me choose what HD to boot from). Re-install Ubuntu and the installation will detect Windows (it's still present in your MBR - Master Boot Record). You should be good to go.

Just a note, this should be your boot options:
First boot device: CD-ROM
Second boot device: HD - Slave (if your BIOS allows)
Second boot device: HD (if you have to physically switch)

Once it's installed, you can make your HD your first boot device.

Another alternative, more straight forward, is to create a partition on your Master HD (the one with Windows installed) and install Ubuntu on that partition. You can do this using progz like Partition Magic or take a look at this link (for XP): [http://support.microsoft.com/kb/313348](http://support.microsoft.com/kb/313348)
or this one for Vista:
[http://www.pcworld.com/article/id,132079/article.html](http://www.pcworld.com/article/id,132079/article.html)

I personally prefer this last alternative as it is much simpler... Good luck!

---

### Post by Victormd on 2008-01-13
> **Hawkhunter said:**
> I finally noticed that I had a Jumper installed on the First drive,which I think Bunged up the Grub Booter and Confused the whole process.

After I pulled the Jumper,Reinstalled XP,and used the Text only Installer CD...it booted up Perfect for me.

Since you re-formatted, you could have used the LiveCD with no problem as long as Windows was the first OS you installed. Ubuntu should be the last installed OS - ALWAYS - this avoids a lot of headache.

---

### Post by bradruca on 2008-01-13
ok here's what i have when i type in sudo fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

hope it helps u help me thanx again

Brad

---

### Post by Hawkhunter on 2008-01-13
> **Victormd said:**
> Since you re-formatted, you could have used the LiveCD with no problem as long as Windows was the first OS you installed. Ubuntu should be the last installed OS - ALWAYS - this avoids a lot of headache.

Yes..probably,but I have an Ati 1900 that was giving me fits with the install as well.I had to Downgrade back to my Old X800 XT til I get the newer drivers installed.

Thanks...
Hawk:):)

---

### Post by Victormd on 2008-01-13
Bradruca, take a look at my previous post. I was thinking about it and I think that your easiest and best bet is in fact to partition your primary HD and install Ubuntu on that partition. Then all your OSs will be on the same HD and boot should not be an issue any more...

---

### Post by Victormd on 2008-01-13
> **bradruca said:**
> ok here's what i have when i type in sudo fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

hope it helps u help me thanx again

Brad

Brad, this is just the usage, you forgot the "-l" open the terminal and type:
sudo fdisk -l
then post that, and don't worry, starting off in a new OS is hard, but in the case of Ubuntu, well worth it!

---

### Post by bradruca on 2008-01-13
ok here it is 

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30862   247898983+   7  HPFS/NTFS
/dev/sda2   *       30863       60424   237456765   83  Linux
/dev/sda3           60425       60801     3028252+   5  Extended
/dev/sda5           60425       60801     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaaf4aaf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sdb2           16709       19457    22081342+   7  HPFS/NTFS

thanx again 

Brad

---

### Post by Victormd on 2008-01-13
Ok, this is the first time I'm trying to decode these results so anyone, feel free to jump in and help us out.

> **bradruca said:**
> 
Device    Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30862   247898983+   7  HPFS/NTFS
/dev/sda2   *       30863       60424   237456765   83  Linux
/dev/sda3           60425       60801     3028252+   5  Extended
/dev/sda5           60425       60801     3028221   82  Linux swap / Solaris


This section shows that your partition with Linux is set as your boot partition - but this should be the results for your primary HD and from what I understood, you have the linux partition on your second HD. Is this right?

---

### Post by bradruca on 2008-01-13
thats correct the 500gb isnt the master it is the slave the 160 gb is the master drive

---

### Post by Victormd on 2008-01-13
> **bradruca said:**
> im using a livecd ver. 7.10 i have 2 drives 160gb that has xp and 500gb that linux partitioned (pretty much split it in half)

Ok, let's quit messing around and find a solution for you.
Please correct me if I'm wrong but during install, you let Ubuntu decide how to partition your HD. This is fine, but I would suggest a different approach:
1. boot Windows
2. Partition you 160Gb HD manually using Windows.
     a. Create a 10Gb Partition for your Ubuntu installation;
     b. Create a ~512Mb Partition for your Ubuntu swap (don't worry about formatting any of these partitions);
3. Make sure your BIOS is set to boot from the CD, insert the CD and restart your computer, login to Ubuntu and begin the installation process.
4. During installation, Ubuntu will ask you how to manage the HD partitions. The default is automatic (probably what you did initially). Set this to Manual.
5. You will then be given the option to choose where Ubuntu will be installed. Choose the 10Gb partition that you created for your Ubuntu installation and set it to type "/" (you can select this from a drop-down menu).
6. Select the 512Mb partition and select the type "/swap"
7. Continue the installation process normally from here on and everything should work out!
Please let me know how this worked out for you!
Good luck!

---

### Post by bradruca on 2008-01-13
in step 5 is that the prepare partitions screen or after that step?

i ask because when i go to type "/" isnt an option, however "/swap" is available almost there, i think tanx again

Brad

---

### Post by Victormd on 2008-01-13
Yes, this is on the prepare partitions screen. It's actually a 2 step process.
You select the "Manual" option (click next), then you first select the partition to install Ubuntu (double click, an option screen will pop up) and select the file system (ext3), click Ok, then double click the partition again and select "/" as the mounting point (I'm not in front of the install screen so I'm not sure these are the right words used). For the swap partition, you select the partition (double click) and on the option window, select the file system as SWAP and that's it.

---

