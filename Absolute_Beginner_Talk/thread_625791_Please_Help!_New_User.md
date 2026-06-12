---
title: "Please Help! New User"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by mattroy89 on 2007-11-28
Hi,
I just installed the latest version of Ubuntu (7.10) and I have no idea what to do right now, I can't listen to mp3's and I don't know how to get Adobe Flash to work so I can watch videos on Youtube. Is there other configuring I should do? If anyone can help, that would be great!

---

### Post by samuel.rajesh on 2007-11-28
> **mattroy89 said:**
> Hi,
I just installed the latest version of Ubuntu (7.10) and I have no idea what to do right now, I can't listen to mp3's and I don't know how to get Adobe Flash to work so I can watch videos on Youtube. Is there other configuring I should do? If anyone can help, that would be great!


install the restricted 

Ubuntu 7.10
Synaptic
Go to Applications &#8594; Add/Remove... 

Set Show: to All available applications 

Search for ubuntu-restricted-extras and install it. Note that there is also xubuntu-restricted-extras and kubuntu-restricted-extras.

---

### Post by DutyDuty on 2007-11-28
You might want to install Automatix (Actually, you DO want to.)
Click the link in my sig for Gusty documentation. 
You should also acquaint yourself with the Terminal as best you can. 
Post back with more problems, we love to help!

---

### Post by mattroy89 on 2007-11-28
Wow! thanks so much!

---

### Post by PeterJS on 2007-11-28
> **DutyDuty said:**
> You might want to install Automatix (Actually, you DO want to.)


NO, no you don't. Automatix had it's time and place before Medibuntu and restricted extras existed.  There's nothing that automatix can do that restricted extras and Medibuntu don't. And Medibuntu and restricted extras don't have a history of breaking upgrades. Use this instead:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I hope automatix soon dies the terrible fiery death it deserves. :(

---

### Post by backflip on 2007-11-28
Check this out, it may be useful, I thought so.
[http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)

---

### Post by twiceasworn on 2007-11-28
You know I have never once used automatix, mediabuntu or anything like that to set up my boxes.  Its just as easy to do it manually with apt-get, since most of the crap you need is in there.

---

### Post by staticvoid on 2007-11-28
I used automatix... I deffinatly made a bad mistake, now with ubuntu 7.10 I just installed stuff clean through the package manager. If you go to YouTube it should ask you to install plugins..

sv

---

### Post by PeterJS on 2007-11-28
> **backflip said:**
> Check this out, it may be useful, I thought so.
[http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)


That looks like a good list, but the guide was written for edgy (6.10) so not everything in is is current.

NTFS-3g is in the main repository so there's no need to add an additional repository for that.

In step 9 the  Seveas repository has been replace by Medibuntu I mentioned in my last post.

Installing adobe reader is a lot easier these days, it is also in the Medibuntu repository and should be installed from there. As a word of general advice installing from a Deb package is always better then another method if you can find a deb for what you're looking for.

Step 12 of installing beagle isn't needed as beagle is now a default component.

The only comment I have about gDesklets is that they're decent, they're in the main repository, but I think screenlets work better and have more widgets available.
Here's a guide on installing screenlets:
[http://ubuntuforums.org/showpost.php?p=3783937&postcount=4](http://ubuntuforums.org/showpost.php?p=3783937&postcount=4)

---

### Post by DutyDuty on 2007-11-28
In defense, Automatix is pretty easy to use. It's how I started, as apt-get requires exact names and Synaptic has a lot of junk in there.

However, I never heard of those other things, so give them a look too.

---

