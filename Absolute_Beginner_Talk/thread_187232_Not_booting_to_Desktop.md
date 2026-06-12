---
title: "Not booting to Desktop"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by martinnc2003 on 2006-06-02
I just finished installing ubuntu on my computer. I installed it on a spare system, with ubuntu being the only os installed and put it on a 20 gb harddrive with no partitions. After I installed ubuntu and it told me to restart and remove the disk, I did. When it booted up it came up to the command line and told me to enter my login, when I enter my username and password, it comes up with my username@linuxbox:~$  I was thinking it was supposed to boot to the desktop but it did not. I have some experience with linux, I took 2 semesters with Fedora Core 4. Any help would be appreciated! Thanks in advance!

---

### Post by nalmeth on 2006-06-02
Sounds like a server install to me.

startx

should tell you whether or not you have an "X" server

If this doesn't work, go (have an internet connection?
```
sudo apt-get install ubuntu-desktop
```
or if you prefer KDE
```
sudo apt-get install kubuntu-desktop
```
or if you prefer XFCE
```
sudo apt-get install xubuntu-desktop
```

---

### Post by martinnc2003 on 2006-06-02
man you are exactly right....stupid me downloaded the server install lol. Thanks for the help tho!

---

### Post by rputtagunta on 2006-06-03
Hi,

   I am new to Linux. So, please bear with my ignorance. Let me get this straight. I went to ubuntu.com and went to:

   I think I know what happened now.

   Please notice that the desktop and server download link, BOTH point to the same link.  [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

   I was thinking that the desktop link is for desktop install and server for server. Since, mine is a personal laptop, I went to desktop. Then I thought that WITHIN the desktop link, I have two options: (Desktop - for a taste of Ubuntu installable in windows (not an actual linux installation) and server - actual linux which I wanted since I wanted to install Oracle XE on linux). 

   Is mine is a genuine error or am I just being dumb? If I am, please explain what this sentence means:

'The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. ' and 'The server install CD allows you to install Ubuntu permanently on a computer.'

   Anyway, the reason I ask is, I was able to load the server fine, but, then I didn't get GNOME just like 'martinnc2003'. So, now, I am doing :

sudo apt-get install gnome-desktop

    Thank god my network was connected to DHCP fine, else , it would have been a big hassle. The installation is not done yet, so, I am keeping my fingers crossed.

---

### Post by painterboy on 2006-06-03
It sounds like the desktop cd is a Live cd which means when you boot up from it you can run ubuntu directly from the cd nothing gets saved or changed on your hard drive then if you like how it works then you can install it from the same disc.  The server install is strictly an installation disc so as soon you  use it you begin the installation and since its meant for server applications gnome doesnt come preinstalled, at least thats my understanding. Hope this helped

---

### Post by rputtagunta on 2006-06-03
Hi PainterBoy,

    You are right on target. Thank you very much for that. Now, my oracle XE didn't load because of too less a swap space (900MB) it needed atleast 1gb swap. So, deleted the whole thing and this time installed the desktop version of Ubuntu. Installed pretty cool after some tweaking. 

    Btw, i used 2gb swap space. specifying this just in case somebody else installs oracle XE here. hopefully, they will save some time.

---

