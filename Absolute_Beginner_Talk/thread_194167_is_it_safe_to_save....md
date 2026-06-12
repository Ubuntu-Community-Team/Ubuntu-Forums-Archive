---
title: "is it safe to save..."
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-11
files to my boot folder? like like mp3's and videos?

---

### Post by manicka on 2006-06-11
You could but it would be a bad habit to get in to

---

### Post by aysiu on 2006-06-11
I think a good question to follow this up would be: Why do you want to save files to your /boot folder?

---

### Post by maddbaron on 2006-06-11
b/c its the only folder i can find not associated with /home i went to my drives and darn near everything leads back to /home. i am worried i will run out of space. i tried to take 4gigs of music off my cds and the systen said i was running out of space(even tho i gave ubuntu 20gigs of space....

can i share a space with my windows partion? there is a 7gig part that i assigned to windows when i set up ubuntu anyway i can make it so both windows and ubuntu can read off it?

i need to find more free space within the 20 create a network of folders and stuff....

---

### Post by aysiu on 2006-06-11
So /boot is on its own partition, and that partition has space but your /home partition doesn't?

Give us a better sense of your partitioning scheme. Can you post the output of these two terminal commands? ```
sudo fdisk -l
df -h
``` Copy and paste is good--you don't have type out the commands.

---

### Post by Rinzwind on 2006-06-11
maddbaron: did you stuff some files into trash? If so there might be some space to be regained :)

---

### Post by 3rdalbum on 2006-06-11
Put directly, it's safe to save things anywhere as long as they don't replace any important system files. However, back all that data up before doing a dist-upgrade.

---

### Post by NeghVar on 2006-06-11
What it sounds like is all of his Ubuntu is on 1 partition but he wants to save his music and movies to a folder that isn't his home. Kind of like the Shared Music/Videos folder on Windows I'd imagine.

---

### Post by maddbaron on 2006-06-11
> Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         383     3076416   12  Compaq diagnostics
/dev/hda2   *         384        3828    27671962+   c  W95 FAT32 (LBA)
/dev/hda3            3829        6404    20691720    5  Extended
/dev/hda4            6405        7296     7164990    b  W95 FAT32
/dev/hda5            3829        4159     2658726   82  Linux swap / Solaris
/dev/hda6            4160        4874     5743206   83  Linux
/dev/hda7            4875        5639     6144831   83  Linux
/dev/hda8            5640        6149     4096543+  83  Linux
/dev/hda9            6150        6404     2048256   83  Linux


yeah i emptied the trash got some space back. my thing is i tried to create folders in the other partitions and it wont let me only in the home holder can i do that. the more i learn of linux the more space i will want. i have all the programs i want already and i am trying to learn wine so i can bring in 3 writing programs but i need space 4 that. once i do i dont need windows having all this space anymore but until then i want to be able to set up a file system chain but dont want to use /home exclusively since it will be cluttered with folders.  but thats my output. anything i can do?

edit: i can save anywhere? cool but i'd like to create folders to house them so i can link them....sorry i just trying to understand the file style here i am very detailed when it comes to my files i like them nice and orderly lol.

---

### Post by xael on 2006-06-11
[QUOTE=maddbaron]files to my boot folder? like like mp3's and videos?[/QUOTE]
It's much better to save stuff you d/l  to the user's home folder (you could ask the system to keep it later, when reinstalling, if needed).

---

### Post by JanVH on 2006-06-11
> my thing is i tried to create folders in the other partitions and it wont let me only in the home holder can i do that.

Have you tried doing this as superuser? Try executing nautilus with

```
sudo nautilus
```

or place sudo before your directory-creating commands.

---

### Post by maddbaron on 2006-06-11
[QUOTE=JanVH]Have you tried doing this as superuser? Try executing nautilus with

```
sudo nautilus
```

or place sudo before your directory-creating commands.[/QUOTE]

can u explain the superuser code to me please? after i type sudo nautilus i do what? I am still very new to command line in fact i only just started making a cheat sheet lol...most of the stuff in installed program wise was thanks to automatix,synaptic and command line codes i saw around.

here is a visual breakdown of my hard drive.

that 7gig's in fat32 i would really love to make part of linux or at least be able to use it with ubuntu and windows but if that cant be done i really want to make it a linux space so i can split my hard drive down the middle one big part for windows and one big part for ubuntu.

and thanks for the help everyone i know it seems small what i want to do but i dont want to lose space if i download big files. i havent tested out the frostwire or ktorrent features yet and those are usually for huge files and with deadwood and entourage and other shows returning i want to have them in my main os(now ubuntu) so i can view them easy b4 i burn them to cd.

---

### Post by JanVH on 2006-06-11
A superuser is a kind of user that can do everything he wants to the system. Normally Ubuntu starts up in a normal user mode, the username you gave up when you installed Ubuntu.

Some commands however need you to identify as superuser, because they can possibly harm the system. This can be done by typing 'sudo' before the command you want te execute. It will ask for your password.

If you run 'nautilus' as a superuser, you should be able to create new directories and things like that where and how you want it. As a non-superuser you'll probably won't be able to do that everywhere.

---

### Post by maddbaron on 2006-06-11
ooooohhhhh ok thanks i will now try it...

---

### Post by maddbaron on 2006-06-11
it works! thanks!!!!!

ok now to my 7gig spare partition that is set to windows.

is there a way to make it useable to both windows and ubuntu? 

or just bring it to ubuntu thru gpart without reformating ubuntu?

---

### Post by JanVH on 2006-06-11
Windows XP uses NTFS as file system. It's only readable in Linux, so you can't write anything to it. Maybe there is a way to write to it, but I shouldn't use it.
Windows 98 and less use FAT32. That's automatically readable in Nautilus.

You can't convert NTFS to FAT32, as far as I know.

I have a NTFS-partition for Windows XP, a FAT32-partition for my files (that's accessible in both Linux & Windows) and an ext3-partition for linux. I think this is the most elegant way to go, if you want to keep on using Windows for applications that don't have a Linux-alternative.

---

### Post by maddbaron on 2006-06-11
yeah my windows xp and the 7gig partittion is fat32. i cant write to my fat32? like save files there?

EDIT: I just opened my 7gig and tried to create a folder there and it let me! does this mean i can save files and media there too? so windows and ubuntu can read and write to there?

if so...i am saved!!!!! lol

---

### Post by JanVH on 2006-06-11
If it's FAT32, yes you can. You can also access them in Windows then... ;)

---

### Post by NeghVar on 2006-06-11
You CAN convert NTFS to FAT, I've done it with Partition Magic, it worked fine although there are some stories where it didn't work so well.

Linux CAN read and WRITE to NTFS, it is still experimental and has risks but it can be done.

Windows CAN read and write to Ext3 file systems, just do a google for ext3 in Windows or some such phrase, I know because I've had to do it.

Superuser or sudo should ONLY be used for limited administartive tasks, going on the web and downloading files or just surfing while SU could be hazardess to your computer's health.

Windows XP does not exclusivly use NTFS, it is quite capable of Using FAT as well.

Sorry for that, just dispelling some of the misconceptions/errors I've read, no offense meant to anyone, I'm sure I've made a mistake already in the above.

Onto the subject at hand, I would personally create a folder in your home directory called Downloads/Music/Videos/Whatever, then create sub folders in that, it doesn't clutter and it keep everything all nice in one place for you.

---

