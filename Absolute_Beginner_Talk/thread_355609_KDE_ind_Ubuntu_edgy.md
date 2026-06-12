---
title: "KDE ind Ubuntu edgy?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by jolger on 2007-02-07
Hello... i was just wondering if it was possible to get KDE on ubuntu instead of downloading Kubuntu itself... and that pretty much all i want to know :P hope i can get some nice answers ^^

---

### Post by resist- on 2007-02-07
Yes it is possible to do so... I tried it a few days ago, installation went perfectly... I didn't like it and i had a little trouble installing it... But here is some reading about kde installation on ubuntu 


First link is a very helpful site to get some advice on a lot of useful stuff:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_KDE](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_KDE)

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

---

### Post by Iarwain ben-adar on 2007-02-07
Just a simple command is needed
```
sudo aptitude install kubuntu-desktop
```

And if you want to remove it
```
sudo aptitude remove kubuntu-desktop
```


Iarwain

---

### Post by SunnyRabbiera on 2007-02-07
yeh its pretty easy to get KDE in ubuntu, its in synaptic too if you dont like terminals.

---

### Post by floke on 2007-02-07
The kubuntu-desktop will install Kubuntu though - which is not really a problem although it hijacks the boot splash screen!

---

### Post by sugarland2k on 2007-02-07
I loaded Kubuntu with sudo aptitude install kubuntu-desktop from Ubuntu Gnome and I love it.  the download was about 114MB but I ended up with a nice Blue KDE 3.5.5.  I just upgraded to KDE 3.5.6 with no problems, another pretty big download, also loaded KDE KOffice.   

From the inititial logon screen, you can hit F-9 (or is it F-10) to bring up an options screen so you can switch back to Gnome if needed.

A happy Ubuntu/Kubuntu camper!

---

### Post by jolger on 2007-02-07
> **Iarwain ben-adar said:**
> Just a simple command is needed
```
sudo aptitude install kubuntu-desktop
```

And if you want to remove it
```
sudo aptitude remove kubuntu-desktop
```


Iarwain

Yes i did that... however i use apt-get wich shouldnt do a big difference... i just dont know how i start KDE now... if i look at the "options" thingy on my bootscreen i can only select gnome... KDE doesnt even show up... some advice would be appreciated ^^

---

### Post by chocbar31 on 2007-02-07
[http://www.kde.org/download/](http://www.kde.org/download/)

[http://docs.kde.org/development/en/kdebase/faq/install.html](http://docs.kde.org/development/en/kdebase/faq/install.html)

Happy reading!

Or you can be safe and do a sudo apt-get install kubuntu-desktop. This will also save you time in the future, as you will definately need to install some KDE apps for other KDE apps to work. Not that you will have issued, but I have read where folks run into issues installing KDE alone.

I know this is lame but kubuntu =  KDE instead of Gnome as your desktop manager, on Ubuntu!

All the answers you'll need is on the KDE site, if you want to get it right.

---

### Post by chocbar31 on 2007-02-07
> **chocbar31 said:**
> [http://www.kde.org/download/](http://www.kde.org/download/)

[http://docs.kde.org/development/en/kdebase/faq/install.html](http://docs.kde.org/development/en/kdebase/faq/install.html)

Happy reading!

Or you can be safe and do a sudo apt-get install kubuntu-desktop. This will also save you time in the future, as you will definately need to install some KDE apps for other KDE apps to work. Not that you will have issued, but I have read where folks run into issues installing KDE alone.

I know this is lame but kubuntu =  KDE instead of Gnome as your desktop manager, on Ubuntu!

All the answers you'll need is on the KDE site, if you want to get it right.


One more thing; you do have the option to use either KDM or GDM as your default login manager. Furthermore, you may swithch these at any time by using the following command:

Code:

dpkg --configure gdm

---

### Post by Iarwain ben-adar on 2007-02-07
> **jolger said:**
> Yes i did that... however i use apt-get wich shouldnt do a big difference... i just dont know how i start KDE now... if i look at the "options" thingy on my bootscreen i can only select gnome... KDE doesnt even show up... some advice would be appreciated ^^

Did you restart your X ? (log out, and hit Ctrl-Alt-Bckspc)

Btw, you should have used aptitude, because aptitude handles unneeded packages way better than apt-get.


Iarwain

---

