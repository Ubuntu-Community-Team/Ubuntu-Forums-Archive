---
title: "Roll Back the Computer to an Older Time"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-02-04
Hello!
I installed KDE 4 by "sudo aptitude install kde4-core" and I found a lot of problems, such as my shot down button in Gnome disappeared! So I removed it by "sudo aptitude remove kde4-core" Again I have problems. How can I roll my computer back to a previous time when there were everything was OK?
+++
I came to Linux because I thought it's more stable than Windows, but it's the least stable operating system. I reinstalled it 3 times in 5 days!
____
Need your help.
Thanks,

---

### Post by LowSky on 2008-02-04
simple answer is you can't, unless you you make your own back ups

as for linux being more stable.. it is, when you know what your doing and dont just hastily add/remove pakages.

as for the shut down button that ubuntu has on the top panel all the way to the right ... it isnt the only one... these another in the Settings menu, and you can re-add it to the menu by right clicking on a panel and choosing add to panel, or use terminal and typiong killx or shutdown

here is a list of bash commands
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)


what other problems are you having?

---

### Post by keithacole on 2008-02-04
> I installed KDE 4 by "sudo aptitude install kde4-core"

> came to Linux because I thought it's more stable than Windows, but it's the least stable operating system. I reinstalled it 3 times in 5 days!

if you want stability, stop installing bleeding edge software, same with windows is the same for linux.go with a well used distro, and never upgrade. you will never have problems

---

### Post by kryth on 2008-02-04
Learn how to make backups or use imagepart to make Norton like ghost images.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
There's other ways of backing up and restoring, but that's my favorite. Although it does have a bit of a learning curver. You can also find other howto's in this forum. 

When first learning Ubuntu, I reinstall probably 2-3 times a week. Not because there was a problem with Ubuntu, but there was a problem with me fubar'ing it. That's how you learn. That's how you learn how improtant it is to backup. Good luck.

---

### Post by Hoom@n on 2008-02-04
Thanks alot for your help. After I removed KDE and restarted my computer I came to a command line view, so I reinstalled it for the 4th time! This time I think, I know what should I do!
+++
I had the shut down button in the top left side, but there were no shut down inside it. There were only supend and hibrebate.
+++
I wanna have a backup of my linux. Not hole computer. What should I do? (I know you told me something in last posts, but please tell it again!)
____
Thanks again.

---

### Post by LowSky on 2008-02-04
best advice is keep a seperate /home partition, this way you dont loose your settings and files

---

### Post by Hoom@n on 2008-02-05
Thank you.

---

### Post by andybleaden on 2008-02-05
I can vouch for the separate partition arguement. It saves a whole heap of problems in cases like this.

As for upgrading I went from Dapper...to Feisty and then to Gutsy with only a few problems...the big pity was that you could not upgrade to say partition 2 when your original system is on partition 1...that would mean that we could roll back surely?

---

### Post by emarkd on 2008-02-05
> **Hoom@n said:**
> I came to Linux because I thought it's more stable than Windows, but it's the least stable operating system. I reinstalled it 3 times in 5 days!

Linux is very stable.  Many people have Linux boxes that run for months or years between reboots.  I've got a Linux server here at home that's been up for almost 60 days now and I experiment on it a lot.  Heck, Google runs their search servers on Linux.  But any system will crash if you use it incorrectly or run buggy software on it.  That's the philosophy behind the Ubuntu LTS releases.  Stick with older, more established versions of the software and you'll have less problems.

---

### Post by andybleaden on 2008-02-05
I have been using Kubuntu for over a year and a half now at least and HAD to go back to a windows system when I had hardware issues and it was awful...really buggy and very inflexible. I could not wait until my kubuntu pc came back and I could do what I wanted to ...play a avi file...download files etc without all the bloody hassle with windows...needless to say windows pc is back with daughter (neds it for games) but I expect a few problems with any system 

However at least with kubuntu/linux I can change it and improve it

---

