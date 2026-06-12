---
title: "[SOLVED] What GNOME tools are available for burning an iso image to cd"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by mister_lister on 2007-10-10
I have searched the forums and none of the posts I saw dealt with what I am asking specifically.

I am using and installed version UBUNTU 6.06 already and what I want to do is use a GUI tool for GNOME that will burn an image onto a CD from an ISO. I have a Sony CDRW drive.

Please let me know what tools are available that meet the above requirement of being GNOME\GUI based and where and how to get the tool.

I appreciate your help, this is one of the last obstacles in my complete conversion to LINUX from M$ Windows. I don't ever want to use M$ Windows again.

---

### Post by ubuntu27 on 2007-10-10
You can burn an iso by _Right Clicking the iso file and choosing "Burn to CD"_   [Or something similar] 

Yes, that simple :)

If you want more control of it, you can install GnomeBaker which is in the repository. You can isntall by using the terminal or using Synaptic Package Manager. If you want to use the terminal, the command will be:

```
sudo aptitude install gnomebaker
```

**OR**

```
sudo apt-get install gnomebaker
```


GnomeBaker is a program for Gnome that let's you burn different kind of files to CDs or DVDs.

---

### Post by mister_lister on 2007-10-10
I will check into that tonight, thanks a lot, exactly what I was looking for. I will try "gnomebaker" tonight.

---

### Post by Jimmyfj on 2007-10-10
Right click on the downloaded .ISO file and select Write to Disk usually do the trick for me. It has never failed yet.

---

### Post by rscott5 on 2007-10-10
K3b is one of the best burning apps I've come across. It runs on the KDE libraries, but I use it in Gnome and it works great. Definitely worth checking out.

---

### Post by n3tfury on 2007-10-10
> **rscott5 said:**
> K3b is one of the best burning apps I've come across. It runs on the KDE libraries, but I use it in Gnome and it works great. Definitely worth checking out.

i second this.  i use gnome, but k3b is secks.

---

### Post by ubuntu27 on 2007-10-11
Well, practically the following programs that I am listing are the best known CD makers. I am not listing specialized applications such as video generators for DVDs:

**GnomeBaker**, a CD/DVD burning program for Gnome.
 
**[k3b]("http://www.k3b.org/")**, a CD/DVD burning program for KDE. This one is considered the most powerful burning program in GNU/Linux. 

**[Brasero]("http://www.gnome.org/projects/brasero/")** - This programs objective is to do its job as simple and painless as possible.  Good for those who does not need a fancy feature. I believe it is in the repositories. If you need the latest version, you can download a deb package [here]("http://www.getdeb.net/app.php?name=Brasero")


Those three are in the repositories, so just installed them with your favorite install style (Terminal, Add/Remove, Synaptic)

---

### Post by dkaddict on 2007-10-11
I always use Gnome Baker for burning stuff. To burn an ISO with Gnome Baker or K3B you have to click on 'Tools' in the main window then select the 'burn-image-to-disc' option. The ISO burning facility is not listed in the main window burning options categories in either application. Of the two, Gnome Baker consistently gives me succesful burns (easy 90% @ 6x speed) whereas K3B (used in Gnome or KDE) almost always reports an unsuccesful burn (regardless of whether the data has really been burned succesfully) and locks up at the end of the second burn of any given project when I use it which forces me to restart x every time it finishes (how annoying is that). Thus I stick with Gnome Baker. GB just seems to do the do for me. Simpler I reckon!

---

### Post by Caffeine_Junky on 2007-10-11
> **Jimmyfj said:**
> Right click on the downloaded .ISO file and select Write to Disk usually do the trick for me. It has never failed yet.

+1

...for a really simple way to burn an ISO you can not beat this method IMO

..this is one of the features of Ubuntu (feisty) that I really love!

Right-Click ISO > Write to Disc > Set Burn Speed (2x 4x etc..)> Write!   :)

I have burnt more than a dozen ISO's with that method (speed:1x 2x 4x) perfect! every time! ...takes approx' 10 min (on my system).

---

### Post by dkaddict on 2007-10-11
Good call caffeinejunky

> 
Quote:
Originally Posted by Jimmyfj View Post
Right click on the downloaded .ISO file and select Write to Disk usually do the trick for me. It has never failed yet.
+1

...for a really simple way to burn an ISO you can not beat this method IMO

..this is one of the features of Ubuntu (feisty) that I really love!

Right-Click ISO > Write to Disc > Set Burn Speed (2x 4x etc..)> Write!

I have burnt more than a dozen ISO's with that method (speed:1x 2x 4x) perfect! every time! ...takes approx' 10 min (on my system.)

The method you have referred to burns with GnomeBaker without using its front-end or GUI. Gnomebaker minus its GUI is installed in Ubuntu by default (for Feisty and Edgy fafaik). The front end can be downloaded from Synaptic if one prefers that method. Either way uses gnomebaker.

peace

dk

---

### Post by uberMongo on 2007-10-11
Hi there, my first post here.
I'm also converting from M$ to Linux. I'm a noob at this so obviously I have a 1000 questions! Fortunatelly for you guys I'll only ask one this time.

I'm using Feisty Fawn for abou a month and I've only used GnomeBaker to burn my CD/DVD's. And only to use within linux.

What I'd like to know is: are those CD/DVD's readable on windows systems?

For example, if I burn a CD with pictures or office documents will I be able to access it in my windows box? What about ISO files?

ok, ok that was 3 questions! So sue me! I still have 997 questions left :D ;)

Thanks in advance guys!

---

### Post by Lord Illidan on 2007-10-11
Yes, they will still be readable, so don't worry about that. Even iso files. The formatting system used for CD-Rs is cross-platform, not something like ext3

---

### Post by misfitpierce on 2007-10-11
Gnomebaker is prob the best utility ive ever used on any OS

---

### Post by uberMongo on 2007-10-11
Cool! That means that I'm a step closer from stop using windows! YAY!!!

---

### Post by MrKlean on 2007-10-12
There isn't ANYTHING I can do in Windows that I can't do in Ubuntu..FREE  !!!!

---

### Post by Jorge on 2007-10-12
In my experience, Brasero is much better application than Gnomebaker. It gets me less unusable burned CDs. It is related to a restriction on the CD burning speed, I believed, as Brasero acts in a more conservative way and keeps a safer choice for the burning speed.

---

