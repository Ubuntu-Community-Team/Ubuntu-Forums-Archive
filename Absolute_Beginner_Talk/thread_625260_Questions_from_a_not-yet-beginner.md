---
title: "Questions from a not-yet-beginner"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by tapasray on 2007-11-27
Hello, everyone! I have been using Windows for years but am now thinking of migrating to Ubuntu for various reasons, including the opinion I have heard about Linux being more stable than Windows generally. But the issue that worries me is running various essential applications. For me, critical applications are daily backup on CD/DVD, daily backup on external hard drive, and ReadIRIS image to text converter. 

I back up my files on CDs and DVDs with Nero every day, because Nero has a very useful backup feature - it reads the CD/DVD and selects for burning only those files that have been added or changed in the source folders on my computer, since the last operation. 

This feature is essential for me, as I often add scores of files in dozens of folders. I need this feature if I use Ubuntu. I understand one can run some Windows apps through WINE, but Nero apparently doesn't work well. I do not want to buy the Linux version of Nero, and I would like to stick to the burning software that comes as part of Ubuntu (as far as I can tell from the web site) or some other free software. Could someone please let me know whether the nice backup feature I have mentioned above is available in these applications?

I also on an external hard drive that came with its own backup software. Is there a way to use it in Ubuntu? Can I use ReadIRIS, perhaps through WINE?

I would really appreciate some advice on these questions.

Thanks in advance and regards.

---

### Post by kelbizzle on 2007-11-27
I'll tell you this...Wine isn't a solution for running windows apps. It's an alternative. If noone else has installed and ran that program the only way to find out is to try and install it. What I did for a customer was [put windows xp inside of a Box]("http://www.virtualbox.org") and installed those "critical apps" that she needed to run.  There are back up solutions for ubuntu. It will be hard finding something "Just like Nero" or something even "close to nero" but I'll tell you there are LOTS of ways to back up your Ubuntu system. Some ways just issue a simple command to .tar (.zip) up all the importants files. Then you can burn that to a dvd.  (With scripts you can do anything. If a program exist of course.)

---

### Post by jordanmthomas on 2007-11-27
> **kelbizzle said:**
> It will be hard finding something "Just like Nero" or something even "close to nero" but I'll tell you there are LOTS of ways to back up your Ubuntu system.

Really?  You do make a valid point, though.  It was just an unfortunate example.  :)
[http://www.nero.com/eng/linux3.html](http://www.nero.com/eng/linux3.html)

---

### Post by tapasray on 2007-11-27
Thank you, kelbizzle. I will try out WINE and check out the Virtual Box information. Thanks also to you, jordanmthomas.

---

### Post by Flying caveman on 2007-11-27
[http://www.linuxquestions.org/questions/linux-news-59/nero-for-linux-300876/](http://www.linuxquestions.org/questions/linux-news-59/nero-for-linux-300876/) There is NERO for Linux but i'd rather use something else.

---

### Post by Grey Box on 2007-11-27
I keep a windows installation on a vmware image (but virtualbox is a good choice too) and keep it updated, but I found after a time that I hardly need it at all. Still, it is great because I know I can run any windows app on it. 

K3B is nero-ish and does all my DVD/CD burning without a problem. K9copy does my DVD backups. 

For regular backups there are heaps of solutions, but I just do a weekly fresh copy of my entire home folder onto an external drive. I just made an automated command to do a simple copy (I havent found time to configure anything more clever yet). There are smarter backup solutions but when you are choosing one, you must ask yourself how easy it is to restore your backup? Low-tech is good-tech for these things, I find.

---

### Post by tapasray on 2007-11-27
This is really encouraging, Grey Box!

---

