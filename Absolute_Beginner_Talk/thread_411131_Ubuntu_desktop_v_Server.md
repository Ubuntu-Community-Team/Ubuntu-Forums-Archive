---
title: "Ubuntu desktop v Server"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by proxima estacion on 2007-04-16
I have been using 6.10 Desktop untill now, but I am getting into running my own server (not for any particular reason). But have had no end of problems getting MySQL to work with PHP5 (apache2 installs and runs fine)

Im thinking of using Ubuntu Server edition so i know Apache,MySQL and PHP are all configured good to go.

But how differant is the server edition? does it have the GUI interface? does anyone have any thoughts or pointers before I wreck my system and start over again?


thanks all....

---

### Post by jvc26 on 2007-04-16
It doesnt have a GUI. You can install one if you want, but as standard it is just CLI entirely - its designed mainly for headless servers, and so consequently you dont need a GUI - again, if you want one you could install one like ```
sudo apt-get install xubuntu-desktop
```for a lightweight GUI. (Or go for something like fluxbox or the like to get it more lightweight.)
Il

---

### Post by fatphilthethird on 2007-04-17
I installed the server edition on an old box a while ago and rather than install a GUI (it's a really, really old box), I installed webmin which seems to do all the administering I need. 

If you want file/folder access, set up a SSH connection via nautilus (sorry, no idea what the correct technical term is, am nooooob). Can't remember exactly what the procedure is, am at work, but it's something like "connect to server" in the Places menu, stick in the IP and select SSH connection and it should prompt you for the uname/pword for the server.

These are the instructions I followed for webmin:
[http://ubuntuforums.org/showthread.php?t=195093](http://ubuntuforums.org/showthread.php?t=195093)


Hope that helps

Fat

---

### Post by proxima estacion on 2007-04-17
thanks all..... the above two messages got my server up and running sweeeeet. THX:popcorn:

---

### Post by hyper_ch on 2007-04-17
If you want to setup the server in a business manner - meaning like an ISP - then I recommend this tutorial:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

It configures everything from scratch... you just have to be able to read and copy'n'paste :)

Apache/PHP/MySQL/Mail Server.... all in there :)

---

