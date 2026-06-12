---
title: "XP and Ubuntu in a desktop"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by ashikuzzaman on 2007-05-11
Hi folks,

I am not an expert user of Linux but have worked with Debian and Red Hat a little. I need to play around with various tools available online and also practice basic linux commands. So instead of doing it in my laptop provided by my office, this week I purchased a used desktop P4 2.8 Ghz, 512 MB RAM and 40GB HDD with an LCD monitor and CD drive. It has WinXP already installed. However, my main purpose will be to get more familiar with Ubuntu and hence I requested for Ubuntu 7.04 CD/DVD which should arrive me end of this month.

I would like to know if this configuration will be smooth enough to dual boot XP with Ubuntu 7.04 and any instruction available to do so. I am okay to purchase few additional things (say HDD or RAM) if I need. My general understanding is running the installer CD will give me wizards to follow and my 40 GB HDD should be enough to host this 2 O/S. After installation of Ubuntu, GRUB will be used as boot loader and ask me if I want to log into Windows XP or Ubuntu. Do I need to know more or am I missing something?

---

### Post by Seisen on 2007-05-11
You have plenty of ram unless you are going to use some hardcore linux apps or use Wine a lot.

---

### Post by xthund3rh3adx on 2007-05-11
there should be no problem dual-booting XP and Ubuntu. If you know waht to do, you will be fine ;). Make seperate partitions and all that and youll be fine :)

---

### Post by KIAaze on 2007-05-11
I think you're good to go.

I assume you know that you have to defragment the windows partition first and backup important data just in case?

---

### Post by ashikuzzaman on 2007-05-11
Thank you all so much for the responses.

> I assume you know that you have to defragment the windows partition first and backup important data just in case?

I dont have any data so am free of backup thought. But I didn't know that I have to defrag. Would you please hint me why defragmentation is needed? Currently there is only a C:\ which I plan to partition in 2 20GB drives and load Ubuntu in D:\

Any free/light-weight partitioning tool can you suggest or I should be able to do it with XP's System Tools?

---

### Post by stevebakerj on 2007-05-11
I would wait and do it with the Live CD when it arrives.

---

### Post by xthund3rh3adx on 2007-05-11
you should defragment your drive with a defrag tool in XP

go to Control Panel>Performance and Matenaince>Rearrange items on your hard drive to make apps run faster

then, click "Defrag" on the window that appears. Shouldnt be much, maybe 10 minutes. 

THe reason to to this is so nothing gets overridden when you install Ubuntu, and more free space is availabie for it

---

### Post by KIAaze on 2007-05-11
You can defragment using the windows defragmenter.
If your windows XP installation is completely new, you shouldn't have any problems.

In case of problems:
-If you are unable to free enough space at the end of the disk (because that's all you really need, it doesn't matter if there are some fragmented files at the start of the disk):
[http://howtoprimers.com/techtalk/2006/02/moving-the-unmovable-windows-disk-defragmentation-strategies/]("http://howtoprimers.com/techtalk/2006/02/moving-the-unmovable-windows-disk-defragmentation-strategies/")

-Some people have also reported that they had to run scandisk to fix some disk errors first.

---

### Post by davahmet on 2007-05-11
Because of the way that Windows typically writes back to the disk during normal operations, it tends to scatter bits of files all over the hard drive, hence the filesystem becomes fragmented.  The reason for defragging before installing a dual boot system is so your Windows files get relocated into a single large cluster near the beginning of the drive geometry.

With a new system, this is most likley not a necessary step.

---

### Post by ashikuzzaman on 2007-05-11
Thanks again for the wonderful responses. One last but important question I would like to ask you.

Should I install Ubuntu Desktop or Server edition? On high-level view what important stuffs would I miss in Ubuntu Desktop that the server edition woudl give me?

I will mostly use Ubuntu to ripe my hands on basic linux commands, java swt and webapps, CVS, bugzilla installations, apache web server and PHP/Jython scripting as well as using portable apps suite.

---

### Post by louieb on 2007-05-11
> **ashikuzzaman said:**
> Should I install Ubuntu Desktop or Server edition? On high-level view what important stuffs would I miss in Ubuntu Desktop that the server edition woudl give me?
Just my two cents.  The learning curve for the command line only is pretty steep. Its real nice to have a browser open to some how to site  and a terminal window open to try out the commands  Get the desktop. 
One of the first things to learn is how to add and update software. There is nothing in the server edition that can't be added to the desktop edition. 
and vice versa nothing in the desktop edition that can't be added to the server edition.

---

### Post by ashikuzzaman on 2007-05-11
Great feedback. I will go for the desktop edition then. Whenever I need anything I will add up later. This forum is so active and helpful, its quite unbelievable to me. Thanks folks. :)

---

