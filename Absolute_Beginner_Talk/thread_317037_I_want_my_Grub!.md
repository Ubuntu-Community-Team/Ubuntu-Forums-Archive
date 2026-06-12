---
title: "I want my Grub!"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by say592 on 2006-12-11
Ok, I installed ubuntu (edgey) on my 20gb slave drive, I did this when windows had a virus, mainly to back up my info, but also to give linux a try. I love linux! However other members of my house dont understand firefox, let alone linux. When XP had its virus, grub picked it up and had it added, but now that I formated my master (the windows drive) and reinstalled xp it doesnt pick it up! How do I get it to even start, because its not so much of an issue of gruuby not picking it up, its that it doesnt even start! I mainly want grubby back and ubuntu so that my family can use their xp, and i can have ubuntu. Now what do I do!

---

### Post by bodhi.zazen on 2006-12-11
> **say592 said:**
> Ok, I installed ubuntu (edgey) on my 20gb slave drive, I did this when windows had a virus, mainly to back up my info, but also to give linux a try. I love linux! However other members of my house dont understand firefox, let alone linux. When XP had its virus, grub picked it up and had it added, but now that I formated my master (the windows drive) and reinstalled xp it doesnt pick it up! How do I get it to even start, because its not so much of an issue of gruuby not picking it up, its that it doesnt even start! I mainly want grubby back and ubuntu so that my family can use their xp, and i can have ubuntu. Now what do I do!

LOL

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

boot to the desktop (live Cd)

What is your ubuntu root partition ?

I presume /dev/hda2

Now, open a terminal
Type:```
sudo gurb
```

You will get a grub prompt:
grub >

Enter:```
root (hd0,1)
setup (hd0)
quit
```

Reboot and all should be goo in life.

(If you do not know your ubutnu root partition look at /boot/grub/menu.lst in your ubuntu root partition)

---

### Post by Sef on 2006-12-11
Windows does not see any OS except its own.   That's why you need to restore GRUB.

---

### Post by say592 on 2006-12-11
Wait, on the live cd? Then I cant see my partition..... Its a single partition on my 20gb slave its just ubuntu on there..........

---

### Post by bodhi.zazen on 2006-12-11
> **say592 said:**
> Wait, on the live cd? Then I cant see my partition..... Its a single partition on my 20gb slave its just ubuntu on there..........

LOL

Boot the live CD

In a terminal:```
sudo mkdir /media/ubuntu
sudo mount /dev/hdb1 /media/ubuntu
sudo grub
```Substitute sdb1 for hdb1 if needed....

If you are not sure, in a terminal type:```
sudo fdisk -l
```

At the grub prompt:```
root (hd1,0)
setup (hd0)
quit
```

Re-boot.

---

### Post by say592 on 2006-12-11
Total n00b here so I would go to hdd1 if this is how it looks for that 20gb drive:

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2330    18715693+  83  Linux
/dev/hdd2            2331        2434      835380    5  Extended
/dev/hdd5            2331        2434      835348+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by gn2 on 2006-12-11
Have you read this: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by say592 on 2006-12-11
I dont get it :(

---

### Post by bodhi.zazen on 2006-12-11
> **say592 said:**
> Total n00b here so I would go to hdd1 if this is how it looks for that 20gb drive:

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2330    18715693+  83  Linux
/dev/hdd2            2331        2434      835380    5  Extended
/dev/hdd5            2331        2434      835348+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

```
sudo mkdir /media/ubuntu
sudo mount /dev/hdd1 /media/ubuntu
sudo grub

root (hd3,0)
setup (hd0)
quit
```

reboot

---

### Post by gn2 on 2006-12-11
To simplify: Windows on the master hard drive with it's own bootloader, and Ubuntu on the slave hard drive with Grub.

Achieved by installing Ubuntu with Windows drive disconnected.

Select which drive to boot using "Boot Device Selection Menu" which comes up when you press F8 (or other key depending on BIOS type)

---

### Post by say592 on 2006-12-11
> **gn2 said:**
> To simplify: Windows on the master hard drive with it's own bootloader, and Ubuntu on the slave hard drive with Grub.

Achieved by installing Ubuntu with Windows drive disconnected.

Select which drive to boot using "Boot Device Selection Menu" which comes up when you press F8 (or other key depending on BIOS type)
whats the benefit or diff. doing it this way compared to the other guys.....

---

### Post by say592 on 2006-12-11
Oh, and what would be better if I plan to add a third windows os (ok its the second windows os, but the 3rd in general, any way vista, i plan to add vista)

---

### Post by say592 on 2006-12-11
Ok, so when I tried to do the code that was posted (the one that went into grub) this is what I got:

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd3,0)

Error 21: Selected disk does not exist

grub> root (hdc2,0)

Error 23: Error while parsing number

grub> 



And when I do sudo fdisk -l this is what I get:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5816    46716988+   b  W95 FAT32

Disk /dev/hdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1           5       40131   de  Dell Utility
/dev/hdc2   *           6        9300    74662087+   7  HPFS/NTFS
/dev/hdc3            9301        9725     3413812+  db  CP/M / CTOS / ...

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2330    18715693+  83  Linux
/dev/hdd2            2331        2434      835380    5  Extended
/dev/hdd5            2331        2434      835348+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
   I want to use the XP drive (80gb) and my ubuntu drive (20gb)

---

### Post by dolphinsonar on 2006-12-11
Second.
\
> **say592 said:**
> Oh, and what would be better if I plan to add a third windows os (ok its the second windows os, but the 3rd in general, any way vista, i plan to add vista)

---

### Post by confused57 on 2006-12-11
You might want to consider this option:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

It'd probably be easier just to reinstall Ubuntu, but connected as the master drive...then add the entry to boot Windows on your slave drive, as described in the above link.

---

### Post by bodhi.zazen on 2006-12-12
> **say592 said:**
> Ok, so when I tried to do the code that was posted (the one that went into grub) this is what I got:

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd3,0)

Error 21: Selected disk does not exist

grub> root (hdc2,0)

Error 23: Error while parsing number

grub> 



That is it.

All we need to do now is find your Ubuntu root partition.

At the grub prompt type:```
find /boot/grub/stage1
```

This should return your root partition, something like:> (hd0,0)I'll call this (hdx,y) since I do not know the numbers.....

Enter that root (hdx,y)

```
root (hdx,y)
setup (hd0)
quit
```

Reboot

---

### Post by gn2 on 2006-12-12
> **say592 said:**
> whats the benefit or diff. doing it this way compared to the other guys.....

Reduced Grub hassles, and a clean MBR on the Windows drive.

The method I suggest means that you will always have Windows available to boot from, independent of Grub, which can need editing from time to time.....

It is not unknown for Grub to cause booting difficulties.

---

### Post by kohl62 on 2006-12-12
I found using the "Super Grub Disk" the easiest way to restore Grub after having to reinstall windows.  I just did a search for "Super Grub Disk", downloaded the iso image and burnt it as an ISO to a disk, and booted it up.  It did all the work of restoring Grub!  Worked like a charm.

Might give it a try.

---

### Post by say592 on 2006-12-12
> **kohl62 said:**
> I found using the "Super Grub Disk" the easiest way to restore Grub after having to reinstall windows.  I just did a search for "Super Grub Disk", downloaded the iso image and burnt it as an ISO to a disk, and booted it up.  It did all the work of restoring Grub!  Worked like a charm.

Might give it a try.

So, what exactly does this do? Is it like a grub utility? And doing it the second way, that reqires me to reinstall right? I had a hard time mounting hard drives, but i should be able to get it.... Oh and how does it work if windows isnt connected? Do I have to add it? I may try the grub disk thing, then I will go from there........

---

### Post by bulldog on 2006-12-12
Don't disconnect anything you'll be sorry when you do.
If you want GRUB on the second disk just install it with setup (hd1) instead of setup (hd0).

If you're confused,I'll make it worse :-).

Install windows on the first hdd,than go to the BIOS and make the second disk master boot device.
Or switch the cable if you prefere.[windows disk slave,ubuntu disk master]
If done,boot the live cd and follow the steps below,
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr

Now we have to alter menu.lst to make windows boot.
```
gksudo gedit /boot/grub/menu.lst
```
make your windows entry like this [the mapping]
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

Now you can boot windows and ubuntu from GRUB and in case of GRUB failure,you can boot windows from it's own bootloader.

---

### Post by say592 on 2006-12-12
Why? I kinda like the sounds of option 2....... I just dont want to have to reinstall........ That would suck!

Ok I see, but in the BIOS it hasnt yet picked up my 20g! I hate it sometimes........ Its a dell dimension something or another... (it has an intel processor, 512 ram, and an 80gb hdd, cd burner/dvd player no floppy)

---

### Post by bulldog on 2006-12-12
> **say592 said:**
> Why? I kinda like the sounds of option 2....... I just dont want to have to reinstall........ That would suck!

What is option 2,you've lost me :-)

If you have windows and Ubuntu installed already,you won't have to reinstall.

---

### Post by say592 on 2006-12-12
Option 2 was reinstalling it with the xp drive out then adding xp, and again what would be best if i plan to add more os's (i have 150gb+ free space :)) I guess I can add vista and anything else later...... so ya..... What now? I need simple easy to understand! Oh, and about making my 20gb my boot disk, couldnt I just switch it to master? Or if anyone else with a dell have this problem, how did you fix it........

---

### Post by say592 on 2006-12-12
Ok this is my sudo fdisk -l if this helps:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5816    46716988+   b  W95 FAT32

Disk /dev/hdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1           5       40131   de  Dell Utility
/dev/hdc2   *           6        9300    74662087+   7  HPFS/NTFS
/dev/hdc3            9301        9725     3413812+  db  CP/M / CTOS / ...

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2330    18715693+  83  Linux
/dev/hdd2            2331        2434      835380    5  Extended
/dev/hdd5            2331        2434      835348+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by bulldog on 2006-12-12
It's a choice you have to make.
If you want the windows disk out just do so.
If you want to use GRUB it should be on the master boot device.
Sins this is windows in your case, I give you another way of doing things.
I did it in the way I described,and it works very well.

But the decision what to do is entirely yours. :-)

---

### Post by Sqwishy on 2006-12-12
there should be a command line option in grub
then go ...
rootnoverify (hd0,****)
chainloader +1

at the **** part you put the the partition # that windows is in

then at the end type
boot

i think this should work <_< although don't be possitive unless someone else around here agrees
if you boot to windows than that's a temporary fix until you can edit your grub configuration file

---

### Post by bulldog on 2006-12-12
> **say592 said:**
> Option 2 was reinstalling it with the xp drive out then adding xp, and again what would be best if i plan to add more os's (i have 150gb+ free space :)) I guess I can add vista and anything else later...... so ya..... What now? I need simple easy to understand! Oh, and about making my 20gb my boot disk, couldnt I just switch it to master? Or if anyone else with a dell have this problem, how did you fix it........

If you can do so,it's the most easiest way.
Important thing is,ubuntu with the GRUB must be the master,the rest is just altering your menu.lst to place the rest of the OS's you have and will install in the future ,to point to the right disk and partition.

So think about the options you have,I read tomorrow what you're gonna do.

---

### Post by say592 on 2006-12-12
Well I tried to make my ubuntu drive the primary, but when I tried, it did not pick it up! When I went into the bios, it said master hdd not installed! This was a stock dell mobo and processor, maybe it is set to check for windows files, since it was dell (90% custom now, all that is left is the hdd and the mobo/processor)

---

### Post by say592 on 2006-12-12
Well I tried the Super Grub Disk but it did not work.....That or I did something wrong :( But I am getting kind of fed up with this, windows is fine when ubuntu is not primary (bios doesnt pick up the ubuntu drive :() Well what do you suppose I do? I cant have it in primary, and Bios doesnt recognize it as a drive........... Where do I go from here! I am so lost!

---

### Post by confused57 on 2006-12-12
> **say592 said:**
> Well I tried to make my ubuntu drive the primary, but when I tried, it did not pick it up! When I went into the bios, it said master hdd not installed! This was a stock dell mobo and processor, maybe it is set to check for windows files, since it was dell (90% custom now, all that is left is the hdd and the mobo/processor)

Make sure the jumper setting on your Ubuntu drive is correct, i.e. master or slave, depending on how it's connected to your IDE cable(or cable select, if supported.

On my Dell, I have to go into bios and disable the IDE slave drive controller, if I only have the master drive connected...then enable it when both master & slave are connected.

---

### Post by bulldog on 2006-12-13
> **say592 said:**
> Well I tried the Super Grub Disk but it did not work.....That or I did something wrong :( But I am getting kind of fed up with this, windows is fine when ubuntu is not primary (bios doesnt pick up the ubuntu drive :() Well what do you suppose I do? I cant have it in primary, and Bios doesnt recognize it as a drive........... Where do I go from here! I am so lost!

Cool down a little,you want to use a whole new OS,well you have to take some time for it.
If you want to configure your drives with ubuntu disk as master,and with GRUB installed,we have to take a look at the menu.lst,because the settings are wrong now. [they point to the wrong disk]

It's all not as hard as it seems,if you think a little,you can figure out for yourself,what to do and how to accomplish this.
If reversing two drives is to big to handle,maybe you better let it as it is.

---

### Post by say592 on 2006-12-13
Ok, I think I am gonna go through and just reinstall ubuntu..... Whats one weekend's worth of work? Well I wont do that tonight, do if you can eplain things simply, I might be able to do it without reinstalling..... I am just getting frustrated, I have XP back, which is frustrating, because I have about 45gb of data to copy back, and I cant boot....... I just want to get this done soon........... Thanks, if there is an easy solution just post so.... I need complete codes though because I dont have the whole sudo and other commands down (sudo is complete access to all files, right?, oh well for now....)

---

### Post by bulldog on 2006-12-13
If you have the OS's installed you just boot up the live cd so we can have a look at your menu.lst.
If you can boot Ubuntu you can do that instead.

The steps from the beginning,if you did this already,you can skip this of course.
1:Install windows on the master disk.
2:Switch the master disk with the second disk so this will be the master.
3:Install Ubuntu on the new master disk,so GRUB will be here as well.
If you did this in another order,don't mind.
But be sure the disk with GRUB or Ubuntu is the master boot device,this is essential.

Now the only thing we have to do is pointing GRUB to the right partitions,which is done through the menu.lst file.
If you can boot from disk or live cd [ubuntu] give me the outcome of```
sudo fdisk -l(l as in like)
```
Let me know if you use the live cd or the hard disk to boot.
If you use the live cd we have to mount your ubuntu partition.

---

### Post by say592 on 2006-12-13
Live disk, it wont boot (ubuntu, but it is on the master now) My sudo fdisk -l is:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5816    46716988+   b  W95 FAT32
ubuntu@ubuntu:~$ 


I dont know why, but it doesnt pick the ubuntu or windows disk up when ubuntu is master, I am going to see if the jumper is in (it can be out, then the cables rule who is what, right?)

---

### Post by bulldog on 2006-12-13
I see just one disk,where is the other?
Is this the disk with windows??

---

### Post by say592 on 2006-12-13
That is a partitioned disk for storage of both systems.... Like I said it wont pick up the win. or ubuntu drives, i still have to check the jumpers............

---

### Post by say592 on 2006-12-13
There is a jumper tab thing in the windows drive, should I take that and add it into the linux drive? I will if no one says otherwise in 15min (i dont want to have to reboot if not needed, as I am working from this computer)

Oh yeah, I see there is a new theme to the forums, a more ubuntu gnome look (standard)

---

### Post by bulldog on 2006-12-13
I strongly advice you to **not** to mess with your hdd's with a computer which is turned on.

You have to examine the disk there should be an indication how it's set as master as well as slave.
This will be done by setting a jumper according the indication,and to connect it with the motherboard on the first IDE port.

---

### Post by say592 on 2006-12-13
Of course I know not to mess with it while its running! I am not stupid! (but if I were I would thank you so thanks) I guess I will have to reboot in a sec.........

---

### Post by say592 on 2006-12-13
Ok it was the jumpers, I had them screwed (win hdd was set on cable select and on the slave cable, and the ubuntu hdd was on slave on the main hdd) I have it set, and my sudo fdisk -l looks like this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5816    46716988+   b  W95 FAT32

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2330    18715693+  83  Linux
/dev/hdc2            2331        2434      835380    5  Extended
/dev/hdc5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/hdd: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1           5       40131   de  Dell Utility
/dev/hdd2   *           6        9300    74662087+   7  HPFS/NTFS
/dev/hdd3            9301        9725     3413812+  db  CP/M / CTOS / ...
ubuntu@ubuntu:~$ 

Ok so 80gb=windows and 20gb=ubuntu 160gb=fat32 (45gb) and unused (rest)

---

### Post by say592 on 2006-12-13
Ok so I tried the way on page two by bulldog, but I failed, right at the end to! I get this error:

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ gksudo gedit /boot/grub/menu.lst

(gedit:12955): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (gedit:12955): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

** (gedit:12955): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
ubuntu@ubuntu:~$

---

### Post by bulldog on 2006-12-14
Okay all the disk are listed.
From which disk are you booting?
If I know that we can get a look at your menu.lst to set the thing up.

If you're on the live cd we have to mount your ubuntu partition.
```
sudo mkdir /mnt/rescue
```
```
sudo mnt /dev/hdc1 /mnt/rescue
```
```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```

This will open the menu.lst in a text editor so we can have a look at it.

---

### Post by say592 on 2006-12-14
Ok, so I have ubuntu on my 20gb, that is the master, 80gb is win. 160 is partitioned for space, and vista (soon i hope)

And I tried those codes, and got this (oh it brought up that file that I was supposed to add to, the grubb file):

ubuntu@ubuntu:~$ sudo mkdir /mnt/rescue
ubuntu@ubuntu:~$ sudo mnt /dev/hdc1 /mnt/rescue
sudo: mnt: command not found
ubuntu@ubuntu:~$ gksudo gedit /mnt/rescue/boot/grub/menu.lst

(gedit:5571): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (gedit:5571): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
ubuntu@ubuntu:~$

---

### Post by bulldog on 2006-12-14
Sorry my fault,try again with this command```
sudo mount /dev/hdc1 /mnt/rescue
```

Then the code to bring up menu.lst,we have to mount it first,and this failed due to a bad code of mine

---

### Post by say592 on 2006-12-14
Its 153 lines, do you want me to post it?

---

### Post by bulldog on 2006-12-14
Just between code tags please.

---

### Post by say592 on 2006-12-14
I didnt know what you meant, so I just am going to post it all :P

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6f3636bd-4a3c-4a74-a260-fcbe0d8775cb ro
# kopt_2_6=root=/dev/hdd1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by bulldog on 2006-12-14
```
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6f3636bd-4a3c-4a74-a260-fcbe0d8775cb ro
# kopt_2_6=root=/dev/hdd1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc2
title Microsoft Windows XP Home Edition
rootnoverify (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

```

I've altered your menu.lst,if you're certain you boot from the ubuntu disk it should work.
Only windows can be wrong because I don't know how your drives are listed.
But this you can easely change by your self.
If you take a look at the windows entry you see the mapping map (hd0) (hd1),the (hd1) could be (hd2) so if it not works [windows] try this instead.
Also you see (hd1,1) as windows root if you have to change the mapping,you have to make this (hd2,1) too.

If you've got error messages take a good look and write them down,so we can use them if it's not working.

Copy this menu.lst and overwrite your existing,fingers crossed and give it a try.[save it as menu.lst in your /boot/grub folder!!]

---

### Post by say592 on 2006-12-14
Ok, that didnt work (OS error or something like that) How would we find out how my dirrectory or whatever? I am haveing some MAJOR issues with this lol is there a way to repair it? Because when I installed ubuntu and grub with that, windows was the master........Does grub still exist? I had to format the hdd so....... What do yo think? If not, should I just reinstall with ubuntu as master (like with ubuntu as master, and windows as slave) or could this cause issues with windows if grub failed?

---

### Post by bulldog on 2006-12-14
GRUB should be on the ubuntu disk so you should have seen it.
You can reinstall GRUB with the live cd.
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

But you have to be absolutely sure ,you boot from the Ubuntu disk.
If you use another bootdisk,GRUB will be messed up on the wrong disk again.

What about windows? It wouldn't boot either?

I can assure you that,if your computer was in my house,it will be up and running in half an hour.
It is straight forward what I'm telling you,but if I have a look at your fdisk -l ,you boot from another disk, (hdb1) in my opinion.
But if you are absolutely sure it's the hdc which boots,just install GRUB onto it.

**EDIT:**
Take a look at this link for more info about GRUB,
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I think you're in a different time zone because it's half past midnight here and I have to get some sleep.
Be back tomorrow if it's not running.

You can also have a look at the Super GRUb disk,which can boot almost anything,

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by say592 on 2006-12-14
It gave a general error, I only have one set of jumpers, so I couldnt switch to the windows drive (in slave) and see, so with this reinstalled, and all we have done, it should be fine? At least I hope so! I am gonna reboot, keep watching as it will only take 2min or so to find out if it worked......

---

### Post by say592 on 2006-12-14
OK I hate this, NOTHING boots, I even reinstalled ubuntu and grub! I cant boot windows either! I think I may just format, and be done, all in windows, and let it be for a while, i may come back to you all! I still want help, as i wont format all till that is my last option! (i need to download this file for my work this weekend, its 4gb and I need to burn it to a dvd so I might have to if worst comes)

---

### Post by bulldog on 2006-12-15
To get your windows back you won't have to format!!
Just boot from the windows install cd ,let it run till you get three options.
1:Install windows
2:Repair a Windows install
3:Exit.
Choose the second option which brings you to a console where your install is listed.
Login with you administrator password and do fixboot and fixmbr.
You will be warned but just ignore that,it goes well in most cases.
Exit the windows cd and you can boot from this disk and use your windows.

The reason you can't boot anything,is your hard disk aren't set properly.
If you do a fdisk -l the drives are listed in the order as ubuntu see them.
In your case you said the 20GB was master but it was not listed as the master,but hdb was.
If I set GRUB menu.lst up with the 20GB as the master,but it isn't,than you can't boot anything.
It all depends on each other,if one thing isn't done right,it won't boot.
So think deeply what you want to do,but if I ask which one is master,be honest and don't do a wild guess.
If you don't know which one is master say so,I can see for myself what to do.
It makes no difference on which drive GRUB is installed,it should be convenient if it was on the Ubuntu disk.
So if you boot from another disk,all I have to do is altering the menu.lst so GRUB points to the right direction.
But if you just guess which disk you boot from and tell me the wrong disk,I can do what I want,but it will never boot.
So if you want to go through with this,**IT'S ESSENTIAL THAT I KNOW WHICH DISK YOU BOOT FROM,OTHERWISE I CAN'T SET THE MENU.LST PROPER**

---

### Post by gn2 on 2006-12-15
Follow Bulldog's advice and repair the damage Ubuntu has done to your Windows MBR, then try this: 


1: Windows on master (far end) connector with jumper set to master.

2: Power connector disconnected from Windows drive.

3: Ubuntu Hard drive on slave (middle) connector with jumper set to slave.

4: Install Ubuntu and grub.

5: Switch off.

6: Re-start and enter BIOS.

7: Select preferred default OS by putting it first in BIOS Boot Order list.

8: Exit BIOS and default OS will start.

9: When you want to re-boot with other OS, press F8 (or whatever key depending on PC model) and select the other hard drive.

Simple really. [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by bulldog on 2006-12-15
Yes gn2,it should be simple,but we're talking about three hdd's  and some how I can't get the right information,to set up GRUB.
Did this so many times,it isn't difficult,but you need to have the right information.

---

### Post by gn2 on 2006-12-15
Three drives 1 Windows, 2 Ubuntu, 3, Data ?

Or 1 Ubuntu with Windows as a VMWare Guest, and 2&3 as Data...

I know which I'd go for!

---

### Post by say592 on 2006-12-15
Ok, so here is the complete set up, I have 2 hdd/cd plugins on my mother board, One is disk drive master, 160gb(data/partition for vista) slave........ Then, we have the other set, which is master=20gb(ubuntu) and slave=80gb(win XP) I know the win xp drive has a dell utility partion, which on my friends dual boot linux system (he is about as much as a n00b as me, and he doesnt have ubuntu) any ways, it caused some issues.........

So again it is:

Port 1: 
Dvd drive (master, on master cable)
160gb hdd (slave, set to cable select on slave cables)

Port 2:
20gb (master, set to cable select, and on master cables)
80gb (slave, no jumpers ((slave on this one is no jumper)), on slave cable)

I can get pics if you want, but that could be a while, I just want to be able to have it all work......

Vista is of course not installed (i dont have it DUH)

---

### Post by say592 on 2006-12-15
Oh, and my bios only lets you boot from master HDD or disk drive :(

---

### Post by bulldog on 2006-12-15
> **say592 said:**
> Ok, so here is the complete set up, I have 2 hdd/cd plugins on my mother board, One is disk drive master, 160gb(data/partition for vista) slave........ Then, we have the other set, which is master=20gb(ubuntu) and slave=80gb(win XP) I know the win xp drive has a dell utility partion, which on my friends dual boot linux system (he is about as much as a n00b as me, and he doesnt have ubuntu) any ways, it caused some issues.........

So again it is:

Port 1: 
Dvd drive (master, on master cable) <-------This is wrong!!!
160gb hdd (slave, set to cable select on slave cables)

Port 2:
20gb (master, set to cable select, and on master cables)<-------this one should be where the dvd drive is!!!!
80gb (slave, no jumpers ((slave on this one is no jumper)), on slave cable)



I did make some notifications for you.
Switch the DVD drive with the 20GB drive and set it to master not cable select!!
As it should be,

Port 1:
20 GB master no cable select just jumper it as master!!and at the end of the cable!
160GB set as slave no cable select may use the middle connector at the cable.

Port 2:
80GB set as master no cable select at the end of the cable.
DVD drive set as slave may use the middle connector.

Make it like this and give me a pm if you want,so we can try it again.

---

### Post by say592 on 2006-12-15
Its all set now, I am sending ya a pm........

---

### Post by say592 on 2006-12-16
Ok, so explain how this was to help, because now I have the 80 and 20 found, but it says i have no cd drive, and i still get an error! I hate this awful cpu (i want to get a new one after christmas, but that wont help here and now)

The error is: "ERROR LOADING OPERATING SYSTEM. CHECK DRIVES AND REBOOT"

---

### Post by bulldog on 2006-12-16
In this setup your hard disk are set with jumpers [cable select often fail]
If your cd rom isn't working yet you can give it a try to switch the hdd and cd rom which are on the same IDE and set cd to master and hdd as slave.
Find it rather strange that you should do this to get the cd player to work.

Okay with a little luck where getting there :D 
Check your BIOS if the 20GB is set as master boot device and were clear to go.
We reinstall GRUB because I don't know on which disk it's installed.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

Please put the outcome of ```
sudo fdisk -l 
``` on the forum.

The next step will be altering your menu.lst,but if you copied the one I made some time ago,most should be set up,maybe I have to change some little thing,but we'll see.

If the menu.lst is in order the next step is to take a look at your fstab to see how things are listed in there.[mostly for mounting,but I want to see if your ubuntu install is listed]
If we accomplished this three steps it's time to reboot.

So I wait till I get the fdisk outcome.

Things to consider.
A new computer will have the same issues if things are messed up.
A computer uses your hardware according the setup which you made or buy.
There are some rules to obey otherwise it wont work out of the box.
To use your hardware you use an OS like windows or ubuntu.
If you install an OS it makes a configuration file from your hardware in order to use it,but if you change your hardware after the install,your heading for trouble.
Windows is pretty neat in catching this changes and how to deal with it,ubuntu don't like this at all,and will refuse to boot.
This will not mean you have to reinstall ubuntu,but you have to tell it which changes you made,this is done in menu.lst and fstab in your case,but there are more configuration
files in ubuntu,think about the xorg.conf.
If you did tell ubuntu what's changed it will adept and boot normally in most cases.

If you get the cd-player to work,you can be creative in this,but be sure you jumper it accordingly the place you put it,so master,jumper it as master and slave,jumper it as slave.
Also keep an eye on the place you connect it with the flat cable,but you know this already.
You can consider a reinstall of ubuntu if you have the time,it should be quicker as reconfiguring your config files trough out the forum.
But after you did the reinstall and in case it shouldn't work,don't go messing with anything,because if you do we're at squire one again.

Don't touch windows and don't reinstall it,it should be working as it is.
We only have to tell GRUB where it is and do some hard disk mapping to fool windows.

---

### Post by say592 on 2006-12-16
Ok, I am going to work on it now! I hope this all works! I will have the sudo fdisk -l in a bit I hope!

---

### Post by say592 on 2006-12-16
Ok, while we are in messing with hardware, my mobo has a video port (much like many others) but I also have another vid card that I want to drop in at some point, would now be the time?

---

### Post by bulldog on 2006-12-16
Shouldn't do that now,it depends on the card however,but changes are X-server will crash during boot.

---

### Post by say592 on 2006-12-16
Ok, primary master=20gb primary slave-160gb secondary master=cdrom secondary slave=80gb

Ok and I didnt put in the vid card

---

### Post by bulldog on 2006-12-16
Nice :D  did you reinstall GRUB yet as I suggest in my previous post?
And I would like to have the outcome of fdisk -l please.

---

### Post by say592 on 2006-12-16
Ok, I just got onto the ubuntu live cd, i am about to run the scripts now so hang for a sec!

---

### Post by say592 on 2006-12-16
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5816    46716988+   b  W95 FAT32

Disk /dev/hdd: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1           5       40131   de  Dell Utility
/dev/hdd2   *           6        9300    74662087+   7  HPFS/NTFS
/dev/hdd3            9301        9725     3413812+  db  CP/M / CTOS / ...
ubuntu@ubuntu:~$ 


I couldnt figure out how to make it code so it wouldnt take 1/2 page on here, but oh well here it is!

---

### Post by bulldog on 2006-12-16
```
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6f3636bd-4a3c-4a74-a260-fcbe0d8775cb ro
# kopt_2_6=root=/dev/hdd1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd2
title Microsoft Windows XP Home Edition
rootnoverify (hd2,1)
map (hd0) (hd2)
map (hd2) (hd0)
savedefault
makeactive
chainloader +1
```

Did you install GRUB to (hd0) yet ?
You need to do all the steps like the find command and put the outcome,probably 
(hd0,0) to the next line and finally setup (hd0) and see if there are no errors.
If done so and no errors we'll go to the next step.

We'll mount your ubuntu again to the rescue folder to access the menu.lst.
```
sudo mount /dev/hda1 /mnt/rescue
```
Copy this menu.lst over the old one.

Now we'll take a look at fstab.
```
sudo cp /etc/fstab /etc/fstab_backup
```
```
gksudo gedit /etc/fstab
```
The first command makes a safety copy and the content of the second command you may put on the forum.

{the code tags are real easy,just open with [code]your text here,and close with the same tag but a /before code like this /code with the hooks around it.}

---

### Post by say592 on 2006-12-16
yes I installed grubb using the instructions you posted, I will give the other codes you posted a run and post the results!

---

### Post by say592 on 2006-12-16
My fstab is:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by bulldog on 2006-12-16
> **say592 said:**
> My fstab is:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
This can't be real,made a mistake again lol
Try this one instead.
```
gksudo gedit /mnt/rescue/etc/fstab
```I'll forgot you have mounted your ubuntu :(

---

### Post by say592 on 2006-12-16
wait so i need to mount it  first right? because that one was blank :\

---

### Post by bulldog on 2006-12-16
Yep the code wasn't set right it's in my previous post70 you can copy paste it.

---

### Post by say592 on 2006-12-16
```
ubuntu@ubuntu:~$ gksudo gedit /mnt/rescue/etc/fstab

(gedit:7759): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ubuntu@ubuntu:~$ sudo mount /dev/hda1 /mnt/rescue
mount: mount point /mnt/rescue does not exist
ubuntu@ubuntu:~$ sudo cp /etc/fstab /etc/fstab_backup
ubuntu@ubuntu:~$ gksudo gedit /etc/fstab

(gedit:8019): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ubuntu@ubuntu:~$ 


```

Ok that is what I coppied from the terminal, i got the same fstab though

---

### Post by bulldog on 2006-12-16
Nope you where using the live cd previous too,so your mount dir is gone.
I'm getting too old for this:D 
Again,
```
sudo mkdir /mnt/rescue
```
```
sudo mount /dev/hda1 /mnt/rescue
```
Now it's mounted.
```
sudo cp /mnt/rescue/etc/fstab /mnt/rescue/etc/fstab_bak
```
Safety copy
```
gksudo gedit /mnt/rescue/etc/fstab
```
This on the forum please

---

### Post by say592 on 2006-12-16
Ok, and thanks, here is the script:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=7334d2a9-fcf7-4a8a-8fdd-91e3ce414ebc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=2bacc5ea-a4b6-4d75-9de6-1397bad7b691 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by bulldog on 2006-12-16
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=7334d2a9-fcf7-4a8a-8fdd-91e3ce414ebc / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=2bacc5ea-a4b6-4d75-9de6-1397bad7b691 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
```
Alter your fstab like this,you only have to change the #/dev/hdc1 into hda1 and#/dev/hdc5 into hda5 and Ubuntu should start.

You can give windows a try too but if it fails it's because it's not listed in your fstab.
I have to go and make your fstab with windows later this night and post it here.
We have to list your other drives too,but it can wait till you're up and running again.

But just try to reboot into ubuntu with GRUB,and let me know if it worked.

---

### Post by say592 on 2006-12-16
So, that should work? Is there a way that we could try for windows now? I have to go to work in a couple hrs, but we may be able to start.............

---

### Post by bulldog on 2006-12-16
Sorry have to go to an appointment so it has to wait till later tonight.
But you can try windows of course,it can work.

**EDIT**
Well no more information?
I was curious if things were working,a pity you haven't post it,now I can't do anything.:-(

---

### Post by say592 on 2006-12-16
Ok, sorry I had to go to work :( Anyways, I did all that you said and grubb comes up! BUT it wont load into ubuntu (os error) and it wont load into windows xp (gets to the screen with the scrolling bar, then after that it goes black! Probly a win xp prob, but I dont know what files to fix, the only one i didnt was the mbr file, can i do that without effecting it?)

---

### Post by bulldog on 2006-12-17
Well at least you have the GRUB menu and that's what you wanted :D 

If windows start to load and after that failed,it has nothing to do with the MBR fix.
This fix is used if GRUB is in the MBR of that particular hard disk and you want to replace it with the windows boot loader.

The exact error you get when you try to boot ubuntu is 'os error'?
Take a look at your mtab as well,if every thing is located as it should be,you can copy it to the forum if you like so I can look at it.
```
cat /etc/mtab
```

I would suggest to reinstall ubuntu in the same partitions,on the same disk.
Just when you come to the partitioner mount the partitions which you already have and format swap as swap and / as ext3 file system and let it reinstall.
It cost only half an hour to do so.
I think it's much more time consuming to find out what the error is and to deal with it.
Grub will be installed at the end on (hd0) and that is where it should be.
If done ubuntu should boot without a glitch.

Don't disconnect any drives so GRUB will recognize all your other partitions and OS's so it will setup fstab just as well.

The reason windows will not boot into the OS is beyond me,GRUB recognized it and set it to boot,the rest is done by windows,and if the scroll bar comes up it's windows which has taken over and GRUB hasn't anything to do with that anymore.
You can try safe mode by selecting the OS with GRUB and push F8 right after wards to get to the safe boot selection menu from windows.
If that works try to restore windows to an earlier date to see if you can get it to boot properly.

If nothing else will do the job,take a look at the Super Grub Page.
I didn't used it myself but it seems to being able to boot a variety of OS's,and it's always handy to have such a disk.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by say592 on 2006-12-17
Hey, its not your job to know windows, so thats fine.....Could I reinstall windows, then ubuntu? Would it all be in the right place then? Thanks!

---

### Post by bulldog on 2006-12-17
Well if you have the time just do so,windows first and ubuntu second.
It should be fine after that.
Don't disconnect anything,leave it as it is.

Speaking of jobs,we'll volunteers in here just trying to help as much as we can......:-)

---

### Post by say592 on 2006-12-17
Yeah, I know about  the whole volunteer thing......(you may not be familier with the psp but I am sure you know what it is, I have a site with about 100 members, and on the official site I have over 1000 posts, so I know what it is like to volunteer! lol)

And yup windows then ubuntu that is what I will do!

---

### Post by gn2 on 2006-12-17
> **say592 said:**
> whats the benefit or diff. doing it this way compared to the other guys.....

The benefit is it's *very* simple, quick and effective.

So long as you can bring up a "Boot Device selection Menu" it works first time every time.

---

### Post by say592 on 2006-12-17
> **gn2 said:**
> The benefit is it's *very* simple, quick and effective.

So long as you can bring up a "Boot Device selection Menu" it works first time every time.

WOW you are a bit behind lol, we are nearly solved now!

---

### Post by gn2 on 2006-12-17
> **say592 said:**
> WOW you are a bit behind lol, we are nearly solved now!

How near? :) 

Maybe you could have been fixed ages ago............... ;)

---

### Post by say592 on 2006-12-17
How near? I just have to reinstall EVERYTHING lol thats about it! I should be done in about 6hrs!

---

### Post by bulldog on 2006-12-18
6 hours?,windows half an hour and ubuntu half an hour,some drivers in windows and up you go :D 
So in one and a half hour you should be online again.

Don't forget to install your new graphics before you install the OS's,so you start fresh with this card.

---

### Post by gn2 on 2006-12-18
> **bulldog said:**
> 6 hours?,windows half an hour

Plus time for all the utility/security software installs/updates/re-boots.......

---

### Post by x1a4 on 2006-12-21
> **say592 said:**
> Ok, I installed ubuntu (edgey) on my 20gb slave drive, I did this when windows had a virus, mainly to back up my info, but also to give linux a try. I love linux! However other members of my house dont understand firefox, let alone linux. When XP had its virus, grub picked it up and had it added, but now that I formated my master (the windows drive) and reinstalled xp it doesnt pick it up! How do I get it to even start, because its not so much of an issue of gruuby not picking it up, its that it doesnt even start! I mainly want grubby back and ubuntu so that my family can use their xp, and i can have ubuntu. Now what do I do!

Windows only sees M$ operating systems.  When you reinstalled windows it overwrote the Master Boot Record and deleted GRUB--very inconsiderate behaviour.

Here's what you do.

1) Insert the Ubuntu CD into the drive.
2) Reboot
3) Enter BIOS
4) In BIOS, ensure your system is configured to boot from CD
5) Boot to the Ubunto CD
6) While running Ubuntu from the CD, open a terminal and type the following: 

sudo grub

(and hit enter)

in the grub shell type the following (one line at a time, followed by the Enter key): 

[indent] root (hd0,1) [/indent]
[indent] setup (hd0) [/indent]
[indent] quit [/indent]

7) Reboot

---

