---
title: "Question KDE/GNOME"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-11-24
Hi,

I have been using Kubuntu for a long time now. But I have found out that whenever I try to install a GNOME based program it doesnt work properly. For example, I installed gparted initially through Adept and when I opened it, I couldnt do anything, ie I was not given the option to move or resize a partition. I opened konsole and used made sure I opened it as root. Then I went to gparted website and downloaded the source and compiled it. Again I opened it as root and again it was the same case as before. What I want to clarify is, will GNOME apps ever work without any problems in KDE or not? Because if they dont then I dont need to waste time trying to get them to work.. I could just find a KDE alternative.

Thanks.

---

### Post by kellemes on 2007-11-24
> **linuxnovice said:**
> Hi,

I have been using Kubuntu for a long time now. But I have found out that whenever I try to install a GNOME based program it doesnt work properly. For example, I installed gparted initially through Adept and when I opened it, I couldnt do anything, ie I was not given the option to move or resize a partition. I opened konsole and used made sure I opened it as root. Then I went to gparted website and downloaded the source and compiled it. Again I opened it as root and again it was the same case as before. What I want to clarify is, will GNOME apps ever work without any problems in KDE or not? Because if they dont then I dont need to waste time trying to get them to work.. I could just find a KDE alternative.

Thanks.

I never have trouble with GTK-based packages on KDE..
Maybe you should try to load a another GTK-app from the console and watch the output.. this may be informative.

---

### Post by qpieus on 2007-11-24
Gnome apps work fine in kde. The issue you're seeing with gparted is that it won't let you do anything because your various disk drives are mounted. Gparted will not allow you to operate on mounted drives, even as root. If you want to perform operations on a drive, you need to unmount it first, then gparted should allow you to do stuff. That being said, I haven't had a lot of luck using gparted while in my nornal gui interface (i.e. logged in normally). I've had a lot of success running gparted from the gparted livecd (google for it). The live cd works very well because it does not mount anything as it boots, so you can then do whatever you want to your drives.

---

### Post by aysiu on 2007-11-24
Maybe make sure you have *gksu* installed?

---

### Post by linuxnovice on 2007-11-24
Thanks for the reply. I have used gparted live cd before. But I left that CD in my lab for a friend. Will qparted give me the same results? If I unmount a partition, what is going to happen? Will I not be able to use it?

---

### Post by aysiu on 2007-11-24
> **linuxnovice said:**
> Thanks for the reply. I have used gparted live cd before. But I left that CD in my lab for a friend. Will qparted give me the same results? If I unmount a partition, what is going to happen? Will I not be able to use it?
QTParted should give you the same results, but, yes, you will not be able to use an unmounted partition.

It needs to be unmounted, though, in order for you to resize it or repartition it.

---

### Post by linuxnovice on 2007-11-24
Thanks,
I found a copy of sysrescd which contains gparted and all the other good stuff. I have a question. I want to upgrade to Gutsy and everywhere I see people suggest on doing a clean install as opposed to an upgrade. I am going to take that advice. I have separate /home partition. What I plan to do is use partimage to create an image of the my entire /home compress it and store in another backup partition. Then install Gutsy and then restore my /home partition and merge the backup partition back with my /home. WIll this work? Or is there an easier work around? I dont want to burn any dvd's although I have plenty of hardisk space. So if there there is an easier way to backup my stuff I would like to know it.

Thanks.

---

### Post by nhandler on 2007-11-24
Well, when you are installing gutsy, you can tell it to not format your /home partition and specidify that it should be mounted as /home. This will keep you from having to back it up. Just make sure to format that partition that has the actual ubuntu installation on it.

---

### Post by linuxnovice on 2007-11-24
> **Cheater said:**
> Well, when you are installing gutsy, you can tell it to not format your /home partition and specidify that it should be mounted as /home. This will keep you from having to back it up. Just make sure to format that partition that has the actual ubuntu installation on it.

Thanks,
I am guessing that this would be the root partition?

---

