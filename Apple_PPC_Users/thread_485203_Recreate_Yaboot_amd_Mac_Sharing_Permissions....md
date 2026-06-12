---
title: "Recreate Yaboot amd Mac Sharing Permissions..."
date: 2007-06-26
forum: Apple PPC Users
---

### Post by DukeZenAku on 2007-06-26
Hi all i'm Doug.

I install Ubuntu 7 in my Mac Mini G4 in a partition and let another to Mac, but 3 days ago i was using Windows in Virtual PC, and when i try to install a keyboard drive the program goes crazy and let my Mac OS instable so i have to reinstall all Mac OS, during the instalation i lost the 'Yaboot' partition, and another problem is, i make a backup of some important files in the Ubuntu partition (when i reinstall Mac OS) but now i can put this files again in Mac OS,  so i like to know:

-How can i recreate just the Yaboot (Ubuntu still installed)?
-How can i 'share' the files between Mac OS and Ubuntu, somethig like 'MacDrive'?

Sorry expand one thread with this questions but it's the first time i run Linux and it's being a little bit confusing for me use it.

Thank's if someone can help me and sorry by my bad English...

---

### Post by pxwpxw on 2007-06-27
If you have really lost the Apple_Bootstrap partition, you will have to reinstall Ubuntu.

But if you have MacosX you can check this from the terminal.app command line
using 
```

$ diskutil list

```

Also:
MacosX has probably reset the boot-device in open firmware.

If you can start up with Option key held, you might see the Linux button as well as the Macosx. I dont know if this works for the  mini.

You can also check this from MacosX terminal
```

sudo nvram boot-device

```


===========================
You can write files from ubuntu to macos extended, but need to disable journalling to do this - use the terminal command line 
```
 
 diskutil disableJournal 

```

Access to linux files from MacosX. ext2fsx at  sourceforge.
[http://sourceforge.net/projects/ext2fsx/]("http://sourceforge.net/projects/ext2fsx/")

---

### Post by DukeZenAku on 2007-06-27
How i say, i'm new at this, when i type the "diskutil list" this  appear for me:

/dev/disk0
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *74.5 GB  disk0
   1:    Apple_partition_map                    31.5 KB   disk0s1
   2:        Apple_UNIX_SVR2 UNTITLED           9.3 GB    disk0s2
   3:              Apple_HFS Alice              64.9 GB   disk0s3
   4:        Apple_UNIX_SVR2                    253.7 MB  disk0s4
   5:        Apple_Bootstrap                    16.2 MB   disk0s5

I don't realy understand to much of partitions and things like it, so what is right or what is wrong? the "Apple_Bootstrap" still in there so i can install only 'Yaboot' again?

And about the "sudo nvram boot-device" when i type it Terminal return me this:

boot-device     pci2/ata-6@D/@0:3,\\:tbxi

What mean?

And thank's for the "diskutil disableJournal" command 'pxwpxw' work's very well for me, now i have my old files again :D what don't work is the app's that you tell me, i use Panther (yet) when i try to mount Ubuntu like a volume the Preference Pane return me this:

Disk Error

Command: Mount
Device: disk0s2
Message: The filesystem may need repair. Plesase use Disk Utility to check the filesystem.
Error: 0x1FFFFFFF

The info that i receive from the app when i select the Ubuntu partition is:

IOKit Name: untitled
Device: disk0s2
Connection Bus: ATA
Connection Type: Internal
Ejectable: No
DVD/CD-ROM: No
Mount Point: Not Mounted
Writable: Yes
Filesystem: Linux Ext3 (Journaled)
Volume UUID: 91BF2949-6C70-471C-8D39-045E95E9DF94
Device Size: 9,27 GB (9.950.000.128 bytes)
Device Block Size: 512 bytes

And thank's for the help, it's good find a forum that works :D

---

### Post by pxwpxw on 2007-06-27
The diskutil list shows 
 5: Apple_Bootstrap 16.2 MB disk0s5

 Means yaboot is probably OK. 

the boot-device pci2/ata-6@D/@0:3,\\:tbxi

makes it boot from  3: Apple_HFS Alice 64.9 GB disk0s3

so if you change the boot-device back to partition 5, yaboot should come back to life.

Try this from macosx terminal:

```

  sudo nvram boot-device=hd:5,\\:tbxi

```
If that fails, you can get nack into macosx by starting into Open Firmware by
holding 4 keys Command(Apple) Option o f
during startup
and type
```

 setenv boot-device hd:3,\\:tbxi

```

 Or you may get back by holding down Option during startup.

=====

There are earlier versions of ext2fsx that would porbably work for Panther, look for other versions on the sourceforge link.

---

### Post by DukeZenAku on 2007-06-27
[SIZE="4"]IT'S ALIVE[/SIZE]

Your comands work very well, the Yaboot has been not deleted when i reinstall Mac OS, it's my confusion, i think Mac OS use the Apple_Bootstrap partition to make a boot machine like Yaboot. but i get a new problem in Mac OS, before put the 'backup' files into Mac OS again, Mac OS start to run slow, apps that start in 5 or less seconds is taking more than 20 to open, for example, when i make my login normaly takes 1 or 2 seconds to finder start and show my dock, icons and desktop (be read to be used), now it's taking more than 20 seconds to dock and the rest appear, whats happening? Ubuntu changes something in Mac OS partition? other app's is having the same problems, Photoshop is taking the double of the time to open.

And i have 2 last doubts about Ubuntu, it's necessary install specials app's (developed only to PPC version), i try to install some app's but this app's don't recognize the processator type, something wrong? and how you learn all this thing's about Ubuntu and Mac OS terminals 'pxwpxw'? (some book)?

And one more time thank's for the help with the other app's.

---

### Post by pxwpxw on 2007-06-28
> **DukeZenAku said:**
> [SIZE="4"]IT'S ALIVE[/SIZE]

 i get a new problem in Mac OS, before put the 'backup' files into Mac OS again, Mac OS start to run slow, apps that start in 5 or less seconds is taking more than 20 to open, for example, when i make my login normaly takes 1 or 2 seconds to finder start and show my dock, icons and desktop (be read to be used), now it's taking more than 20 seconds to dock and the rest appear, whats happening? 
I dont really know.
You could try re-enabling journalling, that might affect startup times, that is all I can suggest.
> 
 Ubuntu changes something in Mac OS partition? other app's is having the same problems, Photoshop is taking the double of the time to open.

Ubuntu does not change anything in MacOS, but you might have - transferred files perhaps?
If you installed the ext2fsx application, that may be doing something in the background, trying to mount ubuntu partitons in Macos.  Try unsinstalling it. 
> 
And i have 2 last doubts about Ubuntu, it's necessary install specials app's (developed only to PPC version), i try to install some app's but this app's don't recognize the processator type, something wrong? and how you learn all this thing's about Ubuntu and Mac OS terminals 'pxwpxw'? (some book)?

Yes you need ppc version for binaries,  but if there are specific applications you need, you could post another thread to ask where to get compatible versions - you might need to edit your /etc/apt/sources.list, to include more repository mirrors.

---

### Post by DukeZenAku on 2007-06-28
> **pxwpxw said:**
> I dont really know.
You could try re-enabling journalling, that might affect startup times, that is all I can suggest.

I alread do it (before redirect my boot disk to Yaboot), can you tell me what is "Journal"?

> Ubuntu does not change anything in MacOS, but you might have - transferred files perhaps?

Yes i transfer the files using Ubuntu disk (the "live" option) to my Mac OS desktop, before this my Mac OS is runing "slow", 20 seconds to see dock and other icons is prety annoying.

> If you installed the ext2fsx application, that may be doing something in the background, trying to mount ubuntu partitons in Macos.  Try unsinstalling it. 

You're right again, when i redirect the boot partition to Yaboot again i don't use the instaled Ubuntu (in last 2 days), today when i acess Ubuntu, Mac OS start to give me a visual "awser" to this "mount-action", now each time i Login at Mac OS a "HD" icon to "simbolize" the Ubuntu partition appear in my desktop, i alread unnistal the ext2fsx and retype the "diskutil enableJournal /" but Ubuntu still in there, i can acess any file into Ubuntu (even system files) without any  problem, this is good, but if this is causing this delay in Mac OS i prefer don't have it.

Mac OS mount it like a "?" partition and ext2fsx like "UNTITLED", i'm confuse.

> Yes you need ppc version for binaries,  but if there are specific applications you need, you could post another thread to ask where to get compatible versions - you might need to edit your /etc/apt/sources.list, to include more repository mirrors.

Can you help me with some of this APP's? To be honest i decide install a Linux distro in my computer to learn how manage a Web Server (i'm going to university to study web-development and server management), how it's visible, it's going to be a little hard for me learn it :( and what is this "sources.list", it's some "shortkut" to Ubuntu "automatic" downloads?

Apache
PHP
MySQL or Postgree SQL
A webmail and forum program
A "port" protecting APP
A "html-css" editor like Dreamweaver.
A program to develop "Flash" animations.
3-Program to drawn like Corel draw.

One more time i'm sorry annoy you like i'm doing, and thank's for all your help.

---

### Post by pxwpxw on 2007-06-28
**journalling:**

google "journalling file syatem" will give a full explanation.

**ext2fs manager:**

I uninstalled it for the same reason, it kept mounting every linux partition, and I have a lot of them on 2 disks, so I use it only for special tasks.

I uninstalled the Tiger version using the Ext2Uninstall.command
There is also an option for Automount (ReadMe). I have not tried that.
I have these files in my ext2fs folder, but not in use now:
```
 
-rw-r--r--      13358 Dec  4  2006 Changes.rtf
drwxr-xr-x        102 Dec  4  2006 Ext2FS.pkg
-r-xr-xr-x       1873 Feb 20  2006 Ext2Uninstall.command
-rw-r--r--       9804 Dec  4  2006 ReadMe.rtf

```
That is all I know about ext2fs.

**APP's**:

I cant really help there, I get all  I want from the availabe ubuntu packages and some others using  synaptic package manager, and reading forum posts.

But you need to read some basic documentation about installation and package management see the **"User-Docs"** link in my signature below. A list of all available ubuntu packages is at
[[COLOR="Red"]http://packages.ubuntu.com/[/COLOR]]("http://packages.ubuntu.com/")

Some good documentation is also on the Debian web site.

> 
One more time i'm sorry annoy you like i'm doing, and thank's for all your help.

You are welcome.:)

---

### Post by DukeZenAku on 2007-07-01
> **pxwpxw said:**
> **journalling:**

google "journalling file syatem" will give a full explanation.

Google it's not bad, but i prefer [Wikipedia](www.wikipedia.com)

> **ext2fs manager:**

I think this is my problem, i stilll using Panther, i will wait for Sneak Peak release, if don't run in a PPC (i prefer believe in the oposite), i'll get Tiger, i try to unnistal ext2fs in all the ways, but before install him, he don't go out anyway.

But i think i get a "peace accord" with my Mac, i reinstall Ubuntu like a .ext2 partition and reinstall my Mac OS too, still a little bit slow to show me dock and the other things, but much more faster than it was.

What is this codes?
> -rw-r--r--      13358 Dec  4  2006 Changes.rtf
drwxr-xr-x        102 Dec  4  2006 Ext2FS.pkg
-r-xr-xr-x       1873 Feb 20  2006 Ext2Uninstall.command
-rw-r--r--       9804 Dec  4  2006 ReadMe.rtf

And my last question is: do you know if exist a "Emulator" like: 'Virtual PC', 'Paralells Desktop', 'Mac on Mac' and others, that can read the Ubuntu partition in my HD and show me it like this emulators?

I mean something like this: (i develop the image)

[[IMG]http://img207.imageshack.us/img207/1739/mesafd8.th.jpg[/IMG]](http://img207.imageshack.us/my.php?image=mesafd8.jpg)

> **APP's**:

I cant really help there, I get all  I want from the availabe ubuntu packages and some others using  synaptic package manager.

Don't worry, i'm going to study more Ubuntu soon as i can, and i don't realy need of this APP's with "urgency".

One more time thank's for all your assistence.

---

### Post by pxwpxw on 2007-07-02
That list of 4 files is the installer files from the Ext2fs utility - you must use the  Ext2Uninstall.command to uninstall successfully..

For the other things, I dont know about emulators, dont use them. Start a new thread for new topics, you will get more answers.

Cheers.

---

