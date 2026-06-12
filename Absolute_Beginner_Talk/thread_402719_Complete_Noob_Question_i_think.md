---
title: "Complete Noob Question i think"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by dragonschild on 2007-04-06
Ok, i burned ubuntu onto a cd reformmated my HD installed windows on a 10g partition, and then installed ubuntu on a 10g partition with a 1 gig swap space. For one, i updated ubuntu and got Kernel Panic: VFS : Mount something error, im on the old kernel now but it says its completly updated and works fine the newer one doesnt i just get that error so help on that would be appreciated. I searched for an answer and i think i found one but i have no idea what they are talking about and how to enter the commands ( ive never used ubuntu/any linix before, no nothing about it im just trying to get some expirience ). ok now my noob question as to the reason im posting, i have 160 gig hd. Ive made two 20 gig partitions and i want them to share the last 138 gig space for my music/videos/anime and want to be able to access them from both OS. Like being able to play the anime from Windows or Ubuntu but not having to have all the stuff on one or the other, i can acess it from both. Ive left the last 138 gigs unpartitions space for now because ive no idea how to do this. Also when i install games i want them to install on the extra 138 space, and run them through the windows OS, means i only gave it 10 gigs. Ive been looking for a few hours and cant find anything on this so any help is appreciated, im decent with computers but not great so please dont get mad if i seem dense. Anyways is all of this even possible?

---

### Post by foxmulder881 on 2007-04-06
Welcome draginschild.

Go into Synaptec and install GParted. This will allow you to configure your drive paritions.

If you format the remaining partition as FAT32, both Ubuntu and Windows should be able to access any files from it.

When you install a new game within Windows, you just have to select the FAT32 partition as the installation path.

Hope this helps.

---

### Post by jvc26 on 2007-04-06
Right, well the 138Gb partition you want to use as space that both OSs can see. Basically format it in FAT32 and then both OSs will be able to see it (Both windows and Ubuntu have FAT32 read-write support out of the box), or alternatively, format it in NTFS (window's proprietary Filesystem) and then install the ntfs-3g drivers so that Ubuntu can read-write to that partition. You may need to tell Ubuntu where the partition is to mount it, but that can be easily sorted out. To partition it download the GParted partition editor from Synaptic, or via: (This command is entered into the terminal)
```

sudo apt-get install gparted

```

To install games from the windows OS to the 138Gb is simple, when you're running the installer tell it to install to the 138Gb partition.

To enter the commands the odds are it will require you to use the terminal - Applications  -> Accessories -> Terminal

Hope that helps,
Il

---

### Post by KIAaze on 2007-04-06
Nooo, don't use NTFS or FAT32!

FAT32 is old and not good if you store big files or a lot of small files. It fragments a lot.
Like my compiler would say, it's deprecated. ^^
Only good for USB keys maybe to ensure portability...

NTFS is Microsoft proprietary stuff. I don't know how good the suggested ntfs-3g driver for Linux is, but it might eventually not be perfect since it was probably made through reverse engineering.
If it works well, then it's ok, if not...

...there is a better way:
Use the Ext2 IFS driver or Explore2fs. :)
->[Ext2 IFS]("http://www.fs-driver.org/") is a driver for windows giving you read/write access to Linux ext2/ext3 partitions.
->[Explore2fs]("http://www.chrysocome.net/explore2fs") is some kind of "windows explorer" for windows with which you can access your Linux partitions.

I prefer using Explore2fs since I don't feel comfortable with Windows having write access to my Linux partition. ^^'
(because it will have access to my root partition and I don't know how to prevent that so far)

The only problem with Explore2fs is that if you want to view a file, you first have to copy it locally to the windows partition.
While this is no problem for text files, it takes some time (and space) in case of music and videos. :(

Therefore, you might prefer using the Ext2IFS driver in your case.
It's easy to install and only requires one reboot.
You can even install windows programs on ext3 partitions that way.
(worked for opera in my case at least)

---

### Post by dragonschild on 2007-04-06
Thank you for all the help. Ive installed gparted already, and i decided to take the route of the ntfs 3g to make it so ubuntu will read ntfs, as i figure i will be using windows OS the most ( cus i play WoW and CS and alot of foreign games). And from what i hear most of them dont work in linux to well. ( atleast the foreign ones, like japanese beta games hehe). i downloaded the ntfs-3g-1.328.tgz but ive no idea how to install it haha.i opned it up and tried the autogen.sh as it kinda soundedl ike a windows exe installer part, but i just get this error.


 Run this to generate configure, Makefile.in's, etc

(autoreconf --version) < /dev/null > /dev/null 2>&1 || {
  (autoconf --version) < /dev/null > /dev/null 2>&1 || {
    echo
    echo "**Error**: You must have the GNU Build System (autoconf, automake, "
    echo "libtool, etc) to update the ntfs-3g build system.  Download the "
    echo "appropriate packages for your distribution, or get the source "
    echo "tar balls from ftp://ftp.gnu.org/pub/gnu/."
    exit 1
  }
  echo
  echo "**Error**: Your version of autoconf is too old (you need at least 2.57)"
  echo "to update the ntfs-3g build system.  Download the appropriate "
  echo "updated package for your distribution, or get the source tar ball "
  echo "from ftp://ftp.gnu.org/pub/gnu/."
  exit 1
}


no idea how to update autoconf so i dont know how to fix this heh X)


Also it says i need to download FUSE for 3g to work, and it looks hard to a newbie to install. they keep saying i just need to type ./configure but that does nothing on ubuntu or atleast for me, also i think im running ubuntu gnome if that helps, i have a gnome thingy in the apps/system tab.

---

### Post by dragonschild on 2007-04-06
Hmm, well i couldnt get that to work so i hopped onto windows and got the ext2 thing installed it after creating the last 138 gig partition in ext3 format, i tried to install steam onto the new partition and it said the Specified filepath was too long, just going to G ( now i have 4 partitons C E F and G now) c windows e linux, f the 1 gig swap, and G the 138 gig partition i was trying to get them both to use. I think im just gonna reformat it into fat32 as this is just being a huge problem so far heh.

---

### Post by foxmulder881 on 2007-04-07
If you just use FAT32 you won't have any issues such as the ones you've mentioned. Using FAT32 is perfectly fine. If it becomes too fragmented, just defragment within Windows.

---

### Post by dragonschild on 2007-04-07
yes formatting into fat32 seems to of worked so far, but i cant figure out how to access the stuff on hda4 (the 138 gig partition as ubuntu calls it). i can acess my windows folder but can get to the bigger partition.

---

### Post by timjohn on 2007-04-07
try post #5 on this thread [http://ubuntuforums.org/showthread.php?t=402986](http://ubuntuforums.org/showthread.php?t=402986)

---

### Post by dragonschild on 2007-04-07
that worked great, but now i messed something up, i used to have a harddisk looking thing on my desktop called windows and i used to be able to access it, now it says it cant find it when i try to access it from my desktop in ubuntu and im not sure what happened exactly. also what decoders/plugins do i need to watch wmv/avi/mpeg on ubuntu?

---

### Post by dragonschild on 2007-04-07
Update, i fixed the plugin problem everyhting is running fine now ( apperently ubunut gnome comes with totem-gstreamer wich cantp lay anyhting, theo ther totem install plays them fine htough)

Still got the other problem though, the windows thingy is still gone :(

---

### Post by KIAaze on 2007-04-07
Usually Ubuntu automatically mounts the windows partition in /mount, /mnt or /media (I'm under windows right now so I don't remember exactly).

If it's not there, just mount it manually.
Maybe Ubuntu has a GUI to do that, but I don't want to restart now to check. ^^'

Here's the command line way:
It's very easy. :)
1)Create a directory to mount your windows partition:
> mkdir /media/windows
2)List all available partitions:
> sudo fdisk -l
Search for the windows NTFS partition.
Lets assume it's on */dev/hda1* for now.
3)Mount the partition on the directory:
> sudo mount /dev/hda1 /media/windows

*sudo* means "do as superuser" (i.e. admin).
I don't know if you need to use sudo for mounting.
Just try it without sudo first and if it doesn't work, use sudo. ^^

If you want ubuntu to load the windows partition at every startup, you'll have to add an entry to the /etc/fstab file.

Note 1: This technique also works for external USB hard disks. ;)
And basically any storage device in fact.
For unmounting, simply use *umount*.
You might also want to look at the manual for the different options like setting read/write permissions.
> man mount

Note 2: I think the *media* folder is for things mountable by the user like USB keys, CDs, etc and *mount* is for stuff mounted automatically at startup (things listed in /etc/fstab file).
Not sure about that though.

---

### Post by dragonschild on 2007-04-07
Ah well, i screwed soemthing up somewhere on XP, to the point i had to reinstall it, and appernetly it does not like to reinstall onto a partition when theres another partition with ubuntu on it so i had to format my whole hd to install windows again. Im on windows right now everyhting seems to be running fine my games are running great, but last time i installed my ATI display driver and my games owuldnt play right anymore so i had to reformatt. im not gonna do that again this time and try installing ubuntu again. im doing it differently this time though, im making a 130 gig partition for windows and a 30 gig partition for ubuntu and ill make it so ubuntu can go into windows to get songs/anime but have windows do nothing with ubuntu like i did before. Hopefully this will fix all the problems.


Heh htis has been a great first learning expirience, i learned ALOT about what i need to do with it to get it running everything right :D

---

### Post by foxmulder881 on 2007-04-09
Sometimes (unfortunately) it takes a mistake to learn what not-to-do next time.

Hope you sort it all out. Give us a yell if you don't and we'll be sure to help you out.

Cheers!

---

### Post by dragonschild on 2007-04-09
Yep, its all running great now, i just need to remember not to update my drivers and everything works fine. No idea why yet heh. Updated ubuntu and it works great it plays all the windows files fine, though one small problem during installation of ubuntu. I accidently clicked on the find free space on the hd and it took 40 gigs from my windows partition, so now windows is 70 gigs and ubuntu 78 X)

---

