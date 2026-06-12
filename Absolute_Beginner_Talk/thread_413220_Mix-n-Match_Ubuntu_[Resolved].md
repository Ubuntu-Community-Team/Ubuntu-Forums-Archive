---
title: "Mix-n-Match Ubuntu? [Resolved]"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by joshjani on 2007-04-18
Can pieces from the various versions of ubuntu be mixed-and-matched? Specifically, can I install the edutainment suites from Edubuntu on my new install of regular ol' ubuntu? One reason I rescued the older PC that I'm running ubuntu on is so that my young school age kids can plunk around on it without ruining anything expensive. I just investigated the edubuntu package, and though I don't particularly like the K desktop (I tried Kubuntu as a live cd) I like the other stuff, and would love to add it to my install for the kids.

How would I go about doing this? Download the edubuntu .iso, make a cd and then add/remove apps with that cd in?

---

### Post by lamalex on 2007-04-18
all of those apps are in the repo already, and edubuntu is a gnome desktop, not k so if you wanted to reinstall you could, or you could just insall any edubuntu apps you wanted to!

---

### Post by aysiu on 2007-04-18
Yes, you can mix and match.

If you're going to use the CD as a repository, though (do you not have a direct internet connection from Ubuntu?), make sure to download the Edubuntu Alternate CD (*not* the Desktop CD).

Then, in the terminal, type ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install edubuntu-desktop
``` When it asks if you want to install a whole bunch of packages, say *no.*

Then, take a look at the list of packages to be installed and pick the ones you want and install them with this command: ```
sudo apt-get install *packagename1 packagename2 packagename3 packagename4*
```

---

### Post by joshjani on 2007-04-19
> **aysiu said:**
> Yes, you can mix and match.

If you're going to use the CD as a repository, though (do you not have a direct internet connection from Ubuntu?), make sure to download the Edubuntu Alternate CD (*not* the Desktop CD).

Then, in the terminal, type ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install edubuntu-desktop
``` When it asks if you want to install a whole bunch of packages, say *no.*

Then, take a look at the list of packages to be installed and pick the ones you want and install them with this command: ```
sudo apt-get install *packagename1 packagename2 packagename3 packagename4*
```

Yes, I do have an internet connection, so I can get these edubuntu add-ons that way, huh?

Umm...How do I do it?:confused: 

Please know that I'm really happy to have found so many helpful hands out there- and I'm keeping an "ubuntu success journal" where I'm writing down all the good tips I'm finding here- so hopefully you'll tell me once and I'll have it for future study!

---

### Post by meborc on 2007-04-19
if you have internet you can install packages simply by```
sudo apt-get install <package name>
```

if you are not sure what you need, try out the synaptic from your menu... it is a graphical interface for searching and installing/removing programs

try searching edubuntu or education and see what you find

---

### Post by joshjani on 2007-04-19
> **meborc said:**
> if you have internet you can install packages simply by```
sudo apt-get install <package name>
```

if you are not sure what you need, try out the synaptic from your menu... it is a graphical interface for searching and installing/removing programs

try searching edubuntu or education and see what you find

I did search in synaptic and found the gcompris packages, installed it with english and spanish sounds.

I then did 

sudo apt-get install edubuntu-desktop

but cancelled out before I installed evrything. So much of this stuff is for the K desktop- but will it work OK with my gnome desktop, as I have just configured my ubuntu-pc for my network and all, and I like the gnome desktop better. 

I guess I want edubuntu with a gnome desktop! And I've read elsewhere here on the forums that it's possible to select your environment as you start, if you have both KDE and GNOME, but how?

---

### Post by aysiu on 2007-04-19
I thought Edubuntu *did* use a Gnome desktop.

---

### Post by joshjani on 2007-04-19
Well, I'm sure you're right as far as edubuntu being gnome based- your screen shot proves it! 

I could have SWORN it said something in Features or Wiki or somewhere about its being the K desktop, and that the edutainment suite integrated so well with it or something...But I can't find that now, and action at the Ubuntu site is slow due to everyone clamoring for Feisty (me included!)

But, I took your advice(es) and downloaded the kids stuff that I wanted. Seems to work great so far- even got a non-educational but fun Mr. Potato Head!

And I've marked the thread and snipped out tips to help later if I want to do more exploring of the different versions. So thanks!
JC

---

### Post by Bill_and_Jim on 2007-05-20
So, we just installed Ubuntu 6.10 from the DVD that came with * Beginning Ubuntu Linux, 2nd Ed*., by Keir Thomas.  Now we want to add the Edubuntu-desktop so we can have all the features we saw on the Live CD.  We were using a live CD for Edubuntu 6.10 made from an ISO file on the DVD.

We are without an Internet connection, and setting up the winmodem is not going to happen for weeks, if ever.
So it seems to me that I am in the situation describe in this thread: 

"If you're going to use the CD as a repository, though (do you not have a direct internet connection from Ubuntu?), make sure to download the Edubuntu Alternate CD (not the Desktop CD)."

So, here are my questions:  
Is the comment above referring to a CD for alternate install of Edubuntu 6.10? 
If that is the CD being referred to, can I still get one?  Shipit for Edubuntu only mentions 7.04.
If not a CD from Shipit, then can I get one?  Downloading requires I impose on someone with a fast internet connection, and I would rather wait for the mail.  Teaches my son to be patient.

Any help on getting Edubuntu running as a Theme under Ubuntu is most welcome.

Thanks, 
Bill.

---

### Post by joshjani on 2007-05-22
> **Bill_and_Jim said:**
> So, we just installed Ubuntu 6.10 from the DVD that came with * Beginning Ubuntu Linux, 2nd Ed*., by Keir Thomas.  Now we want to add the Edubuntu-desktop so we can have all the features we saw on the Live CD.  We were using a live CD for Edubuntu 6.10 made from an ISO file on the DVD.

We are without an Internet connection, and setting up the winmodem is not going to happen for weeks, if ever.
So it seems to me that I am in the situation describe in this thread: 

"If you're going to use the CD as a repository, though (do you not have a direct internet connection from Ubuntu?), make sure to download the Edubuntu Alternate CD (not the Desktop CD)."

So, here are my questions:  
Is the comment above referring to a CD for alternate install of Edubuntu 6.10? 
If that is the CD being referred to, can I still get one?  Shipit for Edubuntu only mentions 7.04.
If not a CD from Shipit, then can I get one?  Downloading requires I impose on someone with a fast internet connection, and I would rather wait for the mail.  Teaches my son to be patient.

Any help on getting Edubuntu running as a Theme under Ubuntu is most welcome.

Thanks, 
Bill.

I'll send you a CD- seems I've downloaded just about every ISO! I have edubuntu-6.10-install-i386.iso 
Contact me via private message.

JC

---

