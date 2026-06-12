---
title: "My girlfriend does not like Ubuntu."
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by phattpuud on 2006-09-10
I have recently aquired Ubuntu 6.06.  I have had it for about a week now.  I have been doing a lot of reading, but I have not been able to find what I am looking for.  Is there any way to add Windows and create a dual boot enviroment?  Please Help.

---

### Post by coastdweller on 2006-09-10
> **phattpuud said:**
> My girlfriend does not like Ubuntu

Welp, only one thing to do, get a new girlfriend.

---

### Post by az on 2006-09-10
Since windows does not play well with other OSes, it is easier to install Windows first, and then install Ubuntu.

You can resize your partition, move it to the end of your drive and then install ubuntu on the free space at the beginning.

Then, boot the live dc, chroot into your ubuntu install and re-install grub.

But it's complicated.

---

### Post by goatmale on 2006-09-10
buy her a computer,

---

### Post by Najand on 2006-09-10
Step 1.Resize your partitions, if you have no free partitions
Step 2.install Windows on a free partition (Resized Patition)
Step 3.Because Windows Overwrite MBR, grub cannot boot... So  just see  the foloowing document in Ubuntu WIKI to recover Grub.
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28Recover%29]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28Recover%29")

---

### Post by alcamus on 2006-09-10
For what it's worth, here's my advice:

Download the [GParted Live CD]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") and burn the .iso to a CD. Make sure your machine is set to boot from a CD and boot GParted. You'll then be able to erase your entire hard drive and set up part of it as a Windows partition (for the sake of argument, I'll use Windows XP as my example OS).

Install Windows to the new partition, being sure you download all patches, plug security holes, grab a good virus scanner and get an adware program (or two to be absolutely safe). Install your girlfriend's favorite programs.

When you're done there (it shouldn't take longer than a couple of hours or so), reboot your computer using the Ubuntu CD. Double-click the install icon and answer about six questions from an installation program. When it asks how to partition your hard drive, tell it to use the largest continuous free space and let it set up its defaults.

After that it's up to you. I always grab Automatix and install the drivers for .mp3s and stuff to kick-start the installation, but that's a personal preference.

Dual boot and live in harmony with the girlfriend.

---

### Post by jpkotta on 2006-09-10
Get VMware server (it's free as in no cost) and install Windows as a virtual machine.

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

---

### Post by phattpuud on 2006-09-10
I would like to thank everyone for their help.  I greatly appreciate it.:-D

---

### Post by Peter41az on 2006-09-10
to the one who said get a new girlfriend, LMAO. i was thinking same thing :)

---

### Post by GonZo1323 on 2006-09-10
wow VMware looks nice

---

### Post by simonn on 2006-09-11
> **phattpuud said:**
> My girlfriend does not like Ubuntu.

[i]<removed>

[size=1]That joke is uncalled for[/i] - Artificial Intelligence[/size]

---

### Post by H3HI on 2006-09-11
install the winxp first, and install the ubuntu after that.

the grub will be detect all the os which in the HD.


and the last advise, why not change a girlfriend who likes linux :P

---

### Post by bluenova on 2006-09-11
My girlfirend loves Ubuntu (Gnome), I suggested she checked out KDE the other day, and she said no way you can't take away my gnome!

You could always run windows in VMWare:
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

But I find with ....non-techinical minded people.. that the content is more important than the O/s, as long as they can do what they need to do then they are happy.

---

### Post by Peter41az on 2006-09-11
seriously, yes, you are correct in saying install windows first.try and install windows last and it turns into a bigggg mess.  Personally, i havent run windows on my own computer since mandrake 7.1 came out ive never owned a copy of windows XP in my life ,But if you must... :)
KDE is a nice desktop. i have nothing against gnome, but i use it for the same reason i have a  younger wife this time: a little eye candy never hurt anyone! My mom is 62 and runs Ubuntu Edgy now. i load all the alphas on hers so if it blows up, its not mine haha :)

---

### Post by mdsmedia on 2006-09-11
> **phattpuud said:**
> I have recently aquired Ubuntu 6.06.  I have had it for about a week now.  I have been doing a lot of reading, but I have not been able to find what I am looking for.  Is there any way to add Windows and create a dual boot enviroment?  Please Help.The simple answer is YES. I'm effectively a Linux newbie and I got sick of XP's problems. I searched these forums and found a HowTo and installed a dual-boot Ubuntu with XP.

I now use Ubuntu as my main Operating System but have kept XP for a couple of programs I have to use...and I hate having to boot into XP to use them because I love Ubuntu/Linux and hate Windows/XP.

There are a number of threads on these forums on how to dual-boot Ubuntu with Windows. I'll have a look and find a link for you, but the simple answer is YES. It's easy to have the 2 running side by side.

---

### Post by Sef on 2006-09-11
For [Dual Booting]("http://users.bigpond.net.au/hermanzone/"), just read this by Herman.

---

### Post by insane_alien on 2006-09-11
well, if you don't want to lose your gf and you want to keep ubuntu, hypnosis would be a nice field of study for you to take up.

---

### Post by mdsmedia on 2006-09-11
> **Sef said:**
> For [Dual Booting]("http://users.bigpond.net.au/hermanzone/"), just read this by Herman.Thanks Sef, that's the link I was looking for.

---

### Post by dabuntu721 on 2006-09-11
Your girlfriend need more patience like ubuntu

---

### Post by Najand on 2006-09-11
Well, I think we are commenting here to solve his problem not to give our opinions about his girlfriend. So better to stop it please.

---

