---
title: "User doesn't excist"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by stekre on 2006-09-26
Installed ubuntu today for the first time.. First I used the same disk where my windows is put. Everything work out nice after some tweaking, but I found it quite "messy" to have both windows and ubuntu on the same disk. So I removed ubuntu and installed it on a separate disk instead. But when I was installing and should add users it seemed like it wouldn't add them. Every time I added a user and wrote a password the install "jumped" back to the start of adding users. So I just skipped it, believing I could add users afterwards. 

After doing the first step of the install and rebooting, install popped up a screen saying that I had to add a "admin password", so I did and got an "add user" screen afterwards. The same thing happened, everytime I tried to add a user it jumped back to the start. So I skipped the whole thing, hoping that it would work anyway.

Now it seems like everything has installed ok, but I can't log in because apparently there is no users made. Is there a way I can log in with the "admin password" I made, or a way I can add users?

---

### Post by CatKiller on 2006-09-26
The commands that you need are ```
adduser stekre
``` and ```
adduser stekre admin
```The first will create a user called "stekre" and the second will add them to the admin group, allowing you to use sudo and do administrative tasks.

To run these commands, you'll need to be running as root. I'm unsure of the mechanincs of how to do that from your situation. Perhaps the recovery mode, or whatever it's called, or the live cd? Something may come to me.

---

### Post by bluefrog on 2006-09-26
boot in recovery mode.

then 
useradd joe
passwd joe
adduser joe admin  (hopefully the admin group (1000) and has been added to the visudoer during the install).

James

---

### Post by stekre on 2006-09-26
ok, I've managed to make a user now. But when I tried to log in with the user I got an error message saying there wasn't a \home\username directory. I tried making the directory in recovery mode, seems like it kind of worked, but I get another error message saying "your $HOME\.dmrc file has incorrect permissions...." etc etc.. 

How do I fix this?

btw: it tries to log in, but fails after just a couple of seconds saying it can't make a .gnome2 directory etc..

---

### Post by stekre on 2006-09-26
Should I just reinstall it? Will be quicker than trying to fix it ^^

Reinstalled instead of trying to fix it.. Took me 15 min :) Damn it's nice to install ubuntu compared to windows :D

---

### Post by CatKiller on 2006-09-26
Well, glad you're up and running, anyway. The later problems were probably caused by you creating the file as root, so the user didn't have permission to write there. [This page]("http://www.psychocats.net/ubuntu/permissions") may get you started on how permissions work under Linux. Have fun using Ubuntu, and welcome to the community.

---

