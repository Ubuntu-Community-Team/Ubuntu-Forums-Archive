---
title: "New Desktop install - trying to customize stuff"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by markdean on 2007-08-29
OK, I'm new to Ubuntu having used mostly RH for the last 13+ years (I even purchased a Dell Precision Workstation pre-loaded with RHEL almost four years ago so Dell has been quietly selling Linux for years now), I decided to see what Ubuntu is all about-especially since Dell is now starting to sell hardware with it pre-installed. There are ways I like to run my *nix that many don't, and the main reason I run Linux is that customization is so flexible. 

Here are the first few:

I noticed that the install never asked me what packages I wanted to install, what run level I wanted to start at, what window manager I wanted, etc, etc, etc. What's up with that? 

How does one change the default run level to 3? (I start at that level and only go to X when I need to-yes, I read much of my emails in a terminal). I've tried to check for /etc/inittab (sudo ls /etc/inittab) but it comes back as not there, so Ubuntu is not RH-like in that regard. I did come across a Ubuntu forum that indicated that the /etc/inittab needs to be edited, but sudo-ing to see if that can be done results in the following:

mark@deanws20:~$ sudo ls /etc/inittab
Password:
ls: /etc/inittab: No such file or directory
mark@deanws20:~$ sudo vi /etc/inittab

(opens a NEW file called /etc/inittab)



I like to su  to root to do root level things and do not like to use sudo, that does not appear to be possible out of the box. 

Sometimes, I actually like to logon as root! (gasp!) ..... so I need to undo whatever the installer did to lock it down.

Any help would be appreciated. 

TIA!

---

### Post by rsambuca on 2007-08-29
> **markdean said:**
> OK, I'm new to Ubuntu having used mostly RH for the last 13+ years (I even purchased a Dell Precision Workstation pre-loaded with RHEL almost four years ago so Dell has been quietly selling Linux for years now), I decided to see what Ubuntu is all about-especially since Dell is now starting to sell hardware with it pre-installed. There are ways I like to run my *nix that many don't, and the main reason I run Linux is that customization is so flexible. 

Here are the first few:

I noticed that the install never asked me what packages I wanted to install, what run level I wanted to start at, what window manager I wanted, etc, etc, etc. What's up with that? 

How does one change the default run level to 3? (I start at that level and only go to X when I need to-yes, I read much of my emails in a terminal). I've tried to check for /etc/inittab (sudo ls /etc/inittab) but it comes back as not there, so Ubuntu is not RH-like in that regard. I did come across a Ubuntu forum that indicated that the /etc/inittab needs to be edited, but sudo-ing to see if that can be done results in the following:

mark@deanws20:~$ sudo ls /etc/inittab
Password:
ls: /etc/inittab: No such file or directory
mark@deanws20:~$ sudo vi /etc/inittab

(opens a NEW file called /etc/inittab)



I like to su  to root to do root level things and do not like to use sudo, that does not appear to be possible out of the box. 

Sometimes, I actually like to logon as root! (gasp!) ..... so I need to undo whatever the installer did to lock it down.

Any help would be appreciated. 

TIA!

The ubuntu developers decided they wanted to make it as close to an out-of-the-box-just-works type OS, and as such, they have picked the default applications to get new users started.

Quite honestly, from the stuff that it sounds like you like to do, I don't think you really need ubuntu!

---

### Post by kellemes on 2007-08-29
As far as I know.. for enabling the root-account you only need to set it's password:
```
sudo passwd root
```

---

### Post by markdean on 2007-08-29
sudo passwd root did the trick-thank you for that tip, I can now su to root. I am very impressed with the ease there is of installing programs, I haven't had to drop down to a terminal or edit a single text file...yet. I was even able to download mp3 codecs without any hassles. I can see why Ubuntu and its cousins are being used for desktop Linux.

---

### Post by kevdog on 2007-08-29
Sounds like a convert speaking :)  Ok maybe not!

---

### Post by CowzRule on 2007-08-30
Take a look at [this post]("http://ubuntuforums.org/showthread.php?t=271800") for info on your runlevel question

---

