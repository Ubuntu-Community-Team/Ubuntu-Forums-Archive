---
title: "New user, Dell sound with 7.10"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by NoPantsJim on 2007-10-22
I'm fairly new to Linux, only been using for about 2 months. I spent almost that entire time beating my head against the wall with Fedora, taking two weeks to make my video card work and never actually getting wireless or Compiz to work. I decided to try Ubuntu the other day and I can't believe how easy it's been. The only thing that's still giving me problems is my sound, which oddly enough worked great under Fedora without me ever having to do anything. I'm not sure where to turn, and the Dell support site has been zero help. When I click on my volume control thing on the taskbar, it gives me this warning:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

I'm running 7.10 on an Inspiron 1720 notebook. The sound device as listed on my original order is "Integrated High Definition Audio 2.0" with no other real information. Any help is greatly appreciated.

---

### Post by Skweek on 2007-10-22
Try this;

sudo apt-get install linux-backports-modules-generic

It worked for my 1720. I now have glorious stereophonic tunes pouring from my lappy!!

---

### Post by NoPantsJim on 2007-10-22
thanks, worked great!

---

### Post by NoPantsJim on 2007-10-27
well damn, that worked fine for awhile, but I decided to do a fresh install of 7.10 and now it's not working properly. I entered:

sudo apt-get install linux-backports-modules-generic

and got the following messages:

nopantsjim@laptop:~$ sudo apt-get install linux-backports-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-generic
nopantsjim@laptop:~$


Not really sure what to do, worked without any problems the first time around. I am connected to the internet while trying this, and I also tried with and without the 7.10 disk in the drive.

---

### Post by stil on 2007-11-04
I also have this problem with 'package not found'. Seems like I'm so close, but so far.

---

### Post by TransitMan on 2007-11-04
Make sure you have the Backports repository enabled, otherwise you will get "pakage not found".

---

### Post by NoPantsJim on 2007-11-04
Well I found out the problem was that I wasn't connected to the internet at the time, so try to be certain you are connected and then try again.

---

### Post by ctt1wbw on 2007-11-16
I have been waiting for a solution to this problem.  I have an Inspiron 1720 and tried the live cd and of course, the sound didn't work.  I'll try to install it this weekend and see how it goes.  Thanks!

---

