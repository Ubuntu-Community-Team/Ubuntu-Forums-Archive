---
title: "Mplayer"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by bobbyshafter on 2007-02-18
I am getting a error from Mplayer  ....fail to open dvd:// 1.

I am running edgy and dapper .Mplayer on dapper work

Edgy is setup with Beryl

---

### Post by taurus on 2007-02-18
Are you trying to play a DVD?

---

### Post by bobbyshafter on 2007-02-18
yes i am

The only tyrant I accept in this world is the still voice within.
Mohandas Gandhi

---

### Post by taurus on 2007-02-18
I find that vlc works better with DVDs.

---

### Post by Maestro23 on 2007-02-18
> **bobbyshafter said:**
> yes i am

The only tyrant I accept in this world is the still voice within.
Mohandas Gandhi

Something might have gotten switched. Do you have MPlayer pointed to the right device?  Check under the misc tab for DVD device.  Compare it to your /etc/fstab entry for your DVD drive.

---

### Post by bobbyshafter on 2007-02-18
I like MPLAYER because of the skins

I love eyecandy.


----------------------------------------------------


The only tyrant I accept in this world is the still voice within.
Mohandas Gandhi

---

### Post by bobbyshafter on 2007-02-20
I have tried inserting a dvd in my drive,it appear on my desktop as cdrom1

I then went inti misc and pointed it to cdrom1 

I still get a error

kaffiene will play the dvd,..Mplayer....movieplayer and totem will not

Any idea

---

### Post by bobbyshafter on 2007-02-24
Help Vlc wont play .Only Kaffeine will play DVD..

I look at /ect/fstab  it is blank

---

### Post by jordanmthomas on 2007-02-24
It's 
/etc/fstab
not
/ect/fstab

---

### Post by okzoolya@sbcglobal.net on 2007-02-24
:confused: sorry, i do not know how to post my own topic so i'm going to ask something here....    I've been trying to install ubuntu with a bootable cd that i have succesfully created, but every time i use the BIOS options to try to boot from the cd-rom drive, the screen displays "Strike f1 to retry boot, strike f2 to return to BIOS". Is it becuase my DELL sucks or is there a part of the process that i'm missing?

---

### Post by mgmiller on 2007-02-24
When you say you successfully created the boot disk, did you just copy the .iso file to the disk or did you use some application to expand the .iso to its original form on the disk?  If you look on the boot CD you created, there should be a number of files and directories, not just one big .iso file.  Assuming you did the .iso burn correctly, you would then make sure your boot order has the CD drive before the hard drive.  On my Dell laptop, I think the F12 key gives me the option to select the boot drive during post.

---

### Post by mgmiller on 2007-02-24
When you say you successfully created the boot disk, did you just copy the .iso file to the disk or did you use some application to expand the .iso to its original form on the disk?  If you look on the boot CD you created, there should be a number of files and directories, not just one big .iso file.  Assuming you did the .iso burn correctly, you would then make sure your boot order has the CD drive before the hard drive.  On my Dell laptop, I think the F12 key gives me the option to select the boot drive during post.   

From the sound of your post, I think you didn't burn the CD correctly.  It sounds like your BIOS is telling you you don't have a bootable CD in the drive.

What operating system and what software did you use to create the boot disk and how did you do it?

---

### Post by mgmiller on 2007-02-24
> I am getting a error from Mplayer ....fail to open dvd:// 1.

I also get the same mplayer error if the disk is in "the wrong drive".  I have 2 optical drives in my 'puter and all works fine with the disk in one of them, but not in the other.  This behavior started with Dapper and continues in Edgy for me.

---

### Post by TonKi on 2007-02-24
> **bobbyshafter said:**
> I like MPLAYER because of the skins

I love eyecandy.


vlc is skinable too 8-)

---

### Post by bobbyshafter on 2007-02-24
Thanks ,i now have vlc and mplayer working.

---

### Post by bobbyshafter on 2007-02-25
Great,thanks,

I now have all my dvd players working

---

### Post by bobbyshafter on 2007-05-14
my fstab           /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto 
             
                        /dev/scd1       /media/cdrom1   udf,iso9660 user,noauto



I tried /dev/scd0 ,/dev/scd1 ,then /media/cdrom0 , /media/cdrom1   none of these setting work

This is after upgrading to kubuntu 7.04

---

### Post by rggavubt on 2007-05-15
I'm having the same problem after upgrading from 6.06 to 6.10 to 7.04.  In Dapper I could play movies but not in Feisty.  I can't play DVD's on any of my movie players.  I'm getting the same mplayer error.  I go to the DVD drive and try to mount it with a DVD in the drive and get the error "unable to mount media, there is probably no media in the drive"  I think it is some problem with the /etc/fstab settings.  My two drives in /etc/fstab are set as "/dev/cdrom listed twice with  /media/cdrom0 & 1 following each one.  My drive are /dev/hdc and /dev/hdd with /dev/hdc being the DVD-ROM drive and /dev/hdd being a CD-RW drive.  It looks a lot of people are having the same problem after upgrading to Feisty.  I can play movies on the web or on my hard drive and I can play CD's.

---

