---
title: "Dual Booting Operating Systems (Multi-Linux Experienced Users Only!)"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by ubunick on 2005-12-15
I'm sorta confused.  I'm know less about partitioning than Linux honestly, and I know this isn't Ubuntu Linux, but I want to dual boot Fedora Core 4 along with Windows XP.

I only have one internal HDD (120GB), but also have an external HDD (80GB).

Anyway, what should I do to partition everything correctly so that I can dual boot? Please make the instructions/help VERY user friendly and thanks for any help you are able to provide.

---

### Post by brentoboy on 2005-12-15
to move forward, you have to be ready to format everything and start over. IF you cant do that, stop now.

There are partitioning utilities that try to let you preserve windows, and do this, but dont waist your time.

Also, for the sake of the forums, Im going to pretend that you want to install ubuntu not fedora, but the general ideas are exactly the same (maybe you want to make it tri-boot...?)

---

So, put in your xp cd, and when it asks to press any key to boot from CD, press the "any" key.

when it gets to the point where it asks you to choose a partition or drive to install windows on, (after you F8 your way passed the license agreement) delete any existing partitions. until you have one big 100+GB unpartitioned space.

Then create a new partion for windows. Make it as big as you want, but I dont see any need for more than 20GB for a win install.  remember, the win partition sizer takes numbers in MB not GB, so add 3 zeros behind your partition size.

that will leave you with a 20GB partition and a 90+GB "unpartitioned space"

tell windows to install on the new 20GB partition. 
you have a choice to make:  NTFS or FAT
FAT is old and sucky, but a documented standard, so it would be visible from linux with no effort whatsoever.  NTFS has better security, faster, more efficient... all around better.  but, linux doenst always do a good job working with it so if you want to see if from linux, use fat.

You are going to share your data on a different partition alltogether, so dont worry about your shared data at this point, only worry about whether or not you want your C drive to be acceable from linux.  if you want my opinion, the answer is no, so go with ntfs.

after that, sit and wait and watch while the winstaller does its thing.....

... stay tuned for the instructions on adding linux - next post (give me a minute to recoupe)

-b

---

### Post by MystaMax on 2005-12-15
I don't think anyone can give you a step by step guide right here right now as there are plenty on the web already, but I did [google your request]("http://www.google.com/search?hs=kM1&hl=en&lr=&c2coff=1&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=dual+boot+fedora+4+and+windows+xp&btnG=Search") and think I found something to help ya.

[http://users.tkk.fi/~tkarvine/linux-windows-dual-boot-resizing-ntfs.html]("http://users.tkk.fi/%7Etkarvine/linux-windows-dual-boot-resizing-ntfs.html")

[http://www.overclockersclub.com/guides/dual_boot_fedora_xp.php]("http://www.overclockersclub.com/guides/dual_boot_fedora_xp.php")

[This link]("http://www.linuxcompatible.org/Dual_boot_Win_xp_and_Fedora_core_t32552.html") is to another forum where a user asked the same question.

If I may add that google is very powerful, and if you can't find it in the forums check google next. Its very helpful. Hope that helps

**P.S.** Some of the tutorials are for Fedora 3, but you can get the general idea. Its only here to lead you in the right direction. Good Luck

---

### Post by brentoboy on 2005-12-15
step 2:

once you like your winstallation, pop in your ubuntu cd (or the linux flavor of your choice).

walk through the installer, until it gets to the point where it wants to partition your drives...

DONT LET IT AUTO PARTITION.

most linux installers will autopartition your entire "C" drive, and leave you with no windows.

instead, tell it you want to partition by hand.
add a partition using the ext3 file system that is about 20GB - this will be your linux / partition (root) it will be everything but your data.  You'll have to tell the partitioner to "mount" this partition at root (/)

add a second partition as linux swap, and make it about the same size as the amount of ram in the box.

now, make a 3rd partition (4th if you count the win partition) with the balance of the data.  make it fat32 (that is the easiest thing to share between all affected OSes).

mount this partition at /mnt/shared

/mnt is traditionally where you mount stuff that doenst go anywhere else.

then, proceed with the installation.

When it sets up grub, make sure it autodetects that fact that you already have windows installed. It always does (in my experience) but it is worth watching for, becuase repairing that problem could be anoying.

---

your shared partition will show up in windows as "D:" (or whatever) and in linux it will be accessable from /mnt/share

---

you will find the ALLCAPS.DOS filenames a liitle bit anoying when working back and forth between Win/Linux FAT32 shared partitions, but the end result is worth the ugly display names.

-b

---

### Post by ubunick on 2005-12-15
I'm not actually installing Ubuntu, like I said.  I've had MAJOR issues with Ubuntu and I got sick of it.  Thanks for the guide (I havn't yet used it).

---

### Post by thalliwell on 2005-12-15
[QUOTE=ubunick]I'm not actually installing Ubuntu, like I said.  **I've had MAJOR issues with Ubuntu and I got sick of it.**  Thanks for the guide (I havn't yet used it).[/QUOTE]

Well in that case may I suggest you ask all your questions at 
[http://fedoraforum.org/forum](http://fedoraforum.org/forum)

.....:confused:

---

