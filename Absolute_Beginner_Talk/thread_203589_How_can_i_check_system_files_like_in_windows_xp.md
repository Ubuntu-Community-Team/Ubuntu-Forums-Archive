---
title: "How can i check system files like in windows xp?"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by theduke11 on 2006-06-25
You know check for bad system files?

Thanks.

---

### Post by bscbrit on 2006-06-25
I'm not quite sure that I know what you mean...  Why do you need to 'check' your system files?  Is something not working?

You do not need to defrag the disk - it is simply not necessary.

Which files do you mean when you say 'system files'?  The entire concept of files, what they do, and how they are displayed is very different under Linux than it is under Windows but until you tell me exactly what you are trying to achieve I cannot give you any help.

---

### Post by theduke11 on 2006-06-25
Hi, I mean the files you know that makes ubuntu run? to check if any files are courrpted? im worried my cd drive didnt burn it right. I checked the m5msums or whatever on the ISO and all is well but ive had problems with burning stuff on this CD drive in the past. In other words I just would like to know if all the files installed correctly?

Thanks.

---

### Post by raptros-v76 on 2006-06-25
when you start up the live cd, there is an option to have the cd check itself for problems

---

### Post by theduke11 on 2006-06-25
Yes I also ran that and it found no problems so im ok? im asking because ive burned many ubuntu cd's and they all dont have the same speed. They all can load the install faster or slower.

---

### Post by raptros-v76 on 2006-06-25
if the disk check came up with no errors, your fine

---

### Post by bscbrit on 2006-06-25
In short, there isn't an easy way but, if you have a few days to waste, then it can be done.  But perhaps there is an easier way to answer your question.

You appear to be unsure if your installation is correct or working properly.  As long as it does what you want then it is working.  You could spend days trying to check if every file is the same as the original in the repository but even that wouldn't guarantee you a working system.  A problem might be caused by a configuration error, or simply be a piece of hardware that is incompatible.

If your software installed without error, and you are happy that it is working, then you needn't worry about each individual binary file.  But, to give you peace of mind, open synaptic (System -> Administration -> Synaptic Package Manager) and then look at the very bottom line.  It will tell you how many packages are installed, how many are broken and how many are awaiting update or removal.  If there are none broken and your computer is working, then there is nothing wrong.

If you had a problem installing Ubuntu from a CD that you burnt yourself then you probably used too high a write speed for the CD write.  Nowadays, people think that waiting 10 minutes is a loss of 10 minutes of their life, but burning a CD at a low speed is always time well invested.  I burn all my CDs at around x10, although the CDs are rated much higher.  **But** I do not waste anyCDs by incorrect burns and my software tends to install first time, every time.  I suppose the 10 minute wait for the longer burn has saved me hours in installation time.

In Windows, you might have had to check that all of your files were correctly installed.  With Linux, just sit back and enjoy the experience.  If something doesn't work then come back with a question but life is much too short to worry about things that 'might' be wrong but that you cannot even detect.

I'm sure that others have their own opinions.  I just find using Linux, and especially Ubuntu, a pleasure.  Of course, in the early days I cursed the fact that it wasn't the same as Windows, that **I** didn't know what to do, that **I** had to come here and ask questions but it was all well worth it. :-D

---

### Post by theduke11 on 2006-06-25
bscbrit, thanks for that.

---

### Post by bscbrit on 2006-06-25
You're welcome.  See you around...

---

### Post by mlind on 2006-06-25
Use fsck as chkdsk replacement. For default, your linux partitions will be checked between 30 mounts automatically.

Use *df* or *sudo fdisk* to see the partition table.

My /boot is **/dev/hda2**, if I'd wanted to force check on it on next boot, 
I would raise "Mount count"  to one lower than "Maximum mount count".

To see the attributes, I would do
```

sudo tune2fs -l /dev/hda2

```

To modify mount count, so checking triggers on next reboot
```

sudo tune2fs -C 29 /dev/hda2

```

_Read tune2fs man page carefully before doing so though_.

---

