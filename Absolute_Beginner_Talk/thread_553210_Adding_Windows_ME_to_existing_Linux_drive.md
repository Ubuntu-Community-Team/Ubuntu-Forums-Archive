---
title: "Adding Windows ME to existing Linux drive"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by jandjfrench on 2007-09-17
Hi,
  I'm totally new to any version of Linux.
  I wanted to tell which version of Ubuntu I've installed but I can't even find that.  The CD identifies it as "Ubuntu 7.04"
  Last week I installed Linux to a new 200GB drive.  I used the entire drive.  I have things working fairly well but still have many questions.  I'm trying to gain more familiarity with Linux before I try to ask for help on those.
  I would like to add Windows ME to the drive but am fearful of screwing up my existing install.
  Any advice would be greatly appreciated.
  I'm fearful that I'll receive bad advice and won't recognize it as such so please let me know if you see this happening.
  Thanks all.
Jim F.

---

### Post by Calash on 2007-09-17
Well...putting aside the fact that ME is a horrid OS you will have a couple of things to consider.

1 - Drive space.  You will have to repartition the drive to allow for the new OS.  Windows only needs one partition, so you will have to shrink one of the linux partitions to make room.  Gparted will do this, I believe.  Partition magic will also do this if you make a boot CD

2 - When you install any windows OS, it will rewrite your MBR.  This means that the linux boot loader (GRUB) will be removed in favor of the Windows one.  This can be fixed by using the live CD and reinstalling grub.  I do not have the link, but the info on how to do it is in the official Wiki

When installing windows, be very careful to tell it not to overwrite the existing installs and just use the one partition.  Also be careful as you partition, it can be a dangerous process if done wrong.  Backup to be safe.

Version 7.04 is Feisty

---

### Post by Skidpad on 2007-09-17
Welcome aboard!  You hit the "version" nail right on the head - 7.04 (Feisty Fawn) is currently the latest release.  It was released in April 2007.  
Ubuntu versions consist of two numbers, in this case, the 7 signifies the year (2007), and the .04 signifies the month (April, being the fourth month of the year).  

The next planned release is Gutsy Gibbon, due out in October, 2007, so it will be 7.10.
/history lesson.  :)

To install ME (let's ask that question in a minute...) your best best is to download and burn the GParted Live Cd [Here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")
Boot from this cd and it will allow you to shrink your Linux partition, thus making room for the installation of ME.   Your best bet is to use GParted and not Partition Magic or other 3rd party Windows programs for this task.  Also, how much room to make for ME is up to you - it will depend on your anticipated use and document storage needs.

---

### Post by Kilz on 2007-09-17
> **Skidpad said:**
> To install ME (let's ask that question in a minute...)

Would that question happen to be 

Are you aware that since Windows ME reached end of life in July 2007 and that since its no longer being patched by Microsoft it is a security risk to run it?

Because it would be tops on my list. I just helped a relative get rid of a virus and adware infested ME computer last week.

---

### Post by r4ik on 2007-09-17
In plain French i would not install ME.
There is nothing Linux/Ubuntu can't do, my advice get you're teeth into linux spend some time with it just like you have to do with any other "new" OS,and enjoy the be pro's.

Good luck !

---

### Post by jandjfrench on 2007-09-17
Hi,

  Thanks to all who replied.  I'm currently downloading the "Gparted" .iso from SourceForge.net.  For some odd reason I wasn't able to see the "Release notes" as recommended.  I'll look into it.  By starting at the SourceForge.net home page I couldn't navigate to Gparted.  If anyone could provide the path I'd certainly appreciate it.
  To address the concerns expressed over Windows ME: I have some older programs and hardware that are no longer supported by newer (or different) OS's.  I do not intend to use it for the internet or any other net.
  I'm looking forward to the day that I'll be able to provide such assistance as I received.  Thanks once more.

Jim

---

### Post by rohan000 on 2007-09-17
> **jandjfrench said:**
> 
  Thanks to all who replied.  I'm currently downloading the "Gparted" .iso from SourceForge.net.  For some odd reason I wasn't able to see the "Release notes" as recommended.  I'll look into it.  By starting at the SourceForge.net home page I couldn't navigate to Gparted.  If anyone could provide the path I'd certainly appreciate it.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by creedog on 2007-09-17
> **jandjfrench said:**
> Hi,

  Thanks to all who replied.  I'm currently downloading the "Gparted" .iso from SourceForge.net.  For some odd reason I wasn't able to see the "Release notes" as recommended.  I'll look into it.  By starting at the SourceForge.net home page I couldn't navigate to Gparted.  If anyone could provide the path I'd certainly appreciate it.
  To address the concerns expressed over Windows ME: I have some older programs and hardware that are no longer supported by newer (or different) OS's.  I do not intend to use it for the internet or any other net.
  I'm looking forward to the day that I'll be able to provide such assistance as I received.  Thanks once more.

Jim

What kind of apps? Maybe you could run them via wine? Search for it. I was running the original command and conquer for a while without too many issues. Or better yet try qemu and run Windows in a virtual pc, its pretty darn easy. 

Also in my experience Its best to install windows first then intstal linux. But that was a long time ago, things may have changed

---

