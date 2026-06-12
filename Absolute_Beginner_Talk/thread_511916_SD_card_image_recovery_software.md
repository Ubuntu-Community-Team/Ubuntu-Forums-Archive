---
title: "SD card image recovery software?"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by MickS on 2007-07-28
Is there any software available that will recover images from a corrupt SD card, when I put the card in my built in card reader Konquerer can't find anything on it but I know there is.
TIA

Mick

---

### Post by Pragmatist on 2007-07-28
With the card not inserted type this in a terminal:
```
tail -f /var/log/messages
```

Now insert the card and look for any messages on the terminal.  Do you see a mount point that looks something like this: /dev/sda /dev/sdb1 /dev/sde  or anything similar?

---

### Post by MickS on 2007-07-28
This is what comes up when I do that, any use?
Thanks

Mick


mick@mick-desktop:~$ tail -f /var/log/messages
Jul 28 18:28:23 mick-desktop gconfd (mick-8256): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 28 18:28:23 mick-desktop gconfd (mick-8256): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 28 18:28:23 mick-desktop gconfd (mick-8256): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 28 18:49:07 mick-desktop -- MARK --
Jul 28 19:09:07 mick-desktop -- MARK --
Jul 28 19:29:08 mick-desktop -- MARK --
Jul 28 19:49:08 mick-desktop -- MARK --
Jul 28 20:09:09 mick-desktop -- MARK --
Jul 28 20:29:10 mick-desktop -- MARK --
Jul 28 20:49:10 mick-desktop -- MARK --
Jul 28 21:00:40 mick-desktop kernel: [10340.246472] SCSI device sda: 1950720 512-byte hdwr sectors (999 MB)
Jul 28 21:00:40 mick-desktop kernel: [10340.256439] sda: Write Protect is off
Jul 28 21:00:40 mick-desktop kernel: [10340.266617] SCSI device sda: 1950720 512-byte hdwr sectors (999 MB)
Jul 28 21:00:40 mick-desktop kernel: [10340.276380] sda: Write Protect is off
Jul 28 21:00:40 mick-desktop kernel: [10340.276514]  sda: sda1

---

### Post by Pragmatist on 2007-07-28
Great!  The device file is **/dev/sda1  **Let's make sure it isn't mounted already:
```
mount | grep sda
```If you don't get anything, then do this (if the output shows that something is mounted, post it here):
Make a directory in /media to mount the SD card:
```
sudo mkdir /media/sd
```Mount the SD Card:
```
sudo mount /dev/sda1 /media/sd
```Take a look inside:
```
cd /media/sd
``````
ls -l
```

---

### Post by MickS on 2007-07-28
Thanks Pragmatist for your trouble but before I have a go at that is it worth mentioning that other cards open fine, i don't want to break anything for the sake of one card.

Mick

---

### Post by Pragmatist on 2007-07-28
None of my instructions will cause any damage.  If you don't want to make a directory called /media/sd  then just use any directory that isn't being used.  Convention is to mount devices in directories within the /media directory and give those directories meaningful names.  You could also make the /media/sd directory and just remove it later if you decide you don't want, or need it.  The commands to mount the card are completely harmless--they either will or will not work, but it won't make any lasting change to your system or the card.

You say other cards work.  Are they the same format (i.e. are they also SD cards)? Are you reading them with the same reader?

I suggest following my instructions since, whether it works or not, we will learn something useful.

---

### Post by MickS on 2007-07-28
Here is what I did and nothing seemed to happen, the other cards are the same ie SD and the reader is the same.

mick@mick-desktop:~$ mount | grep sda
/dev/sda1 on /media/CANON_DC type vfat (rw,nosuid,nodev,noatime,uid=1000,utf8,shortname=lower)
mick@mick-desktop:~$ sudo mkdir /media/sd
Password:
mick@mick-desktop:~$ sudo mkdir /media/sd
mkdir: cannot create directory `/media/sd': File exists
mick@mick-desktop:~$ sudo mount /dev/sda1 /media/sd
mick@mick-desktop:~$ cd /media/sd
mick@mick-desktop:/media/sd$
mick@mick-desktop:/media/sd$ ls -l


Have I done that right?

Mick

---

### Post by Pragmatist on 2007-07-28
> **MickS said:**
> Here is what I did and nothing seemed to happen, the other cards are the same ie SD and the reader is the same.

mick@mick-desktop:~$ mount | grep sda
/dev/sda1 on /media/CANON_DC type vfat (rw,nosuid,nodev,noatime,uid=1000,utf8,shortname=lower)

It is already mounted! Try this:
```
cd /media/CANON_DC
```
```
ls -l
```

---

### Post by MickS on 2007-07-28
Did this:-

mick@mick-desktop:~$ cd /media/CANON_DC
mick@mick-desktop:/media/CANON_DC$ ls -l

And again nothing happened, I suspect the card is damaged.

Mick

---

### Post by Pragmatist on 2007-07-28
> **MickS said:**
> ....I suspect the card is damaged.

That is always a possibility.  If it were me, and I wanted to get the information off that card, I would work on the assumption that the card is NOT damaged, at least until I was proven wrong.  So far, I don't see any proof that the card is damaged.  Konquerer not finding the card is not proof that the card is damaged.  Linux mounts the card, so it can't be completely damaged or it wouldn't be able to read it at all.

Is this card from a camera?  Can you view the images on the card using the camera?  Can you read and view the card using another OS, like windows, or a LiveCD?

I have had cards in the past that seemed damaged, but really only needed a filesystem change or a new partition.  Anyway, like I said, if it were me, I wouldn't give up yet.

---

### Post by MickS on 2007-07-28
The card is from a camera, Canon S3 and I can't view images on the camera either, I have checked the camera with another card and it works fine both in the camera and with Konquerer so the problem is just the one card, I  haven't tried it in Windows because I don't want to admit defeat so where do we go from here?
BTW the images on the card are not important so it's not a great loss but it would be nice if I could get them back so I would know what to do if the same thing happened with something more important.
Thanks for your time so far.

Mick

---

### Post by Pragmatist on 2007-07-28
> **MickS said:**
> ....I  haven't tried it in Windows because I don't want to admit defeat....

I don't agree with this statement.  You would be using windows to troubleshoot a problem.  If the problem has to do with the card being incorrectly formatted or partitioned, then it is useful to see if Windows recognizes it.  Whatever the problem is, we can fix it with Linux, but in this case Windows can help in figuring out what the problem really is.

I have used Linux for 5 years and have used it as my main OS for the last 3 years.  Even so, I still turn to Windows if that is the best tool for the job (granted, I only boot Windows about twice-a-year, but I would use it more if the situation called for it).

---

### Post by MickS on 2007-07-28
Please don't get me wrong I'm not into bashing windows but the truth is while I'm here I am also perusing 2 other forums and posting replies so I don't want to shut down and reboot into windows, that would be a pain right now.
Come to think of it I probable have some software in my XP  partition which would do it, haven't been there for ages and can't remember for sure. I don't want to use windows if I can avoid it because I get a real kick out of doing things in Ubuntu and hate the thought that there is still things I need windows for, I want to get rid of windows eventually just to release disc space for Ubuntu.

Mick

---

### Post by Pragmatist on 2007-07-28
Let's have a look at the card's partition table:
```
sudo fdisk /dev/sda
```

Now print the table (lowercase P):
```
p
```

Now exit (lowercase Q):
```
q
```

Post the table here.

---

### Post by az on 2007-07-28
See here:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


Use gnu ddrescue to make an image of the card onto your harddrive.  Then, use formost or photorec to pull the files off of the image.

---

### Post by MickS on 2007-07-29
The table that I get is:-

The number of cylinders for this disk is set to 1912.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 998 MB, 998768640 bytes
20 heads, 51 sectors/track, 1912 cylinders
Units = cylinders of 1020 * 512 = 522240 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1913      975295+   6  FAT16

That number 1913 seems a bit odd to me, the card is a 1gb.
I'm off to have a look at the other thing now but thanks for your help so far Pragmatist, it's been fun messing about in the terminal and I can see why old hands at Linux like it.

Mick

---

### Post by az on 2007-07-29
> **MickS said:**
> 
That number 1913 seems a bit odd to me, the card is a 1gb.


That is actually irrelevant since it has no heads, no sectors and no cylinders.  You can't apply how a hard disk works to a memory card + memory card reader.

---

### Post by MickS on 2007-07-29
I've got Photorec running right now only another 14 and a half hours to go.

Mick

---

### Post by MickS on 2007-07-30
Grand result...nothing. I wonder what to do now, reformat it?

Mick

---

### Post by Pragmatist on 2007-07-30
> **MickS said:**
> The table that I get is:-

Disk /dev/sda: **998 MB**, 998768640 bytes
20 heads, 51 sectors/track, 1912 cylinders
Units = cylinders of 1020 * 512 = 522240 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1913      975295+   6  FAT16
Mick

Notice that fdisk returned the correct size for the card.  Before reformatting, let's see the disk usage:
```
df -h /dev/sda1
```

---

### Post by MickS on 2007-07-30
That code gives me

mick@mick-desktop:~$ df -h /dev/sda1
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             953M   65M  888M   7% /media/CANON_DC



Is that telling us that 65mb or 7% of the card has been used? I don't know whether it's relevant or not but the last time I used the card it was in my camera trying to take photos or a flying bird and I managed to point the camera too close to the sun, some sort of safety device seemed to trigger and shut the camera down, do you think that could have corrupted the card, seems likely to me.
Thanks.

Mick

---

### Post by leong on 2007-07-30
:popcorn:try "test disk " just install from Synaptic, i was lost a file before and use this app recovered , but is in text mode . 

good luck !

---

### Post by MickS on 2007-07-30
> **leong said:**
> :popcorn:try "test disk " just install from Synaptic, i was lost a file before and use this app recovered , but is in text mode . 

good luck !

I'll have a look at that sometime but for the moment I'm sticking with Pragmatist instructions because I'm learning a lot on the way. Thanks for your input.

Mick

---

### Post by Pragmatist on 2007-07-30
Does 65 MB sound right to you?  Look at a typical file size of other pictures you've taken, divide into 65, and see how many pictures are likely to be on the card.  Did you take approximately that many pictures?

Meanwhile, please post the output of this command:
```
mount
```

---

### Post by az on 2007-07-30
> **MickS said:**
> Grand result...nothing. I wonder what to do now, reformat it?

Mick

Did you make an image of the card?  That copies the data on the raw device to a file.

On a one-gig image, photorec should take about five minutes to run.  If you ran in straight on the deivce, then I would suggest that you make an image of the device before you try to reformat it and use it again - that would also explain why it found nothing.  If the drive is inconsistent, then you are unable to use the drive (card, device, whatever) directly.  ddrescue will build an image of the data there that any other data recovery software will be able to use.  

As for what happened to the card, well it's not clear yet whether this is a filesystem corruption or if the device is physically damaged.

---

### Post by MickS on 2007-07-31
> **Pragmatist said:**
> Does 65 MB sound right to you?  Look at a typical file size of other pictures you've taken, divide into 65, and see how many pictures are likely to be on the card.  Did you take approximately that many pictures?

Meanwhile, please post the output of this command:
```
mount
```

Doing that gives me:-
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/CANON_DC type vfat (rw,nosuid,nodev,noatime,uid=1000,utf8,shortname=lower)


My photo file size is about 2mb so I might have took 30 odd pictures but I wouldn't have thought so.

az, I am not sure what I did but it was obviously wrong, please don't think me rude if I stick with Pragmatists instructions only I think they are teaching me a lot, thanks for your input though.

Mick

---

### Post by Pragmatist on 2007-07-31
Please post your **/etc/fstab**

---

### Post by MickS on 2007-07-31
Sorry to be a pain but how do I do that?

Mick

---

### Post by MickS on 2007-07-31
Think I've got it:-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=e4f082ed-fb09-41d1-8531-a70aa87aedc9 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=82998935-08a0-4e92-b507-ac12fda92f56 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0


Mick

---

### Post by Pragmatist on 2007-07-31
When you typed "mount", this was the line for your card:
[B]
/dev/sda1 on /media/CANON_DC type vfat (rw,nosuid,nodev,noatime,uid=1000,utf8,shortname=l  ower)[/B]

To understand the options in between the ( ), read the man page for mount:
```
man mount
```

What I would like to do, is put an entry in your fstab, after backing it up of course, with a small number of options and see if that changes anything.

First, we back up your /etc/fstab:
```
sudo   cp /etc/fstab   /etc/fstab.backup
```

Now open /etc/fstab in an editor (use sudo for a console-based editor or gksudo for a GUI application) and add this line at the end:
> 
/dev/sda1 /media/CANON_DC vfat defaults,errors=remount-ro 0 1


unmount the card:
```
sudo umount /media/CANON_DC
```

mount the card:
```
sudo mount /dev/sda1 /media/CANON_DC
```

See the result of mounting (post the results of this so we can see it):
```
mount
```

---

### Post by MickS on 2007-07-31
Hope I have done it right.

mick@mick-desktop:~$ sudo umount /media/CANON_DC
mick@mick-desktop:~$ sudo mount /dev/sda1 /media/CANON_DC
mount: mount point /media/CANON_DC does not exist
mick@mick-desktop:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
mick@mick-desktop:~$


Mick

---

### Post by Pragmatist on 2007-07-31
Sorry about that, I forgot I already had you make a directory called "sd" in /media

Follow the same instructions, but replace **CANON_DC **with[B] sd

[/B]In **/etc/fstab** change this:
			 				/dev/sda1 /media/**CANON_DC** vfat defaults,errors=remount-ro 0 1 			 		 	 	 

To this:
			 				/dev/sda1 /media/**sd** vfat defaults,errors=remount-ro 0 1 			 		 	 	

Run the mount commands with **sd **instead of[B] CANON_DC
[/B]

---

### Post by MickS on 2007-07-31
Another go gives:-

/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/sd type vfat (rw)

Should I re edit fstab and get rid of that line?

Mick

---

### Post by Pragmatist on 2007-07-31
> **MickS said:**
> Another go gives:-

/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
[B] /dev/sda1 on /media/sd type vfat (rw)
[/B] 
Should I re edit fstab and get rid of that line?

Mick
The line in bold is what I wanted.  Can you see any files now?

```
cd /media/sd
```
```
ls -l
```

---

### Post by MickS on 2007-07-31
I just did :-

mick@mick-desktop:~$ cd /media/sd
mick@mick-desktop:/media/sd$ ls -l
  

And nothing happened. Thanks so far but I'm off to bed now and will look in tomorrow hopefully.

Mick

---

### Post by Pragmatist on 2007-07-31
> **MickS said:**
> I just did :-

mick@mick-desktop:~$ cd /media/sd
mick@mick-desktop:/media/sd$ ls -l
  
And nothing happened....
Mick

All of my above suggestions were basic troubleshooting techniques.  If it was my card, I wouldn't give up yet--if only for the challenge.  Whatever else can be done will require research.  I would be happy to spend some time doing that research on two conditions:

1.) Before we start the research, you at least try to read the card in Windows.

2.) You are also willing to do research and we will compare notes.

Beyond that, there is not much else I can do.

---

### Post by MickS on 2007-08-01
I shall be a bit clogged up with things for a few days so wont have a lot of time to spare but I haven't given up. If I get some sort of result I shall post back here.
Thanks.

Mick

---

### Post by MickS on 2007-08-02
I booted into windows this morning and had a go at that card and it was nothing doing. While I had windows running I downloaded a program Art Plus photorec which is highly recommended on another forum I inhabit, I ran that and it managed to retrieve a few images but only old stuff which was on the card from a previous occasion.Of the few new images they would show up as thumbs in windows fax viewer but wouldn't open properly. I tried to open them separately with the Gimp but that wouldn't do it either, just got an error report saying there were extraneous bytes on the image file.
The thumb nail views were enough to see that the images are not worth worrying about other than as an academic exercise.
What I would like to find out is whether the card has developed a fault or whether the emergency shutdown the camera performed corrupted the card.

Thanks for your time.

Mick

---

### Post by az on 2007-08-02
> **MickS said:**
> While I had windows running I downloaded a program Art Plus photorec

That's just the windows version of Photorec.  I would still recommend running it on a properly made image instead of on the raw device.


> **MickS said:**
> 
What I would like to find out is whether the card has developed a fault or whether the emergency shutdown the camera performed corrupted the card.

Thanks for your time.

Mick

Use the badblocks program.

If your card appears as /dev/sda, do this:

sudo badblocks -s -w /dev/sda 

The -w option will make badblocks run a write test which will erase any data on the card you would be able to recover.

There is no question that the filesystem is corrupt, but whether it is physically damaged (which causes the filesystem corruption) or just logically damaged (the filesystem coruption is the only problem) is what you want to know.  If badblocks does not show anything, reformat the card and try to use it.

---

### Post by MickS on 2007-08-02
I tried that badblocks thing but it was taking to long so I closed it because I needed the reader for something else and now it doesn't work, any ideas how to get it working again, thanks 

Mick

---

### Post by Pragmatist on 2007-08-02
> **MickS said:**
> 
The thumb nail views were enough to see that t**he images are not worth worrying about other than as an academic exercise.**
What I would like to find out is whether the card has developed a fault or whether the emergency shutdown the camera performed corrupted the card.
Mick
Does this mean you want to continue this as an "academic exercise", or do you want to get the card working?

I'm happy to help get the card working.  First you need to put a new filesystem/format the card:

See post #12 of the following thread:
[http://ubuntuforums.org/showthread.php?p=717877](http://ubuntuforums.org/showthread.php?p=717877)

---

### Post by Pragmatist on 2007-08-02
The key steps for a clean card formatted as vfat are:

1.) Make sure you know the device file for the card (is it /dev/sda1 ?)

2.) Use fdisk or cfdisk or gparted or some other partitioning program, to:
  (a)  Delete all partitions on the card 
  (b) Make a new partition on the card.

3.) Put a file system on the new partition using a variant of mkfs
You can read about mkfs by typing:
```
man mkfs
```
You can see other man pages for the different variants of mkfs:
```
man -k mkfs
```

---

### Post by MickS on 2007-08-02
Sorry Pragmatist I seem to have jumped the gun a bit, see further back up the thread my problem now is the card reader doesn't seem to work any more, running the badblocks thing and interrupting it seems to have broke it, how do I get that working again?

Mick

---

### Post by Pragmatist on 2007-08-02
> **MickS said:**
> ....the card reader doesn't seem to work any more, running the badblocks thing and interrupting it seems to have broke it....

I sincerely doubt that the card broke the reader; maybe the reader broke the card, but not the other way around.  I don't know anybody who has broken any media drive (floppy, CD, DVD, LS-120, Zip, or media card drives) by inserting a bad card/disk.

If you really want to be sure, here is what you can do:

1.) Use a LiveCD and see if the drive works there.
2.) Use another installed OS (like Windows)
3.) Physically move the drive to another computer and see if it works there.

4.) Use a card that is known to work on another media drive (I suppose it is possible, if your media drive is shot, for it to damage a working card.  I don't know that for a fact, and I wouldn't be worried--but you probably shouldn't do it if you are worried.  As you can see, however, there are many other tests you can do, that involve little or no risk.)

5.) Use a different media reader on the same system with the same card
5.a.) Use a different media reader on the same system with a different card

I would try step 2 first.  Then, I would try step 5., then 5.a.  Then the other steps if necessary.  I am not recommending YOU do this, but I would buy a USB media reader, and return it if it doesn't solve my problem (I doubt you can do that with a card, but with a reader I don't see why not.  Ask for the store's return policy).  On the other hand, there is a good chance I would keep it as they aren't expensive.  I currently have an internal usb media drive, which came with the computer, and an external one that I bought seperately--it didn't cost much.

Those are my recommendations.

---

### Post by MickS on 2007-08-02
Just booted into windows and the card reader and card work fine, obviously I have upset something but what I don't know, should I start another thread?

Mick

---

### Post by Pragmatist on 2007-08-02
> **MickS said:**
> Just booted into windows and the card reader and card work fine, obviously I have upset something but what I don't know, should I start another thread?

Mick

If you want.  I'm not sure how you would describe your problem! :)  It makes no sense at all that the card should work in windows now, but it didn't work before.  A couple of posts ago you said:
> **MickS said:**
> I booted into windows this morning and had a go at that card and it was nothing doing. While I had windows running I downloaded a program Art Plus photorec which is highly recommended on another forum I inhabit, I ran that and it managed to retrieve a few images but only old stuff which was on the card from a previous occasion.Of the few new images they would show up as thumbs in windows fax viewer but wouldn't open properly.

1.) If the card works anywhere, the card is not physically damaged.
2.) If the reader works anywhere, the reader is not physically damaged.
3.) If they both work fine in windows, then it is strictly something with your Linux system.  First you want to determine if linux is having a problem with just the card, the reader, or both.  

(a.) You should find the make and model of your media drive and see if Linux  supports it.  If Linux doesn't have good support for the drive then that could be the problem.

(b) If the drive works well in Linux, you should try experiments with a card that is known to work.  If you can, buy a new SD card and start using it in Linux (not in windows).  If Ubuntu doesn't recognize the new card, try a LiveCD like Knoppix.


If the drive works well in Linux, and a new card works fine, with that drive, in Linux, then the problem is your current card.  In that case, follow my instructions, in my earlier post, for starting from scratch on the current card (remove old partitions, add new partition, create new filesystem on new partition).

I am sorry, but that is all the advice I can give.  Let me know the results of any of the above.

---

### Post by MickS on 2007-08-02
Sorry I am doing a lot of apologising aren't I.:)
What I meant was, the card reader seems up the creek in Ubuntu, I tried windows with a different card which I know is OK and that card and the reader are fine in windows so no problem with the hard ware, before I ran that badblocks thing, everything except that one bad card worked fine in Ubuntu. Hope that hasn't confused you even more.
I am more concerned about the card reader not working than I am about that one dodgy card.

Mick

---

### Post by Pragmatist on 2007-08-02
> **MickS said:**
> Sorry I am doing a lot of apologising aren't I.:)
What I meant was, the card reader seems up the creek in Ubuntu, I tried windows with a different card which I know is OK and that card and the reader are fine in windows so no problem with the hard ware, before I ran that badblocks thing, everything except that one bad card worked fine in Ubuntu. Hope that hasn't confused you even more.
I am more concerned about the card reader not working than I am about that one dodgy card.

Mick
Ok, so we know that the drive is fine, so forget about the whole "bad blocks" thing.  It is irrelevant.  Try a LiveCD like Knoppix and see if you can read the good card with the drive.

---

### Post by az on 2007-08-03
> **MickS said:**
> I tried that badblocks thing but it was taking to long so I closed it because I needed the reader for something else and now it doesn't work, any ideas how to get it working again, thanks 

Mick

It would be helpful if you post the output of things like that.  I have no idea what you did or how you did it.  Checking a 1 gig memory card should take less than five minutes.  Were errors shown?  What was the progress?  How fast was it progressing, etc...

EDIT:  Did not see the second page of the thread...

If the card did not work, but others did, then badblocks is relevant to know whether it is a logical problem or a physical one.  If the card works perfectly in windows, then it is a linux driver issue instead.  Now, are you absolutely sure that some cards work fine in linux and just this one doesn't?  And as well, this card woks in windows?  That's unusual.  Usually a driver problem is specific to the card reader, and not the media inside it.  The media is abstracted by the card reader to the linux kernel.

---

### Post by MickS on 2007-08-03
Card reader is sorted, all I had to do was put my fstab back to what it was originally, as for the corrupt card I am going to leave that alone for now.
Thanks for trying to help guys.

Mick

---

