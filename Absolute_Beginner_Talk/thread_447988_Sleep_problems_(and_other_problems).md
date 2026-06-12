---
title: "Sleep problems (and other problems)"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by st33med on 2007-05-18
Whenever I close the laptop lid while in the login screen, it doesn't suspend. When I open it again, It just remains a blank, non-lit screen. I hit Fn-Esc to Stand By.

My other problem is when I switch users, the user that I logon to has a completely white screen after loading everything. Thing is, I can still rotate my (non-Beryl) 3D-Desktop. I think it has something to do with the Desktop Effects.

Also, I have a problem when I boot up. When Ndiswrapper tries to rename my wlan0 to eth1, it freezes for a while, saying the wireless card is currently busy. This only happens occasionally.

EDIT: Second problem solved, it was the desktop effects.

---

### Post by Inxsible on 2007-05-18
Do you have restricted drivers installed for NVidia?
 
I have those installed and needless to say...my Hibernate, Log out, Suspend do not work :(
 
I have found something called suspend2 that seems to work for ppl. Havent tried it yet, if it works I shall let you know !

---

### Post by st33med on 2007-05-18
No, I do not even have Nvidia. I do have, however, a really bad Intel 256 MB Integrated card.

---

### Post by st33med on 2007-05-18
[SIZE="5"]Bump[/SIZE]

---

### Post by Gen2ly on 2007-05-18
Open up your Power Management in Preferences.  Is your settings "When laptop lid is closed" set to Suspend?  If not try starting "gnome-power-manager" again and see if it is.

---

### Post by st33med on 2007-05-18
It's fine there. I'm trying to say this only happens when there is a logon screen. I'm thinking that my settings do not affect it.

---

### Post by st33med on 2007-05-19
GAHHHHH!!!!!!! I messed up even more! My Firefox hangs when I play a flash video, Banshee doesn't play music anymore.

[SIZE="7"]HELP![/SIZE]

---

### Post by st33med on 2007-05-19
Anybody??? SOMEBODY??????????

---

### Post by st33med on 2007-05-26
Well, right now I'm running on fail-safe gnome, and everything works fine. Music plays, flash plays...

Which tells me something... a start-up script must be preventing me from playing any media. 

Hmmmm...

---

### Post by incubus on 2007-05-27
Hey st33med,

I suggest you create a new thread for these other problems and write detailed information about them.  Otherwise, people can only take a guess (which is not what you want). It is very important, therefore, that you include what you did to get to that state.  I hope we can figure it out.  So, keep this thread here just for the sleep issue.  

I'm having a similar issue myself.  I've seen people pointing to try what is written in this page:
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

The advantage of trying this is that you would know if it's some kernel module that's causing the misbehavior.

incubus

---

