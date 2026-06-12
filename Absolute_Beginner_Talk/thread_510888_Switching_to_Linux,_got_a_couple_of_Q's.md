---
title: "Switching to Linux, got a couple of Q's"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Kaeota on 2007-07-27
Hi guys =D i've ordered my linux CD, simply cause when ever i try to do ANYTHING on XP i get 50 billion different error messages, and the final outcome is corrupt half the time anyways >_< (stupid Microsoft :mad:), however, i have about 20 gig of anime on my comp, and due to internet restrictions [900 mb/month D/L limit =( ] i REALLY dont wanna have to find and d/l it again, so i was wondering if there's anyway other than a lot of disks to allow my files to remain on my computer, and it'd be nice to keep my settings while i'm at it, thought that's second.

i'm running 2 HDD's, a really old 8 gig FAT and a new 80 gig NTFS, however i think i read somewhere NTFS is Ms, so linux shouldnt run on it, any advice on this matter would be freakin awesome as well.

i understand basic's, can use the CLI etc, but beyond that i get really lost, really quickly =( so if its possible to get dumbed-down Info, it'd probably be more useful =D 

Thanks guys :)

---

### Post by styphon on 2007-07-27
I think the best way forward on this is to get either another internal hard drive, or an external hard drive and store your anime there. When you first get the harddrive format it as FAT32 so Ubuntu can read it.

---

### Post by Mornedhel on 2007-07-27
Is your OS on the FAT32 drive and your anime on the NTFS one ? If so you're good, you *can* read files from an NTFS partition, write support is still under development but usable.

Installing Linux on an NTFS filesystem may be possible at the cost of really heavy tinkering (read : not advised for beginners, possible with a few years experience). The best thing would be to find someone with a drive you can borrow to copy your anime on, then reformat your 80 GB to FAT32 (or even ext2 if you plan to go all Linux), then copy the anime back.

8 GB should be enough for a simple installation of Ubuntu, you may have to be careful with free space if you intend to install a lot of apps (and a lot of newcomers do once they find out how simple the installation procedure is).

However, if I were you, I'd replace the 8 GB drive, it may have been the cause of your problems under Windows (old drives do corrupt easily after all).

Keeping your settings will be more difficult. If you're talking about Internet bookmarks, it will be easy if you use a sensible browser (probably Firefox). What other settings would you want to keep ?

---

### Post by Kaeota on 2007-07-27
okay, however, having run with FAT for too long on my old computer, i have to ask, can linux re-format it into something better? because i'm really not keen on going back there.

Thanks for the advice though, i'll look into an external =D

OKAY: OS is on the NTFS, the FAT was removed from my old comp recently, have been having the errors for a LOT longer than that unfortunately =(
mainly i want to keep my stored net passwords (cause i dun really know most of them) and my bookmarks, and yep =D Firefox

---

### Post by Mornedhel on 2007-07-27
ext3 and reiserfs are *waaay* better filesystems than FAT32, they won't rejuvenate your drive though... ext2 is the default (and most stable/used/recommended) filesystem for a root partition (the one you'll have system files on, to talk Windows-like).

---

### Post by Smu on 2007-07-27
The new migration wizard on the Feisty installation should make it possible for you to get all the files you have on your \My Documents folder copied to your home folder in the new ubuntu installation. That should work, but I'd still recommend you to do a backup the files if they are really important...

---

### Post by spur on 2007-07-27
You can choose to do a 'manual' partition on installation and reformat a partition at that time or reformat later thrpugh ubuntu. I beleive their are a couple of programs that will let you reformat a parition that is an excessory one.(not the one you mount / on)

---

### Post by Kaeota on 2007-07-27
okay =D so linux does have its own? good, however what i mean is my 80 GB HDD, will i be able to format it as a ext3? or will i actually *have* to go out and buy a new HDD that will support it?

---

### Post by spur on 2007-07-27
During install you can reformat as ext2 or 3 or reisurfs or fat32(vfat).

---

### Post by Smu on 2007-07-27
> **Kaeota said:**
> okay =D so linux does have its own? good, however what i mean is my 80 GB HDD, will i be able to format it as a ext3? or will i actually *have* to go out and buy a new HDD that will support it?

It'll work just fine. No need to buy a new one..

---

### Post by Mornedhel on 2007-07-27
All drives support all filesystems (unless there are weird exceptions I don't know about). You can't reformat a drive to another filesystem and expect not to lose any data though, so backup, then reformat to whatever you want, then copy the files back. Warning : Windows only supports FATxx and NTFS, not most Linux-specific filesystems. Linux does work flawlessly with FATxx.

---

### Post by Kaeota on 2007-07-27
by flawlessly i'm guessing you mean as flawlessly as FAT32 will allow it to? hehe, but thanks guys =D that was really the only things that i was all that concerned about, however just as an after thought, how do i get all my bookmarks etc off of FF before i install ubuntu, because as i said, i have a few stored passwords i dont remember

---

### Post by styphon on 2007-07-27
Go into FireFox security options and you can view all the stored passwords. Write them down and then if you don't like the idea of written down passwords destroy (burning is a good option) them after you've reentered them in your new firefox.

---

### Post by Mornedhel on 2007-07-27
The Firefox bookmarks can be exported to an xml file from Firefox itself, the File menu I think. Then copy the file to your Linux installation, and when you have it up and running, you can open Firefox and import the bookmarks file.

---

### Post by styphon on 2007-07-27
> **Mornedhel said:**
> The Firefox bookmarks can be exported to an xml file from Firefox itself, the File menu I think. Then copy the file to your Linux installation, and when you have it up and running, you can open Firefox and import the bookmarks file.

That doesn't copy out the passwords though does it?

---

### Post by Kaeota on 2007-07-27
okay, thanks a heap guys =D now just to go sit by the mailbox ~yes, i'm nearly exited enough to sit out there for 4-6 weeks, lol~

---

### Post by Mornedhel on 2007-07-27
> **styphon said:**
> That doesn't copy out the passwords though does it?

Nope, only the bookmarked URLs. But he wanted both his bookmarks and passwords.

---

### Post by zabien1970 on 2007-07-27
Just a little insight, You might want to dual boot, I tryed but messed up my install and completely wiped windows, not necessarily a bad thing but I lost everything on my hard drive, if you got 20 gig of anime you want to save review the instructions for dual booting, then you should be able to access your files you want to save, just installing linux or any os could wipe your drive!

---

### Post by zabien1970 on 2007-07-27
Also, why wait? I downloaded the live cd then installed from that. it's not that large of a download and it's the same you'll get in the mail.

---

### Post by Smu on 2007-07-27
"About Ubuntu 7.04 Desktop Edition

The latest version of Ubuntu includes the following new features:

Windows migration tool: The new migration tool recognizes Internet Explorer bookmarks, Firefox favorites, desktop wallpaper, AOL IM and Yahoo IM contacts, and imports them all into Ubuntu during installation. This offers easier and faster migration for new users of Ubuntu and individuals wanting to run a dual-boot system." 
[http://www.ubuntu.com/news/ubuntudesktop704](http://www.ubuntu.com/news/ubuntudesktop704)

---

### Post by spur on 2007-07-27
Smu is right but I would back up to cd or somewhere safe anything you really want to keep.
[img]http://img172.exs.cx/img172/1236/bowtothefox7mw.gif[/img]

---

### Post by Sef on 2007-07-27
> Smu is right but I would back up to cd or somewhere safe anything you really want to keep.

Definately **Back up** your data.   During installs, nothing is 100% guaranteed.   Most likely everything will go well, but still there can be problems.  

> ext2 is the default (and most stable/used/recommended) filesystem for a root partition (the one you'll have system files on, to talk Windows-like).

Ext3 is the default.   If you dual boot, you can set up a partition to be shared by both XP and Ubuntu.    It used to be that you had to use FAT32, but now there is a tool that you can use to read and write to NTFS.  (Not sure of the name off hand.)

---

