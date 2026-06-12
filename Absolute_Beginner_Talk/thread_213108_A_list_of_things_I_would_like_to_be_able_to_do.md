---
title: "A list of things I would like to be able to do"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Tom Brokaw on 2006-07-10
Aside from play games, I would like to have my Ubuntu machine do all the same things my XP box can.  Preferably through easy methods, but if it works, it works.  I made a list before I installed U, and so I've marked things I've already got taken care of with an X.

What I am asking for is instructions (or links to instructions, natch) for these specific tasks, or as close as can be found.  I hope I'm not coming across as demanding.  These are things I would like to know how to do now, and I can learn stuff the long way when I'm comfortable doing these things.

1. Surf with firefox [X], with Flash [X] and QT [X] and WMP [X] embedded.
2. Create [X]and print office documents. 
3. Scan.
4. Listen to music, formats including MP3 [X], Ogg Vorbis, FLAC, 5. MPC, etc.
6. Watch videos, including AVIs, MPGs [X], MOVs, and hopefully even WMV [X], etc.
7. Share files on the network. [Haven't fully tested all the way around, but can at least currently import from Windows box to Ubuntu).
8. Use my USB drive. [X]
9. Edit photos. Using the GIMP is just a matter of learning - is there a more basic photo editor around?  I really like FastStone for Windows, if anyone is familiar with that.
10. Import pics from camera.
11. Email using Thunderbird [X].
12. Rip and Burn CDs.
13. Rip and burn DVDs.
14. Download via BitTorrent [X]
15. Get my 5-button mouse to work properly. Note: It's a Logitech MX510 *going through a KVM switch.*  The KVM interfered with Logitech's proprietary software in Windows, so I may have to stick with it as  a 3-button. [edit] Works in Firefox, might try to get it to work in Nautilus.


16. My second drive is a 250GB, NTFS single partition with all my music on it.  I understand NTFS is best treated as read-only in U, so I'd like to set it up so that I can modify and write new files from my Windows machine. [Edit] I went ahead and formatted this drive as ext3 and copied all my files over.


That seems like a long list to me, but it's at least the majority of what I do with my compy, if not everything.  Thanks in advance for your time.

---

### Post by nalmeth on 2006-07-10
7. Share files on the network. [Haven't fully tested all the way around, but can at least currently import from Windows box to Ubuntu).
**Check out samba**
9. Edit photos. Using the GIMP is just a matter of learning - is there a more basic photo editor around?  I really like FastStone for Windows, if anyone is familiar with that.
**Browse around synaptic, perhaps krita is a good start if you use kde, perhaps even if not.**
10. Import pics from camera.
[B]Plug in the camera to USB if you can.
You may enjoy F-Spot
[/B]12. Rip and Burn CDs.
**These tools are included I think**
13. Rip and burn DVDs.
[B]DVDShrink via wine, or k9copy natively for burning the DVD's.
Acidrip or DVD::RIP to encode to avi
[/B]16. My second drive is a 250GB, NTFS single partition with all my music on it.  I understand NTFS is best treated as read-only in U, so I'd like to set it up so that I can modify and write new files from my Windows machine.
**Setup a fat32 data partition to share between windows and linux, or download the ext3 driver for windows. Or you can use the experimental ntfsprogs to dangerously write to NTFS from linux **
:)

---

### Post by MetalMusicAddict on 2006-07-10
> **Tom Brokaw said:**
> 
4. Listen to music, formats including MP3 [X], Ogg Vorbis, FLAC, 5. MPC, etc.
12. Rip and Burn CDs.
Give 2 players a look for #4. Listen & Amarok
See my sig for the Rip part in #12 and Bonfire or Gnomebaker for the Burn part. Your list is very doable BTW.

---

### Post by catlett on 2006-07-10
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) That's the dapper guide. It will give you commands for almost everything you want.
The only thing you have to make sure of is to change your sources list to there list. It gives the instructions and the list.
After you change the source list you pretty much just cut and paste the commands.

P.S. I don't know how simple you wanted to get with a photo editor but there is now Picasa for linux. [http://picasa.google.com/linux/](http://picasa.google.com/linux/)

When you get comfortable with your system, you can tackle your mouse issue. Here is one guide. There may be others. Just do a search in the forum search bar oir go to "How To's- Tips + Tricks" section. [http://www.ubuntuforums.org/showthread.php?t=188302](http://www.ubuntuforums.org/showthread.php?t=188302)

---

### Post by Anduu on 2006-07-10
> 3.Scan.
Give xsane a shot...it supports many scanners.

---

### Post by Sef on 2006-07-10
3. Scan - What scanner do you have or do you want?  Have you checked out the [http://sane-project.org/]("http://sane-project.org/")

---

### Post by CarpKing on 2006-07-11
> **Tom Brokaw said:**
> 
16. My second drive is a 250GB, NTFS single partition with all my music on it.  I understand NTFS is best treated as read-only in U, so I'd like to set it up so that I can modify and write new files from my Windows machine.

If you're willing to back it up and reformat that drive, you could make it ext3.  Check out [www.fs-driver.org](www.fs-driver.org) for drivers that allow Windows to read and write ext3.

---

### Post by Tom Brokaw on 2006-07-11
Thanks for all the pointers, especially the specific ones.  I'm a little busy tonight, so I won't get to mess with the U too much (gotta get some resumes out).

The scanner is a HP 1210 all in one printer/scanner/copier.  I have a few physical config things to do - right now, Ubuntu-compy is on the opposite side of my desk as my Windows; need to get them together to ease switching of the USB cable, and sharing an audio connection.

I'm glad nothing is too far out.  I had done some fairly extensive modifications to this case/computer, and then found a good deal on a Lian Li with some superior hardware.  I switched over to that one a little more than a month after I had finished all the modding on this case, so it was a little forlorn and hiding next to the closet.  It'll be happy to be back in use and the limelight.

Apologies to those who find this type of thing garish.

[[IMG]http://img162.imageshack.us/img162/1566/leftside9ge.th.jpg[/IMG]](http://img162.imageshack.us/my.php?image=leftside9ge.jpg)

[[IMG]http://img129.imageshack.us/img129/9960/rightside8gp.th.jpg[/IMG]](http://img129.imageshack.us/my.php?image=rightside8gp.jpg)

---

### Post by Tom Brokaw on 2006-07-12
> **nalmeth said:**
> 7. Share files on the network. [Haven't fully tested all the way around, but can at least currently import from Windows box to Ubuntu).
**Check out samba**
9. Edit photos. Using the GIMP is just a matter of learning - is there a more basic photo editor around?  I really like FastStone for Windows, if anyone is familiar with that.
**Browse around synaptic, perhaps krita is a good start if you use kde, perhaps even if not.**
10. Import pics from camera.
[B]Plug in the camera to USB if you can.
You may enjoy F-Spot
[/B]12. Rip and Burn CDs.
**These tools are included I think**
13. Rip and burn DVDs.
[B]DVDShrink via wine, or k9copy natively for burning the DVD's.
Acidrip or DVD::RIP to encode to avi
[/B]16. My second drive is a 250GB, NTFS single partition with all my music on it.  I understand NTFS is best treated as read-only in U, so I'd like to set it up so that I can modify and write new files from my Windows machine.
**Setup a fat32 data partition to share between windows and linux, or download the ext3 driver for windows. Or you can use the experimental ntfsprogs to dangerously write to NTFS from linux **
:)

The install instructions on Samba's page were beyond Greek to me.  I'll have to do considerable research before moving ahead with that.

Krita didn't appear to be what I need at a cursory glance.  F-stop, however, did.  

I checked out k9copy, and it looks pretty cool.  I'll try to burn a DVD later.  I hadn't asked for a DVD to AVI converter, but that doesn't mean I can't use one. Good catch, thanks.

I'll skip the ntfsprogs, thanks.  :)  I was going to ask dangerous how, but I'll go there and find out for myself.

Sane didn't list my printer/scanner, so I'll skip that for now.  I've got a backup plan, so no stress freaking out about how to print a resume RIGHT NOW.

> **MetalMusicAddict said:**
> Give 2 players a look for #4. Listen & Amarok
See my sig for the Rip part in #12 and Bonfire or Gnomebaker for the Burn part. Your list is very doable BTW.

Did a google for Listen and Listen linux and couldn't find it.  Downloaded Amarok and will give it a try later on.  I had actually heard great things about it recently and was disappointed there was no Windows version.  I really like my quintessential on XP, but the developer of that project has stated there will be no linux port.

I'll try to learn more before I post more about ripping and burning - forgot about them because I got all happy about synaptic.

That was my first time using it on my own, and I really really liked it.  It's like a little software store in your computer - you just search right there, in the OS, and then you get stuff!  How friggin cool is that?

A related question: I had read that downloaded programs aren't separate applications, but additions/upgrades to the actual OS kernel?  Is that right, or did I completely twist that around?  That's probably not a priority to learn.

babble babble, tired, long day, excited.  I don't think I've been this excited about my computer since I got broadband 4 years ago.

---

### Post by catlett on 2006-07-12
Amarok is in the repositories. No need to download. Always do a search in Synaptic Package Manager for an application. It will install easily with all dependencies taken care of. (Synaptic is found at System<Administration<Synaptic Package Manager)
The guide I linked you to earlier walks you through the setup of applications it deals with. It has a section for Amarok and Samba.

---

### Post by Perfect Storm on 2006-07-12
*9. Edit photos. Using the GIMP is just a matter of learning - is there a more basic photo editor around?  I really like FastStone for Windows, if anyone is familiar with that.*
Pixel32 (photoshop clone, commercial $29)
Cinepaint (free)
Photoshop 7 via crossover office (commercial)
Gimpshop (free, interface like photoshop)


*10. Import pics from camera.*
When I borrow a camera and plug it to ubuntu it automatically starts image viewer, from there I can save the pics on my computer. Maybe your camera is non-compatiable with ubuntu.

---

### Post by Tom Brokaw on 2006-07-12
> **catlett said:**
> Amarok is in the repositories. No need to download. Always do a search in Synaptic Package Manager for an application. It will install easily with all dependencies taken care of. (Synaptic is found at System<Administration<Synaptic Package Manager)
The guide I linked you to earlier walks you through the setup of applications it deals with. It has a section for Amarok and Samba.

I got it through Synaptic.  I thought the repositories were online - are they on my computer?  If so, how does that not bloat the hell out of the program?  I would have sworn the dialog box said it was DLing the packages.  I'm at work right now, can't get something else to make sure.

---

### Post by MetalMusicAddict on 2006-07-12
> **Tom Brokaw said:**
> I got it through Synaptic.  I thought the repositories were online - are they on my computer?  **If so, how does that not bloat the hell out of the program?**  I would have sworn the dialog box said it was DLing the packages.  I'm at work right now, can't get something else to make sure.

They are online and on your cd. Bloat you might run into though is using a KDE app. It will install alot of extre files that make some OCD types like me feel dirty.

If you want to use Listen (Its a Gnome based app) add these lines to your sources.list:

```
#Listen Music Player
deb http://theli.free.fr/packages/dapper/ ./
```

If you dont know how to do that do this. From a terminal paste this: **sudo gedit /etc/apt/sources.list**. That will bring up a file in a text editor. Add the Listen lines at the end of the file and save. Then from the terminal **sudo apt-get update** then **sudo apt-get install listen**. Your using Dapper right?

---

### Post by Brunellus on 2006-07-12
> **Artificial Intelligence said:**
> *9. Edit photos. Using the GIMP is just a matter of learning - is there a more basic photo editor around?  I really like FastStone for Windows, if anyone is familiar with that.*
Pixel32 (photoshop clone, commercial $29)
Cinepaint (free)
Photoshop 7 via crossover office (commercial)
Gimpshop (free, interface like photoshop)


*10. Import pics from camera.*
When I borrow a camera and plug it to ubuntu it automatically starts image viewer, from there I can save the pics on my computer. Maybe your camera is non-compatiable with ubuntu.
failing that, most cameras mount as USB storage, so you can simply copy/move images from the camera onto a directory of your choice manually.

---

### Post by catlett on 2006-07-12
> **Tom Brokaw said:**
> I got it through Synaptic.  I thought the repositories were online - are they on my computer?  If so, how does that not bloat the hell out of the program?  I would have sworn the dialog box said it was DLing the packages.  I'm at work right now, can't get something else to make sure.

Sorry about being unclear. Yes, the repositories are on line. The install cd can also be used as a repository but it has limited packages. Your system caches info about packages but doesn't keep the packages that are available on your system.
I thought you went to Amarok's site and downloaded the program that way. All the packages in synaptic can also be downloaded and installed from the source but synaptic is a better choice because it tracks the dependencies for an application and will install them as needed. If you download the source and install and something is needed as a dependency, your install will fail.

---

### Post by Tom Brokaw on 2006-07-12
OK, thanks for the clarifications.  Catlett, that's also my misunderstanding.  I really like how synaptic works, I just think it's awesome.

I'm using gnome, btw.  I prefer to leave things more or less stock until I understand more about what I'm doing.

---

### Post by bailout on 2006-07-13
Digikam is an excellent photo viewer/organiser with extensive eidting ability but not to the level and complexity of gimp/krite/ps.

---

### Post by Tom Brokaw on 2006-08-08
Been a while, but I had some time to get back to learning Ubuntu.

I decided to make my 2nd drive compatible by reformatting it in ext3, and installing the ext2IFS drivers on the relevant Windows installs.  

So I installed gparted and formatted the drive as ext3.  However, now when I doubleclick on it, it won't mount and gives me this error:
> mount: according to mtab, /dev/hda1 is already mounted on /media/windows

mount failed

I did have it mounted on /media/windows when it was still ntfs, but it was hdb1.  

How do I unmount it from media/windows?  "Unmount" not offered with rightclick menu.  And why would it be showing as hda1?  It's the primary slave.

Thanks.

---

### Post by catlett on 2006-08-08
Post the output of these 2 commands 
```
cat /etc/fstab
```
```
sudo fdisk -l
```
The first one is the file that tells ubuntu what partitions to mount and where. The second is how your computer sees the hard drives. Basically you want to make sure that the 2 files match. The labels match and the filesystem type.

---

### Post by Third Thoughts on 2006-08-08
> **Tom Brokaw said:**
> Been a while, but I had some time to get back to learning Ubuntu.

How do I unmount it from media/windows?  "Unmount" not offered with rightclick menu.  And why would it be showing as hda1?  It's the primary slave.

Thanks.

open up the terminal and type
```

umount /media/windows

```
It might yell at you about only root being able to unmount, and if it does then just do
```

sudo umount /media/windows

```

~Andrew S.

---

### Post by Tom Brokaw on 2006-08-08
Thanks for the quick replies!

output of first command:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdg        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1    /media/windows ntfs  nls=utf8,umask=0222 0    0
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0


Output of second command:
> 
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2472    19856308+   7  HPFS/NTFS
/dev/hda2   *        2473        4763    18402457+  83  Linux
/dev/hda3            4764        4865      819315    5  Extended
/dev/hda5            4764        4865      819283+  82  Linux swap / Solaris

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30515   245111706   83  Linux


I did the sudo umount command, and then tried to browse the drive.  I got this error:
> mount: only root can mount /dev/hdb1 on /media/windows


Cat fstab now gives this:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdg        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1    /media/windows ntfs  nls=utf8,umask=0222 0    0
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0


Identical, no?  Seems like I need to tell the computer that this drive no longer needs to be mounted at /media/windows (I don't want it there anyway).

Edit:
I guess I need to edit my fstab file.  I typed 
gksudo nautilus
and browsed to the file, and it opened in gedit without the (read-only) part.  What's the code to back it up?  And what would I change the relevant line to, if this is the right way to do it?

---

### Post by catlett on 2006-08-09
You have 2 partitions mounting at /media/windows. 

If I am right you still want to mount windows the ntfs one at /media/windows. But you now have a linux drive at hdb1.

Do this to mount the hdb1 at /media/data

```
sudo mkdir /media/data
```
Then edit your /etc/fstab
```
sudo gedit /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdg /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb1 /media/data   ext3 defaults  0 0
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
```
Make sure to save the file. Reboot and windows should be mounted at /media/windows and your second drive will be mounted at /media/data

---

### Post by Tom Brokaw on 2006-08-09
> **catlett said:**
> You have 2 partitions mounting at /media/windows. 

If I am right you still want to mount windows the ntfs one at /media/windows. But you now have a linux drive at hdb1.

Do this to mount the hdb1 at /media/data

```
sudo mkdir /media/data
```
Then edit your /etc/fstab
```
sudo gedit /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdg /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb1 /media/data   ext3 defaults  0 0
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
```
Make sure to save the file. Reboot and windows should be mounted at /media/windows and your second drive will be mounted at /media/data

The other NTFS partition is my program setups backup and is not crucial, although I suppose it would be nice to be able to access it.  I'll try this tomorrow. Thanks!

---

### Post by Tom Brokaw on 2006-08-09
OK, that worked.  Now I need permissions to read and write to the drive.  Why can't I do that off the bat, it's not root?

Also, how do I change the color of my highlighted windows?  If I have several non-fullscreen windows open, the active one shows grey in the panel, and the others show white.  How can I reverse or otherwise customize this?

---

### Post by xpod on 2006-08-09
Just to say "cheers".....I now feel a bit better about ALL the questions i ask........lol

This lot are great eh

---

### Post by Third Thoughts on 2006-08-09
> **Tom Brokaw said:**
> OK, that worked.  Now I need permissions to read and write to the drive.  Why can't I do that off the bat, it's not root?


I'm not exactly sure what your asking... no that's not true, I'm not exactly sure what your current situation is. Do you not have any read or write permissions on those drives? Can you only read as root? Can you read as both root and normal user? Out of the box you cannot write to ntfs partitions because there is no safe driver to do so. If you'd like to set up read/write support for ntfs partitions look here [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

~Andrew S.

---

### Post by Tom Brokaw on 2006-08-09
> **Third Thoughts said:**
> I'm not exactly sure what your asking... no that's not true, I'm not exactly sure what your current situation is. Do you not have any read or write permissions on those drives? Can you only read as root? Can you read as both root and normal user? Out of the box you cannot write to ntfs partitions because there is no safe driver to do so. If you'd like to set up read/write support for ntfs partitions look here [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

~Andrew S.

Hi Andrew.

I currently cannot read or write to my 250 GB drive, which has been formatted ext3.  I did this as it seems to be safer to teach windows to use ext3 than to use NTFS with Ubuntu . 

I don't know if I can read as root or not because I don't know how to read as root.  I cannot read or write as normal user.  There is a folder in the newly formatted drive called "Lost and found" that I cannot read (no permission). I tried to drag and drop my Music folder from my Windows box to this drive, and it said I couldn't write (again, no permission).

I found a thread that also needed help with permissions, and tried to modify the code given to that person for my own fstab file.  Didn't work, and most frustrating, the backup fstab I saved to my desktop disappeared without a trace.  So now I can't mount the drive at all.  I'm about go out, but when I get back I guess I can take the fstab code from earlier in this thread and get back to square one.

Am I going to have to enter my password everytime I want to listen to a friggin MP3?

---

### Post by catlett on 2006-08-09
To set permissions for yourself you need this command (I do not know your user name so I will use tombrokaw, obviously edit in your username)

Enter this for one  of them

```
sudo chown -R tombrokaw:tombrokaw /media/data
sudo chmod -R 755 /media/data
```

And enter this for the other

```
sudo chown -R tombrokaw:tombrokaw /media/windows
sudo chmod -R 755 /media/windows
```

---

### Post by Tom Brokaw on 2006-08-09
Cool, that worked, thanks.  

[Question moved to here:
[http://www.ubuntuforums.org/showthread.php?t=233663]](http://www.ubuntuforums.org/showthread.php?t=233663])

---

