---
title: "Need a helping guru here, please,"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-04-16
Hi people, new [to ubuntu] user here who is totally confused. 

I recieved the CD for Version 6.06 today and now I'm not sure on how to procede.

I'm now using Win XP Home, sp2. One hard drive with the usual c:/d: partition with about 20 gigs of free space.

I would like to keep windoze and also install ubuntu in a dual boot config.

Problem is, in the CD folder it says that while installing the default it will erase all software and data. This is a no-no.

I read one of the stickies that shows the installation in a step by step manner. Am I correct in presuming that ubuntu will partion a portion of the hard drive for itself and leave everything else alone? Or do I have to partition the hard drive manually, say to drive X:, for the installation?

As I am the only user do I have to use a password when the PC asks which OS I want to use on boot-up?

Finally, would 5-6 gigs be enough for Dapper to run smoothly?

Thanks for any assistance,

Jon

---

### Post by Gorthus on 2007-04-16
If you just go through with an automatic "Repartition and install in free space", none of your Windows files will be touched in any way. You will NOT need to enter a password at the GRUB Menu (boot option thingy), but you will need to once you get into Ubuntu.

If you have any other questions please feel free to ask.

---

### Post by ParkingBrake on 2007-04-16
There should be an option to resize the partition which will leave Windows in tact and create a dual-boot system.

---

### Post by NeoLithium on 2007-04-16
One thing you should do before setting up a dual boot; is make sure you freshly defragment your hard drive; which will also help lessen the chances of anything happening. As well; it is always a good idea to back up vital stuff just in case something does go wrong.  While the install is easy; sometimes things can happen, it's somewhat rare; but better to be safe than sorry.

---

### Post by stmiller on 2007-04-16
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

This is a bootable live cd which will let you non-destructively resize your windows partition down to make room for Linux. Leave the latter half of the drive as unformatted free space.

Then run the ubuntu disc, telling it to install into that free space.

---

### Post by Wim Sturkenboom on 2007-04-17
I suggest that you make a backup of (important) data first. You would not be the first one where something goes wrong during the partitioning and all data is lost (e.g. because of a power failure at the wrong moment).

---

### Post by mcduck on 2007-04-17
> **stmiller said:**
> [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

This is a bootable live cd which will let you non-destructively resize your windows partition down to make room for Linux. Leave the latter half of the drive as unformatted free space.

Then run the ubuntu disc, telling it to install into that free space.

Ubuntu's live CD (and installer) does exactly the same thing,.. ;)

---

### Post by Romin-1 on 2007-04-17
Thanks for your replies guys.

Got it up and running, [mostly] now I have to see if I can migrate My Documents/programs into Dapper.

Also how to import Bookmarks into Firefox without burning them to a cd first.

Once again, thanks

Jon

---

### Post by hyper_ch on 2007-04-17
You can get read access to your ntfs drive.

(1) Open a terminal

(2) enter the following command:

```

sudo fdisk -l

```

That will list the partitions you have and then you see what the ntfs one is :)

(3) Make a folder for mounting the ntfs drive:

```

sudo mkdir /media/c_drive

```

(4) Mount it by issuing this command:

```

mount /dev/PARTITION /media/c_drive/ -t ntfs -r -o umask=0222

```

(Replace PARTITION with your actual one, e.g.  hda1 or sda1 (very likely one of those two)

Now you can browse to to the media/c_drive folder! However you have only READ access. No writing!

For more info you can look here:  [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)


For firefox: Well the profile is locatedin ~/.mozilla/firefox
~ --> Your home folder... this is normally /home/USERNAME

All you have to do it basically copy over the firefox profile from windows into the linux one :) and then you have to make sure that you have the right permissions. In order to do that make this:

```

sudo chown USERNAME:USERNAME -R /home/USERNAME/.mozilla/firefox/*

```

---

### Post by airtonix on 2007-04-17
or you could wait til this thursday and download the fesity release....

why?

because it will help you do all this automatically. it will help you import your bookmarks from explorer, mozilla, your settings from outlook(i think)....

you will possibly also have access to the beryl windows manager that will give you the 3d openGL rendered effects. think [macosx expose]("http://www.apple.com/macosx/features/expose/")

---

