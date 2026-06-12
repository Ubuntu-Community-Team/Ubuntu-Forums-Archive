---
title: "Isdn"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by TheMask on 2005-09-09
Ok, so... i installed my ubuntu, everything went ok and I was pretty satisfied, but when I wanted to get my internet connection working that's when the trouble started... I go online (using Windows) and find something called isdn4linux... I follow the instalation instructions but it seams I have no gcc?! Now I try to find a gcc installer or something and I download something, but in the middle of instalation it says it is missing something (cc or something... I can check) and does not want to continue. Now I am really frustrated with ubuntu and I just give up, and continue using Windows........ After a week or two I decide to give it another go... I go online, ask some of my friends for help and one of them suggests I download some packages (.deb) and try to get my ISDN working using them... I get tangled up in dependencies, but I manage to be patient enough to download something like 10-20 packages and dpkg them. One of them even asked me to give it my username and password and I got all excited but 4 nothing. I tried to connect using isdnctrl dial ippp0 (I read this on some page) but (as I expected) it didn't work. So now I am asking you... how can I get my connection to work... I would also really like to have gcc, but I am told that it is no problem when I have an Internet connection (there are some updates or something I can use to get it).

---

### Post by heimo on 2005-09-09
Hi,

check these instructions (Hoary section if you have Ubuntu 5.04):
[https://wiki.ubuntu.com/IsdnHowtoHoary]("https://wiki.ubuntu.com/IsdnHowtoHoary")

You probably need to install linux-restricted-modules-386, or if you have some other than default kernel installed, the matching one. Check by running uname -a on terminal. If you see 686 or k7 or something else than 386 there, you should install matching restricted modules. To do that, you need to have restricted section enabled in /etc/apt/sources.list, you can do this with synaptic package manager or with any "raw" text editor. It's similar as enabling universe section
[https://wiki.ubuntu.com/UniversePackages]("https://wiki.ubuntu.com/UniversePackages")

I haven't used ISDN for ... 7-8 years? It was pain then, it should be fairly easy now, but I don't have any detailed instructions. Hopefully however I can point you to right direction - I also recommend using Search on these forums to find how other people did it. And please don't hesitate to ask any qustions, other people with better knowledge of ISDN with Ubuntu will read this thread (and hopefully give their input). :)

Welcome to Ubuntu!


EDIT: Argh, I just realised that I didn't take into account that you probably don't have internet connection on that box... that's why you're downloading manually, isn't it? Darn. Chicken-egg-problem.

---

