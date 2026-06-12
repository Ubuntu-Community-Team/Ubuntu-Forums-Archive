---
title: "Yahoo Messenger Install Edgy"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by scotty76uk on 2006-11-14
Hi I'm trying to install yahoo messenger on edgy 

when I try to install ymessenger_1.0.4_1_i386.deb I get the following message

"Error: Dependency is not satisfiable: libss0.9.6"

so I tried

root@scotty-desktop:/home/scotty# apt-get install libssl0.9.6_0.9.6c-2.woody.8_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libssl0.9.6_0.9.6c-2.woody.8_i386.deb

what am I doing wrong? sorry I'm a newbie so it's all a learning curve

thanks scottt

---

### Post by Jukey on 2006-11-14
Did you try checking synaptic for it? You should be able to find and install all packages from there.

---

### Post by scotty76uk on 2006-11-14
thanks for the reply

I checked in synaptic and it says i have a later version installed 9.8

---

### Post by Ambimom on 2006-11-14
Try web-based Meebo.com for Yahoo.

---

### Post by scotty76uk on 2006-11-14
I'm trying to find a IM client that I can enter the rooms with

---

### Post by nhoj on 2006-11-17
Hello everyone! I am also an newbie with Ubuntu. I must say, I love it! I am, little by little, drifting away from Windows.

Anyway, my question is about some features of Yahoo! Messenger that maybe found in Gaim.

Gaim is a great program. No doubt about that, BUT there's one particular feature in Yahoo! Messenger that I use that is not found in Gaim (or at least not yet), or any other "generic" chat software for that matter: "Login to mobile phone".

It's a feature in Yahoo! Messenger that we can send/receive text messages with other online or "logged-in mobile" friends. I do this all the time to keep in touch with friends back home in the Philippines (I'm in the USA). It's cheap (both sender and receiver) and the texts are charged in our phone plan, as opposed to expensive overseas text messaging.

So, I'm not really sure, yet, if Gaim has that capability. That's the only thing I look for in any other chat softwares. If ever, I will have to happily ditch the Yahoo! Messenger software and go head-on with Gaim!

Thanks for your time, everyone. Have a great day. 

Peace.

---

### Post by loell on 2006-11-18
gyachi deb package for edgy is now in its official download page

[gyachi.sourceforge.net]("http://gyachi.sourceforge.net")

---

### Post by adam.tropics on 2006-11-18
What's wrong with Gaim?

nhoj....point taken! didn't see your post. Even so, Gaim is a pretty good all rounder

---

### Post by nhoj on 2006-11-22
Thanks Adam.Tropics. Yup, Gaim is excellent. I am just hoping it would have that functionality (login to mobile phones). I guess there will be in the net version of Gaim? :-D 

Have a great day everyone!

Peace.

---

### Post by nhoj on 2006-11-22
Thanks Loell. I see that you're from the Philippines! I'm from Baguio, but now I'm abroad. 

Thanks, I'll try that out...

---

### Post by nhoj on 2006-11-22
Gyachi doesn't have that function either :( 

Thanks anyway, Loell. Have a great day!

---

### Post by loell on 2006-11-22
hi nhoj :mrgreen:

  yeah, this is one of the capabilities that third party messengers can't  
  duplicate, there never was a documentation on how yahoo does it.

---

### Post by ragadanga63 on 2006-11-25
Another important feature of Yahoo Messenger that GAIM may not have is WEBCAM.  I wonder why the guys at Ubuntu did not incorporate this feature.  This is the only thing that's keeping me from totally moving over to Ubuntu.  Windows sucks!

Has anyone tried installing YM using WINE?

---

### Post by loell on 2006-11-26
kopete and gyachi does webcam in yahoo, ubuntu is not responsible for gaim development, its the work of gaim developers, which leads to the question 
why no webcam? well short answer is, they having difficulties incorporating audio/video in gaim

---

