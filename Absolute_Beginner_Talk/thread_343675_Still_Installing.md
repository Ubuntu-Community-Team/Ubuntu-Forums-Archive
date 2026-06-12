---
title: "Still Installing"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by evolving on 2007-01-21
Not having much luck at all.  Finally got down to installing and now I don't get this message anymore:

[IMG]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=6.png[/IMG]


Now I got a screen that gives me a choice of erasing the entire disk, manually creating the partitions or letting the partition program find free space and create the partition.

What am I doing wrong?

---

### Post by jpeddicord on 2007-01-21
What do you want to do with your PC? Do you have Windows currently and want to dual-boot it? If so, the first option (resize + free space) should work for you.

Jacob

---

### Post by evolving on 2007-01-21
Yes, I have Windows XP and want to dual boot.  However, when I try to install, I am no longer getting the resize option, just erase entire disk; use feed space but with no mention of resize or manual.

---

### Post by jpeddicord on 2007-01-21
It doesn't even give you the Manual option? That is strange. If you haven't restarted the CD and tried the installer again, it may work. Sometimes bugs like those are worked out through a restart.

Which version are you trying to install: 6.06 Dapper or 6.10 Edgy?

:)

---

### Post by ComplexNumber on 2007-01-21
select "Manually edit partition table". you will be given the option to resize etc on the next page.

---

### Post by evolving on 2007-01-21
I am using Dapper or, should I say, trying to use Dapper.  It does give the manual option; however, I am so new to Linux I am hesitant to use it.  It would be easy enough if it just wanted me to manually re-size the windows partition but it asked for more information than I understood.

I have re-started a number of times and am still in this situation.

Also, there are errors when the live cd boots...not everything can be loaded like hc or hw_random.    Is this normal?Thanks for your help.

---

### Post by jpeddicord on 2007-01-21
For manual partitioning, you need to do these steps:
[LIST=1]
[*]Resize the Windows partition down to leave some space for Ubuntu
[*]Add a partition of about 2 GB, and select 'linux-swap' for the filesystem
[*]Add another partition to fill up the rest of the drive, and make the filesystem Ext3.
[*]Click Apply, then confirm to immediately apply the changes. It may take 3 to 5 minutes to run. Make sure you have backups in case something goes wrong.[/LIST]

As for the hw_random error, I used to get this occasionally. I don't believe it has been a problem.

---

### Post by BCRailrodder on 2007-01-21
Hopefully this problem has already been solved.  However, I have had a similar problem when I was installing Edgy on my laptop.  It didn't matter what I did, I could not get the NTSF partition to resize.  After checking out some other posts, I downloaded Qtparted and used that to resize the partition.  I then went back to the install disk and finished the installation.

You can find Qtparted at [http://qtparted.sourceforge.net/](http://qtparted.sourceforge.net/) .

I would try the other suggestions first and use this more as a last resort.

Kent

---

