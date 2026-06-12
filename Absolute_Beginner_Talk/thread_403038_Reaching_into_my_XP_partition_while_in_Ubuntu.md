---
title: "Reaching into my XP partition while in Ubuntu"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by rbzelman on 2007-04-06
I'm pretty new to Linux, and I'm still in the "playing around with stuff" phase. I have my Dell Dimension 4550 set up with a fresh install (after formatting) of XP on one of its two 80 GB hard drives, and Ubuntu 6.10 on the other 80 gig drive. Yesterday, I had 7.04 beta on here, but was not pleased with the lack of support for Beryl on this version (can't blame them though, it isn't a full release yet) so I completely formated my Linux drive, and went back to 6.10. While 7.04 was installed, I was able to access my XP drive, which I believe was called just "disk" and I could work off it, putting all my music files in a media player library, etc. I can't do this anymore. I thought maybe I needed to install Wine, which I did, but that did not fix anything. Any ideas? Was that just a feature of Feisty?

---

### Post by pppetter on 2007-04-06
This link will help you out with that.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Btw. The wiki is awesome, if you have a question, the wiki will almost certainly have an answer... I just went to wiki.ubuntu.com and searched for NTFS.

---

### Post by theninthdimension on 2007-04-06
I might be able to help. I just mounted my Windows C drive in my Ubuntu 6.10 install yesterday using the directions in "The Official Ubuntu Book". I will attempt to underline all computer commands that you need to type. Here goes:

Open a terminal window and type sudo fdisk -l you will probably be required to enter your password. This command will return a list of all the drives your computer is recognizing. My return looks like this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 * 7 60408 485179065 7 HPFS/NTFS
/dev/sda3 60410 60801 3148740 db CP/M / CTOS / ...

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 59665 479259081 83 Linux
/dev/sdb2 59666 60801 9124920 5 Extended
/dev/sdb5 59666 60801 9124888+ 82 Linux swap / Solaris

What you want to look for is the device listed as an NTFS type. Mine is the /dev/sda2 listing above. This is what you will want to mount. Once you have found the drive's location, you will want make a place to mount the drive (I always crack up when I think of mounting drives). Anyway, the book recommends creating a mount point in the “media” file on your main file system. To do this, type sudo mkdir /media/C In this case the C is the drive letter.

Now, for mounting that bad boy. To do this, you need to make changes to your “fstab” file in the /etc directory. You may want to make a back-up of the file before you modify it. I didn't, and everything worked fine, but sometimes fortune favors the dumb. Anyway, you will now need to type the command sudo gedit /etc/fstab in your terminal. This will bring up the fstab file. Mine looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=c791e04d-fe04-4fe7-975a-786b398a5abd / ext3 defaults,errors=remount-ro 0 1
# /dev/sdb5
UUID=5dacee55-3692-4556-98e3-6111cb268835 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

At the bottom of this list, you simply need to type the following entry and then hit the save button:
/dev/sda2 /media/C ntfs nls=utf8,umask=0222 0 0

The /dev/sda2 refers to the device that the sudo fdisk -l command should have returned (see above). The /media/C entry tells the file where this disk should be mounted. The ntfs entry tells the file what format the beast is in. The nls=utf8,unmask-0222 entry allows any user on your Ubuntu install to read the file (I don't know how to modify this yet). I have no idea what the two 0s following this mean, but they were in the book so I added them.

The last thing you will need to do in the terminal is actually activate the mount. You do this by typing sudo mount -a. This immediately mounted the C drive for me, but you might have to restart your X-windows session by typing Ctrl+Alt+Backspace. Make sure that anything you want saved is already saved before you do this.

I have had no trouble reading any of the files that are readable on my C drive through this technique. I don't think you can edit them, but I haven't tried that yet.

Jeff.

---

### Post by rbzelman on 2007-04-06
Thanks for the link. I looked at it, and it seems that 7.04 has better support for what I want to do, which is why it worked automatically before. For the time being (before the 19th) I'd like to try doing what it recommends to get NTFS support on 6.10, but I'm having a hard time following the directions on the wiki. 

"Enable the universe repository and install the ntfs-config package."

What is this "universe repository" thing? I've heard it mentioned before in my search for Beryl information, but I don't quite understand what it is or what it does.

---

### Post by theninthdimension on 2007-04-06
rbzelman,

     To activate the universe repositories, go to System -> Administration -> Synaptic Package Manager. You may have to enter your password. Once in there, click on the Settings menu and choose Repositories (not be confused with suppositories). This will open a menu window. The first tab that should be open will list Ubunu 6.10 (or something similar). Just check mark the radio button next to the source you want repositories to come from. Just be aware of the ones which may present copyright restrictions.

Jeff.

---

### Post by rbzelman on 2007-04-06
Jeff, I tried your longer method with the terminal window and all that jazz, but to no avail. Thanks though.

Pppetter, as far as the shorter method with the universe repository, I apparently already have it activated, however I can't find anything pertaining to NTFS in the add/remove application thing. Should I be looking elsewhere in order to get this file?

At this rate, I may as well wait the 13 days for Feisty. Thanks for the advise so far. Any other ideas anybody?

---

### Post by benerivo on 2007-04-06
If you need the ntfs-3g driver, it will not appear in 'add/remove'. You will need to search for it in synaptic package manager (accessible through the main menu).

---

### Post by pppetter on 2007-04-06
Well, if you just browse further from the link I gave you...

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

Then, of course, after reading that, click Manage Repositories in Ubuntu. Read and you'll become the master of your OS ;)

---

### Post by Happy_Man on 2007-04-06
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

Have you tried that thread? I'm pretty sure it's what you're looking for.

---

### Post by kelvin spratt on 2007-04-06
if your stil having problems after all that go into admin gparted if the partition is mounted you will see a little padlock next to it if no padlock right click on the menu flag click on mount restart comp
thats what i did

---

