---
title: "how to get to root in ubuntu 7.04"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by ehtoft on 2007-10-24
absolute novice banging head in vain. Problem: trying to get to root so that I may put flashplayer there (this was advised by Truefire.com in order that their interactive video lessons would work on linux). I've just installed Ubuntu 7.04 for very first time ever. I've only ever used windows as GUI dependent and am embarrassingly ignorant. No other users, just me. Brand new installation. Something about "sudo", but I'm lost in terminal because of command demands. File I need is now in a folder in "Desktop". How to get permission rights to my own user! Ultimately, I want to stick with linux and get more of my music stuff going there and truly get windows-free! et from norway

---

### Post by dca on 2007-10-24
There is no 'su' or super-user only 'sudo' by default.
 
Preface your command w/ 'sudo' and it should ask for your user (which is root user in a way) password...  Wait a tic, can you go to System -> Administration -> Synaptic???
 
 Search for flashplugin-nonfree or something thereabouts and install?

---

### Post by ehtoft on 2007-10-24
Thanks for your speedy answer. I did actually find something to that affect on the help pages, and I even tried it. But since I have no idea what to write after that - to get the file in root - I go out again and try to find a GUI app to do it, but it wont accpet me. Also, I got Firefox to install the flashplayer as available for webbrowser, but it doesn't go deep enough and hence not usable by other programs. I guess what I need is either a totally GUI mode for idiots, or start learning the command language. Any hints on how to ease into that? Whew! busy on all fronts. Will I make it someday?  eT

---

### Post by aysiu on 2007-10-24
You don't need to log in as root.

But you especially do not need to log in as root in order to install Flash.

Just follow this tutorial:
[http://www.psychocats.net/ubuntu/flashpre710#synaptic](http://www.psychocats.net/ubuntu/flashpre710#synaptic)

This doesn't involve logging in as root or using the terminal at all, but it will install Flash "deep enough" to affect all web browsers and users, not just Firefox for the current user.

---

### Post by ehtoft on 2007-10-24
cheers. I'll do this tomorrow and let you know..... thanks guys. maybe there's hope after all
eT

---

### Post by Hospadar on 2007-10-24
If you reeeeaaaly want to log in as root, you can do "sudo su" but you really shouldn't do that.  ever.  you will probably just muck stuff up accidentally.  just prepend every command that needs root with sudo, or gksu if it's a GUI application.

---

### Post by aysiu on 2007-10-24
It's not really that dangerous to log in as root, but it's completely unnecessary.

---

### Post by megahertz on 2007-10-24
There is a way to log as root. I used myself for editing There is a way to log on as root. I used myself for editing my scanner configuration files and copy other files owned by root. Two steps to follow:
1) open menu = System – Administration- Users and Groups
-Select user root root and open Properties 
- On Account tab in the Password field put a new User (for root) password and repeat it in Confirmation.
- On User Privileges tab select almost all options and hit OK and then close.
2) open menu = System – Administration – Login Window
- Select Security tab.
 - Check box = “Allow local system administrator login” and then close.

Now you can switch user to root and you will be logged on as an super user.
Beware that as root you have unprotected your system. Do what you have to do with extreme care and return to your own log as soon as possible.

---

### Post by megahertz on 2007-10-24
There is a way to log on as root. I used myself for editing my scanner configuration files and copy other files owned by root. Two steps to follow:
1) open menu = System – Administration- Users and Groups
-Select user root root and open Properties 
- On Account tab in the Password field put a new User (for root) password and repeat it in Confirmation.
- On User Privileges tab select almost all options and hit OK and then close.
2) open menu = System – Administration – Login Window
- Select Security tab.
 - Check box = “Allow local system administrator login” and then close.

Now you can switch user to root and you will be logged on as an super user.
Beware that as root you have unprotected your system. Do what you have to do with extreme care and return to your own log as soon as possible.

---

