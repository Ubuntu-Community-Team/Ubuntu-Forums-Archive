---
title: "anti virus?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by TrevorRS on 2007-07-04
whats a good anti virus programme for ubuntu?

Trevor

---

### Post by Nekiruhs on 2007-07-04
You don't need one. Thats it.

---

### Post by TrevorRS on 2007-07-04
lol u sure?

Trevor

---

### Post by Nekiruhs on 2007-07-04
> **TrevorRS said:**
> lol u sure?

Trevor
Absolutely. Linux is way more secure. The only time you'd ever want a virus scanner is if your paranoid about passing on viruses via email to windows users.

---

### Post by smoker on 2007-07-04
there are antivirus apps available, but i've never used one, no need,

but check the repos.

---

### Post by TheRingmaster on 2007-07-04
yes, he is right. Linux (and mac) don't suffer from viruses mainly because linux doesn't make you the admin instead linux gives you temporary rights using sudo.

---

### Post by mig5 on 2007-07-04
Look for clamtk in the repositories, or klamav if you are using the KDE desktop environment or Kubuntu.  Clamtk doesn't have resident protection, ie. it doesn't sit in your tray scanning everything, wheras klamav does if you set it up that way.  Most antivirus programs in Linux are just scanners, so you run them once a week and not all the time.
You can get lots of the common antiviruses for linux, such as avast, AVG and Panda.

---

### Post by Modred on 2007-07-04
I know AVG and Kaspersky both have Linux products, but the latter is definitely targetted more toward corporations.  Makes sense, considering that corporations are more likely targets for deliberate attacks than home computers.

While the others aren't completely accurate to say Linux (or BSD, or OS X) don't get viruses, the viruses that exist for these systems are usually not encountered by normal users.  This could change in the immediate future, all it takes is one person to write a little contagious bug that works for a non-Windows systems and we'll all be scrampbling for antivrus.

---

### Post by John.Michael.Kane on 2007-07-04
Have a read [ Are firestarter and clamav really necessary ??]("http://ubuntuforums.org/showthread.php?t=131616")

[AntiVirus]("http://ubuntuforums.org/showthread.php?t=123230&highlight=anti")

[AntiVirus2]("http://ubuntuforums.org/showthread.php?t=5875&highlight=anti")

Theres many views on this topic.

---

### Post by cogadh on 2007-07-04
I've posted this numerous times already, but it is worth saying again. There have only been 14 viruses and 9 worms for Linux since 1991. None of those viruses or worms have ever been able to propagate due to the inherent security of Linux and none of them are a threat anymore (kernel and software updates have eliminated the holes they exploited)

Compare that to Windows which had over 103,000 different viruses and worms before 2005 and you'll understand why most people feel antivirus software for the purposes of protecting a Linux system is really unnecessary.

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms)
[http://en.wikipedia.org/wiki/List_of_computer_viruses](http://en.wikipedia.org/wiki/List_of_computer_viruses)

---

### Post by gn2 on 2007-07-04
> **TrevorRS said:**
> whats a good anti virus programme for ubuntu?

Trevor

No such thing, they're all pretty poor. And totally not required.

---

### Post by lisati on 2007-07-04
> **TheRingmaster said:**
> yes, he is right. Linux (and mac) don't suffer from viruses mainly because linux doesn't make you the admin instead linux gives you temporary rights using sudo.
As well as this, there's always the option of being smart - for example: if in doubt about an incoming email, don't open it, and make sure you have a means of recovering important data, just in case (which also applies when checking out new software)

---

### Post by SirGrant on 2007-07-04
I'm just curious any slightly diverting the thread off topic but what if you were running ubuntu server and hosting windows files via samba.  Would you want a virus scanner like avast running, not so much because it threatened the security of your ubuntu server but more because it could detect potential windows viruses and prevent them from spreading to any windows machines you happened to have accessing the server?

---

### Post by Wiebelhaus on 2007-07-04
> **TrevorRS said:**
> whats a good anti virus programme for ubuntu?

Trevor

but if you want to scan windows drives or emails , Bit Defender is by far the best IMO.

---

### Post by cogadh on 2007-07-04
> **SirGrant said:**
> I'm just curious any slightly diverting the thread off topic but what if you were running ubuntu server and hosting windows files via samba.  Would you want a virus scanner like avast running, not so much because it threatened the security of your ubuntu server but more because it could detect potential windows viruses and prevent them from spreading to any windows machines you happened to have accessing the server?
Yes, that is the only real reason to run antivirus on Linux.

---

