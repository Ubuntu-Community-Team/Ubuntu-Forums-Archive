---
title: "New user, ubuntu fails to log in."
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by klomp10 on 2006-11-14
I am extremely new to ubuntu and everything was working great. Now when I go to log in I put in my user name and pass, it starts logging in, gives black screen with blinking hyphen type thing, ubuntu background shows up, then it gives an error sound. and goes back to log in screen. If I enter a incorrect password it gives me an error, so thats not the problem. The first time this happened I just reinstalled ubuntu but this is the second time it has happened. I think it's user error but I do not know. I have also tried starting a Default system session, failsafe Gnome. and they all do the same thing. 
and the version is 6.10, and I was warned not to use it but I wanted to try it first. :-D  Thank you.

---

### Post by grim918 on 2006-11-14
I am also a new ubuntu user so my answer may not be the best. If you absolutelly can't log into the system in any way then there is no chance for you to try and fix it since you can't modify any files. You should try running the Edgy Eft Live CD. I heard that if the cd runs on your system then it is safe to install on the hard disk. 

If all fails then you can install Dapper Drake. I think that is the best Ubuntu distro yet. Or just wait for a more experienced person to come along and help.

---

### Post by schrombot on 2006-11-14
From the login screen, press CTRL+ALT+F2 and see if you can log in from the command prompt, if you can it is probably an xorg.conf folley. Try running ```
sudo dpkg-reconfigure xserver-xorg
``` follow the prompts and see if that helps any.

---

