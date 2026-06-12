---
title: "Ubuntu on vista computer"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by freerid3 on 2008-04-18
Hi! Here comes a total n00b question:
 I'm currently running Vista home basic :( on my computer I want to install Kubuntu. If i move all my files to an external hdd, terminate Windows and then install Kubuntu. Will Kubuntu be able to read the pictures, mp3's and movies from the external hdd? 

Forehand thanks!

---

### Post by SunnyRabbiera on 2008-04-18
it should, what kind of external is it?

---

### Post by freerid3 on 2008-04-18
haven't purchased it yet.. So I don't know :P

---

### Post by SunnyRabbiera on 2008-04-18
ah, what external are you thinking of investing in?

---

### Post by warbread on 2008-04-18
Unless something goes horribly wrong, yes.  Ubuntu has NTFS read/write support.  
Be aware that you'll have to enable some file types, like .mp3, which are not included in a default Ubuntu installation for legal reasons.

See [UbuntuGuide ]("http://www.ubuntuguide.org")for more information.

---

### Post by freerid3 on 2008-04-18
ok. But formats like divX and avi shouldn't reak havoc? :P is there an easy way to convert mp3s into for instance ogg?

---

### Post by SunnyRabbiera on 2008-04-18
> **freerid3 said:**
> ok. But formats like divX and avi shouldn't reak havoc? :P is there an easy way to convert mp3s into for instance ogg?

they shouldn't, beside you can get what you need rather easily anyway...
dixX might be troublesome though but I do not speak from experience.
However if you are worried about all your stuff working right away when you install linux you may want another distrobution.
Give Linux Mint a shot or if you dont like gnome you can try Mepis, both have very good media support out of the box.

---

### Post by rogirwin on 2008-04-18
Any USB drive should be compatible.Seagate FreeAgent drives work pretty well.

---

### Post by warbread on 2008-04-18
Soundconverter is convenient.  It's in the repos.

I don't have much experience with video formats, but I don't think I've ever had to enable .avi or divx formats.

---

### Post by SunnyRabbiera on 2008-04-18
> **rogirwin said:**
> Any USB drive should be compatible.Seagate FreeAgent drives work pretty well.

well mainly seagate as WD has horrible linux support.
I am not sure about others either such as toshiba.

---

### Post by bumanie on 2008-04-18
> **rogirwin said:**
> Any USB drive should be compatible.Seagate FreeAgent drives work pretty well. You're very lucky if your free agent works well with ubuntu, there are multiple reports of problems with them and ubuntu. Personally I'd buy an enclosure and put a spare drive in it (that is, if you have a spare drive around of course).

---

### Post by tonyp1969 on 2008-04-18
> **freerid3 said:**
> Hi! Here comes a total n00b question:
 I'm currently running Vista home basic :( on my computer I want to install Kubuntu. If i move all my files to an external hdd, terminate Windows and then install Kubuntu. Will Kubuntu be able to read the pictures, mp3's and movies from the external hdd? 

Forehand thanks!

Why don't you download and install Virtual PC 2007 and install Ubuntu as a Virtual PC? That is what i have done on my machine, I use Ubuntu for all the important stuff and switch to Vista when I want a toy.

---

### Post by rogirwin on 2008-04-18
I was going to ask how much RAM you have but I can see the answer.....

Surely there are major speed issues doing it that way.

I have it the other way round. Installed Linux and run VMWare for Windows when needed.

---

### Post by tonyp1969 on 2008-04-18
Speed problems? You have got to be joking, Both OS's run like a dream and I was even playing Fifa 08  with no lag on the Vista earlier even with Ubuntu running. Either way should be fine though.

---

### Post by rogirwin on 2008-04-18
> **bumanie said:**
> You're very lucky if your free agent works well with ubuntu, there are multiple reports of problems with them and ubuntu. Personally I'd buy an enclosure and put a spare drive in it (that is, if you have a spare drive around of course).

I haven't used it much with Ubuntu but it has been plugged in and works fine. The only problem I found with linux is they go to sleep if left unused for any length of time. Ubuntu may not wake it up... haven't tested.

---

### Post by freerid3 on 2008-04-18
Ok! I've tried Gnome a little earlier and I think it's ok. Thanks a lot for all the great answers! I have no reason  to regret joining this forum! :D

---

### Post by maniac_X on 2008-04-18
> **SunnyRabbiera said:**
> ...as WD has horrible linux support.

I'm curious about this. In what way are WD drive that much different than Seagate, etc? 

I currently have some WD drives that are about 10 years old that work fine in Ubuntu. I also have other WD drives, one of which is a Raptor. No problems have yet to be encountered.

---

### Post by SunnyRabbiera on 2008-04-18
> **maniac_X said:**
> I'm curious about this. In what way are WD drive that much different than Seagate, etc? 

I currently have some WD drives that are about 10 years old that work fine in Ubuntu. I also have other WD drives, one of which is a Raptor. No problems have yet to be encountered.

I am talking about newer WD external drives, people have better luck with seagates in comparison

---

### Post by andylyon11 on 2008-04-18
> **SunnyRabbiera said:**
> well mainly seagate as WD has horrible linux support.
I am not sure about others either such as toshiba.

I use a WD drive and has always worked fine for me!

---

### Post by stchman on 2008-04-18
> **freerid3 said:**
> Hi! Here comes a total n00b question:
 I'm currently running Vista home basic :( on my computer I want to install Kubuntu. If i move all my files to an external hdd, terminate Windows and then install Kubuntu. Will Kubuntu be able to read the pictures, mp3's and movies from the external hdd? 

Forehand thanks!

So you are wanting to convert this PC completely over to Kubuntu?  Excellent.  I personally recommend Gnome over KDE as most of the Ubuntu HOWTOs are for Gnome but that is a personal decision.  Also you can make Gnome look quite a lot like KDE as well.

Yes, Linux can read all of your multimedia formats.  If you get an external hdd I would format it in FAT32 as you will need to do ZERO to read/write to it.

As long as the files are less than 4GB in size there is no problem.  Else you will have to use NTFS and Linux can read not write natively to NTFS.  Linux can write to NTFS with the package called ntfs-3g.  So pretty much anything you want to do in Windows you can do in Linux.

I do recommend that until you make a full switch that you dual boot if your hdd is large enough.  A lot of folks say that if they rid themselves of Windows completely they can more effectively learn Linux.

---

