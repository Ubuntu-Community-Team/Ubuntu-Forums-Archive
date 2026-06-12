---
title: "lost windows?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Wletnzft on 2008-01-24
I've gone a stupid mistake that I'm sure many before me has done too..

I felt like trying out Linux, and now I fear I have actually lost Vista. I'm sure that it is my mistake though, I'm not especially proficient when it comes to computing...

Anyways, I have a few questions. Thanks in advance to anyone kind enough to answer, it is really appreciated as I feel like a major *** right now...


1) Is there any way for sure to know that I have actually 'deleted' my old OS?
2) Can I somehow access its old files, or are they gone forever?
3) If it is gone, how can I restore it? (I had Windows Vista, but got no installation CD)

Answers are really appreciated, thanks for taking the time too read through the frantic words of someone who deserves what he got...

:I

---

### Post by taurus on 2008-01-24
Open a terminal and see what happens to your harddrive?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L.

---

### Post by Wletnzft on 2008-01-24
This is what I got:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44f15d12

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

means it is lost forever, doesn't it?

---

### Post by secondstage on 2008-01-24
nothing
(i screwed up on this post)

---

### Post by taurus on 2008-01-24
> **Wletnzft said:**
> This is what I got:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44f15d12

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

means it is lost forever, doesn't it?

I guess when you installed it, you told the installer to use the whole drive!  #-o

---

### Post by secondstage on 2008-01-24
"Device Boot Start End Blocks Id System
/dev/sda1 * 1 18701 150215751 83 Linux
/dev/sda2 18702 19457 6072570 5 Extended
/dev/sda5 18702 19457 6072538+ 82 Linux swap / Solaris"
means that you don't have the partitions for Vista, so sadly you did remove vista :( sorry

But when I first installed Ubuntu, there was an icon on the desktop that said "sda1"(might not be in solaris). That got me to the whole drive and through that you can get to your windows files. I don't know if this will be the same for vista (i have xp)

---

### Post by taurus on 2008-01-24
> **secondstage said:**
> Like that will help any^^^( don't try it )

Don't try what?

---

### Post by secondstage on 2008-01-24
i thought that the fdisk part of that command would format the whole disk (it does in windows command prompt) 

newb idea my bad

---

### Post by smurphy_it on 2008-01-24
You used the whole disk and wiped out the partition with MS Windows Vista on it.  Some utilities out there can still recover files, but I can't think of any Linux ones at the moment.

As for the comment about fdisk and don't do it .... The fdisk -l command doesn't do anything other than display all of the partitions on the active hard drive.

It is good to question these things before trying them!

---

### Post by seventhc on 2008-01-24
> **secondstage said:**
> i thought that the fdisk part of that command would format the whole disk (it does in windows command prompt) 

newb idea my bad
you can use fdisk in windows without formatting, just to check partition information, you have to tell it to format it to actually format. :)

---

### Post by Wletnzft on 2008-01-24
Thank you very much for the fast replies :)

I guess Vista really is lost then...meh.

So, anyone knows how to restore it (without the CD, that i didn't get with the comp)
or should i continue to use linux?

---

### Post by seventhc on 2008-01-24
I think you need the disk to install vista, normally a computer will either come with the disk or if not, let you create a back up which basically restores the computer back to factory defaults. 'The way it was the day you got it.' I'd stick with linux, I had a new comp made the back ups then removed vista entirely. Had it on less than 7 hours before it was gone. ;)
It might seem difficult at first but there are plenty of people here willing to help. :) Once you get used to it, you'll forget all about windows. :D

---

### Post by Mze on 2008-01-24
I keep reading new posts about new users hosing their VISTA machines. 

How do the developers fix this in subsequent versions?

Are the users failing to read correctly the instructions? 

Should a RED popup window be implemented to joggle their memory at partitioning?

Or should the users be redirected to a webpage to read up before the LIVE CD installs?

Any solutions how to reduce these type of scenarios to the bare minimum?

---

### Post by seventhc on 2008-01-24
> **Mze said:**
> I keep reading new posts about new users hosing their VISTA machines. 

How do the developers fix this in subsequent versions?

Are the users failing to read correctly the instructions? 

Should a RED popup window be implemented to joggle their memory at partitioning?

Or should the users be redirected to a webpage to read up before the LIVE CD installs?

Any solutions how to reduce these type of scenarios to the bare minimum?
It is from not reading the instructions correctly, to have a dual boot you would have to have a separate partition which you can resize the vista partition from vista, or from the live cd of ubuntu. Then during the install you have to read the options presented to you, 1 option will install on entire drive(I think thats what you chose) or you choose the option to install ubuntu on remaining free space. This option will install ubuntu next to your windows partition and create a dual boot menu to choose from during boot up.
There really is really nothing for the developers to fix about this.
As for reading up on the installation method I highly recommend it, they have complete instructions for dual booting. But sometimes learning the hard way even though it might be bad, it is something you'll never forget and believe me, I have learned the hard way with lots of things so don't feel bad.
Since you have ubuntu installed, why not try to learn it you can already see in this forum there are plenty of people willing to help. Most of your questions will probably be answered fairly quickly to, just try not to get frustrated b/c it is different than windows but also more stable and more secure.

---

