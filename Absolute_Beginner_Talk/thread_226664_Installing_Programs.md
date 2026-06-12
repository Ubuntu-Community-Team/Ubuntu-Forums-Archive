---
title: "Installing Programs"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by trav777 on 2006-07-31
Hi, I am very new to Linux and I am trying to wheen(spelling?) myself of Windows and it's a little frustrating.

I am wanting to install Nvu for web design, but I have no idea which Linux format(am I saying that right?) Ubuntu is and after the download, what do I do?

Thanks,
Travis

---

### Post by T700 on 2006-07-31
Most programs can be installed automatically via Adept or using the command line with "apt-get" or "aptitude".  Please see "How to Install Anything" in my signature for a complete explanation.

Paul

---

### Post by trav777 on 2006-07-31
Ok, could you tell me which download I should choose?
[http://www.nvu.com/download.php](http://www.nvu.com/download.php)

---

### Post by FizDev on 2006-07-31
Download the .deb then do this in a terminal
```
sudo dpkg -i nameofthedeb.deb
```

Edit : By the way, it might already be in apt (I'm not on my computer so I can't check right now)
To check if it's there, do this
```
apt-cache search nvu
```
then to install the good one
```
sudo apt-get install nameofthegoodone
```

---

### Post by trav777 on 2006-07-31
Is there a .deb file on that page?

---

### Post by T700 on 2006-07-31
You don't need to download anything from nvu.com.  You don't need to compile it by hand.  It is already done and readily available from the Adept package manager or from the command line.  See the attached screenshot.

Please take a few minutes to learn the easy way to install things in Ubuntu.  I promise you it will save you a huge amount of frustration.

Paul
[IMG]http://img.photobucket.com/albums/v307/paulmyoung/Sharing/adept.png[/IMG]

---

### Post by Vladimirm on 2006-07-31
[http://cvs.nvu.com/download/nvu-1.0-pc-linux2.6.10-gnu.tar.bz2](http://cvs.nvu.com/download/nvu-1.0-pc-linux2.6.10-gnu.tar.bz2)

In future, it is easier to install packagesvia ubuntus apt-get or aptitude 

[https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)

See this for more information

---

