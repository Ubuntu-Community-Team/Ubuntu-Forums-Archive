---
title: "changing permissions"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Shadowmeph on 2007-06-04
ok I am a noob at linux but the one thing that annoys the hell out of me with this os is that since I am the only one using this comp how come i get permission denied's? and how can I change this permanently. I am using two hard drives one drive is using data center 2003 and the other is using  Ubuntu feisty fawn which I am learning about ( thats why I have two drives :)   )anyway I can't get all of my mouse buttons to work for my gaming well for everything and I have found some posts instructing on how to change this but like I said I get those annoying permissions prob is there a way to make it so I have permissions permanently?

---

### Post by Henry Rayker on 2007-06-04
This is a horrible idea. The permissions are there as a safegaurd. If you really want such a thing, you should just search the boards for something along the lines of "logging in as root" and find a howto that way. This account is not enabled by Ubuntu by default to prevent accidents and mistakes.

The permissions are honestly there to prevent accidents etc. If you really want to edit the file, you could just do a ```
gksudo gedit [filename]
```The added effort will help to keep your system healthy and secure.

---

### Post by daimaru on 2007-06-04
ubuntu uses the sudo command to temorarily grant you root (admin) rights. 15 minutes or so. if you want to for example edit a file you type in terminal
```
sudo gedit /etc/X11/xorg.conf
```
then you open that file with admin rights and you are allowed to change stuff.
if you want to work as root, you can type
```
sudo -i 
```
that changes you to root until you type
```
exit
```
if you really want to login as root which is not recommeded because of security issues, you have to enable graphical login for root.  to do that
system-->administration-->login window
select the security tab and check the box "allow local system admin login"

---

### Post by Henry Rayker on 2007-06-04
> **daimaru said:**
> ubuntu uses the sudo command to temorarily grant you root (admin) rights. 15 minutes or so. if you want to for example edit a file you type in terminal
```
sudo gedit /etc/X11/xorg.conf
```
then you open that file with admin rights and you are allowed to change stuff.


I wanted to add that this should be ```
gksudo gedit /etc/X11/xorg.conf
``` because of the fact that gedit is graphical. Yeah, I know it's dumb....

---

### Post by lazyart on 2007-06-04
Windows machines by default let users run with full rights-- and this is how viruses and spyware are able to do their dirty work.  Microsoft in fact has tried to change this and has ended up annoying at lot of users with Vista, but that's another story altogether.

Use sudo and gksudo to make your changes.  Most of the time you don't need rights to everything.

---

