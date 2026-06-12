---
title: "Routine Maintenance on Ubuntu?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-05-11
So what now?  I've used Ubuntu for around 6 months now.  My system does the standard harddrive scan on every 30th boot.  
Do I need to defrag (last harddrive scan said 1.3% non-contiguous)?  
Do I need to install AVG and run routine antivirus scans?
What about spyware scans?

I'm just so paranoid that I'm NOT maintaining my system after years of being a Windows user, and having to do these things.

---

### Post by davahmet on 2007-05-11
Nope.  That's about it for maintenance requirements.

The only reason for an anti-virus scan on your Linux system is if you are concerned about passing possibly infected Windows files to a vulnerable Windows box.

Spyware does not and most likely will not gain a foothold on Linux.  In order to be effective, spyware needs a place to hide on a system.  Closed, propriatery systems like Windows and even Macintosh have lots of nice, dark corners for spyware to hide.  Since an Ubunutu system by default is open for inspection, there is no place for spyware to hide.  Additionally, spyware needs anonymity.  By using repositories with MD5 signatures as the source of software installations, the authors are easily verified, which removes the hidden, non-acountable place that badware author need.

In short, the minimal maintenance you're doing is all you need for an Ubuntu system.

---

### Post by starcraft.man on 2007-05-11
> **l951b951 said:**
> I'm just so paranoid that I'm NOT maintaining my system after years of being a Windows user, and having to do these things.

I know, its freaky huh? You get used to it though, and then you really have to look at windows users a bit oddly :p.

---

### Post by mikewhatever on 2007-05-13
Have you installed alot of things during the 6 months? You may want to clear the download cache in /var/cache/apt/archives. Unless you've done that, everything you downloaded with apt-get should be there. Here is the command
> sudo aptitude clean

---

### Post by steve.horsley on 2007-05-13
Just clean the dust out of the fans and air channels every few years. 
And do regular backups of course.

---

