---
title: "Absolute newbie, can't write files to other partitions on hard disk"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by StarFire039 on 2007-04-12
Hi all, started using SuSE 9.2 a few years back and couldn't get my head round it, and recently installed ubuntu 6.10 and loving it (can't wait for feisty!!). However, I can't save things to my other partitions where my data is being stored. I'll explain it better by giving you an idea of my hard disk layout-

**hard drive 1 - 160gb**
3 partitions- root, swap, and data that couldn't fit on my other hard disk

**hard drive 2 - 120gb**
2 partitions- paging file for windows (only a gig) and the rest is all my music, pictures and work.

So when I open the partition on hard drive 2 that has all my work in, and open a word document, it'll come up in openoffice fine but I cannot edit it, let alone save it. I can't create folders or anything either, or save any other file to it. Obviously I need to do this, can anybody help? Also how do I create files in the filesystem? I guess it'd be the same thing, I want to import Windows fonts, and the guide I was using said to create a folder in some directory, but i can't do it as it says i don't have permission.

Thanks in advance!

---

### Post by ComplexNumber on 2007-04-12
is your windows drive fat32 or ntfs?

if it is ntfs, you need 2 components:
-firstly, you need to install the ntfs-3g packages
-download, install, and run [this]("http://flomertens.free.fr/ntfs-config/"). near the bottom of the page, you will see where you can download either the feisty or edgy debs. once you've downloaded it, double click on it to install it. then run it. this will enable you to write to the ntfs filesystem.

---

### Post by annda on 2007-04-12
you have two separate issues. one is write-access to you ntfs windows partition. here's a good guide:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

the other issue is write-access to system directories. you need to precede all commands with sudo (not su), which will grant you root privileges.

---

### Post by ComplexNumber on 2007-04-12
> you have two separate issues. one is write-access to you ntfs windows partition. here's a good guide:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)thats the complicated way....and it also doesn't work with some people.

---

### Post by gh0st on 2007-04-12
Ubuntu doesn't come with the read/write drivers for NTFS file systems. Windows uses NTFS by default. It's easy to sort out. Check this out [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Check out Easy Ubuntu it will make getting your system setup with MS Fonts and media codecs and stuff a lot less painful [http://easyubuntu.freecontrib.org](http://easyubuntu.freecontrib.org)

I found it invaluable when I first moved to Ubuntu :)

---

### Post by StarFire039 on 2007-04-12
Thanks a million guys! It worked.

Also, when you say

"the other issue is write-access to system directories. you need to precede all commands with sudo (not su), which will grant you root privileges."

How come I can't create a folder with the UI? Does it HAVE to be through terminal? If so, could you tell me the command? Thanks.

---

### Post by annda on 2007-04-12
by default, unix/linux is a multiuser system, so users can do anything they want to with their own files in their own directories (/home/username). not so in the system directories, which only root/uberadmin is allowed to fiddle with.

now that linux is going desktop, users are practically roots. but it is still a good idea not to let them/us do anything if we don't know exactly what we are doing.

here's a useful guide to the command line/terminal:
[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

all that said, you can run the file manager and do anything with root privileges from the terminal or create a launcher (right-click on your desktop) with that command:

```
gksu nautilus
```

---

### Post by ComplexNumber on 2007-04-12
[quote=Starfie039] How come I can't create a folder with the UI?[/quote]did you install and run ntfs-config? i can create and edit documents through the gUI after using that. if you have a look at the screnshot on my system, none of the options to create and edit things are greyed out.

---

### Post by StarFire039 on 2007-04-13
> **ComplexNumber said:**
> did you install and run ntfs-config? i can create and edit documents through the gUI after using that. if you have a look at the screnshot on my system, none of the options to create and edit things are greyed out.

I can create and edit documents in my NTFS documents now, I meant in my system directory in ubuntu I couldn't edit. That's all sorted now though. Thanks!

---

### Post by ComplexNumber on 2007-04-13
> **StarFire039 said:**
> I can create and edit documents in my NTFS documents now, I meant in my system directory in ubuntu I couldn't edit. That's all sorted now though. Thanks!
ok. sorry, i misunderstood. glad you got it sorted.

---

