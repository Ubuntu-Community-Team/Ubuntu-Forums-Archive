---
title: "format for dual boot?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by pax.discordia on 2006-10-11
hello,
i've been having a number of problems with my computer, and after pretty much driving myself crazy and trying everything i can think of i've decided to try re-installing windows and starting all over again - but i figured that while i'm at it i'll give ubuntu a try. 

so, i have a couple of questions:

1) i have two hard drives - a 20 gb and a 120 gb. to install both xp and ubuntu, what would be the best way of setting up the partitions? which format should i use? it would be useful if i could access files on the hd from both operating systems, but not necessary.

2) i have about 60 or so gb of stuff that i'd like to keep (work, music etc), so where should that go?

3) the version of ubuntu i downloaded says it's the athlon 64 version - i have a barton 2500 (32 bit), so will the 64 version work? 

thank you very much,

rs

---

### Post by StormNet on 2006-10-11
Alright lets tackle the questions one at a time.

> i have two hard drives - a 20 gb and a 120 gb. to install both xp and ubuntu, what would be the best way of setting up the partitions? which format should i use? it would be useful if i could access files on the hd from both operating systems, but not necessary.

i have about 20 or so gb of stuff that i'd like to keep (work, music etc), so where should that go?
What i have done in my situation, since i want to have access to files in both operating systems (XP and Linux) I have made a partition where i store all my Datafiles, so my current drive looks like this:

hda1 Windows XP        NTFS
hda2 Data              FAT32
hda3 swap              swap
hda4 Linux             ext3

in order mount the Data partition i added this to my fstab file (/ect/fstab)

> [COLOR="Blue"]/dev/hda2       /mnt/Data      vfat     umask=0000   0  0[/COLOR]
This allows me to access the drive through a folder placed at /mnt/Data. It gives me access to the datafiles and allows me to read and write to FAT32. There is an NTFS driver to write to NTFS partitions, but as far as i am aware it is not always stable. A friend of mine has gone the other way and installed a driver for XP that in order to read and write to ext2 partitions.

> the version of ubuntu i downloaded says it's the athlon 64 version - i have a barton 2500 (32 bit), so will the 64 version work?
You will have to download the 32bit version since the 64bit version has code specifically designed to take advantage of that architecture. It wont work with you current CPU. Download the x86 version. Like the one at this link:

[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-i386.iso]("http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-i386.iso")

I will be trying out the ext2 driver for XP in the next little while to see how stable it to read and write to ext2 partitions.

Hope that helps.

---

### Post by Frak on 2006-10-11
Trust me I've tried it 64 bit will NOT WORK with a 32 bit processor, different?

---

### Post by Frak on 2006-10-11
Great explanation StormNet! You said it all.

---

### Post by gn2 on 2006-10-11
You could always try this method:

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)
.

---

### Post by paulius2003 on 2006-10-11
> **pax.discordia said:**
> hello,
i've been having a number of problems with my computer, and after pretty much driving myself crazy and trying everything i can think of i've decided to try re-installing windows and starting all over again - but i figured that while i'm at it i'll give ubuntu a try. 

so, i have a couple of questions:

1) i have two hard drives - a 20 gb and a 120 gb. to install both xp and ubuntu, what would be the best way of setting up the partitions? which format should i use? it would be useful if i could access files on the hd from both operating systems, but not necessary.

2) i have about 60 or so gb of stuff that i'd like to keep (work, music etc), so where should that go?

3) the version of ubuntu i downloaded says it's the athlon 64 version - i have a barton 2500 (32 bit), so will the 64 version work? 

thank you very much,

rs


Here is how I would go about that.

1) Primary 40gb Partition - Windows XP NTFS
* This is assuming that Windows will be your main OS to use, and you are just using Ubuntu to experiment.
2) 60gb Extended Partition
*This will let you create 1 60gb Logical or 2 30gb Logical drives, where you can store your stuff and whatever.  Use NTFS, because FAT32 is slower and less secure, and I don't think it recognizes volumes more than 6gb (Altho I am not 100% sure of it).
3) 20gb Logical Partition - Ubuntu ext3
*20gb is plenty, I doubt you are going to do any hardcore gaming or anything. My Ubuntu is only 10gb.

You are going to have some left over space for other stuff. You can convert to dynamic disk and increase volumes, but be careful with that, it may corrupt data.

---

### Post by pax.discordia on 2006-10-12
thank you very much - i'll give that a try :)

rs

---

### Post by Vorian on 2006-10-12
Just a side note...  With windows, set up a swap for your page file.  I use it as drive z.  Sound like your in for a fun night

---

### Post by lapsey on 2006-10-12
> **Vorian said:**
> Just a side note...  With windows, set up a swap for your page file.  I use it as drive z.  Sound like your in for a fun night

this is a bad idea and actually makes windows operate slower

---

### Post by pax.discordia on 2006-10-14
what do you mean swap for the page file? i know what the page file is, but swap? 

yeah, definitely going to be an interesting night...
thanks,
rs

---

### Post by randiroo76073 on 2006-10-15
I'd use fat 32 for data as Ubuntu read/writes it natively so no hassle with third party prgm, and, it will go to 128gb, 4gb on file trasfers :)
AFAIK XP doesn't need separate swap/page partition

---

