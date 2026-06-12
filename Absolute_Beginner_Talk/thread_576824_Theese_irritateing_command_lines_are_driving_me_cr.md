---
title: "Theese irritateing command lines are driving me crazy!"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by DevEight on 2007-10-15
I'm REALLY tired of this sudo stuff, is there absolutely no way of giving yourself root privileges and just skipping the whole sudo stuff?

I can't even move File1 in Folder1 to Folder2.

I also tried the cp commands etc and they didn't work as expected and it's tiresome to type/copypaste filepaths all day long.

I also tried sudo chown me *.* but that wouldn't do it. :D

So could someone please help me so that I at least can drag folders around without it bitching about permission?

---

### Post by floke on 2007-10-15
sudo apt-get install windows?

:frown:

---

### Post by Pumalite on 2007-10-15
It's for your own security.
You can try: sudo su
Or sudo -i

---

### Post by rsambuca on 2007-10-15
You can open the Nautilus file browser with root privileges:```
gksudo nautilus
```

---

### Post by philinux on 2007-10-15
Try gksudo nautilus you can copy and past for fun **anywhere**. But just be careful with it. You could even make a custom launcher for to avoid launching it from the terminal.

Using sudo means your system stays that bit safer from accidental cock ups and the like.

---

### Post by LowSky on 2007-10-15
> **DevEight said:**
> I'm REALLY tired of this sudo stuff, is there absolutely no way of giving yourself root privileges and just skipping the whole sudo stuff?

I can't even move File1 in Folder1 to Folder2.

I also tried the cp commands etc and they didn't work as expected and it's tiresome to type/copypaste filepaths all day long.

I also tried sudo chown me *.* but that wouldn't do it. :D

So could someone please help me so that I at least can drag folders around without it bitching about permission?

the command ```
sudo -i
```
 will make your computer a super root user for about 15 minutes.

---

### Post by DevEight on 2007-10-15
> **floke said:**
> sudo apt-get install windows?

:frown:

Haha. :D

I mean still though, if I'm the only one using my own computer and there barely are any viruses/etc against Ubuntu, who the hell is going to destroy my computer?

Tried a few other things and it still won't let me move the folder, only 1 file at a time and at this rate it's going to take all night.

---

### Post by LowSky on 2007-10-15
> **philinux said:**
> 
Using sudo means your system stays that bit safer from accidental cock ups and the like.

i think you meant lock ups...get you mind out of the gutter.....lol

---

### Post by kamitsukai on 2007-10-15
> **floke said:**
> sudo apt-get install windows?

:frown:

i loled:lolflag:

---

### Post by troy1of2 on 2007-10-15
> **floke said:**
> sudo apt-get install windows?

:frown:

Egads! I think I'm going to be sick.

:shock:

---

### Post by DevEight on 2007-10-15
> **rsambuca said:**
> You can open the Nautilus file browser with root privileges:```
gksudo nautilus
```

Thanks! Really saved me a lot of trouble when moving files!

---

### Post by yabbies on 2007-10-15
It's very dangerous by being permanent root.

read [this ]("https://help.ubuntu.com/community/RootSudo") to help you along.

At the bottom of the doc there is a how to on sudo drag and drop

---

### Post by LowSky on 2007-10-15
> **DevEight said:**
> Haha. :D

I mean still though, if I'm the only one using my own computer and there barely are any viruses/etc against Ubuntu, who the hell is going to destroy my computer?

Tried a few other things and it still won't let me move the folder, only 1 file at a time and at this rate it's going to take all night.

may I ask what are you moving and why you need root privaleges to do so?

---

### Post by Doppler on 2007-10-15
I believe if you type "sudo passwd", it lets you make a root password. Thereafter, you can "su root" in terminal to be root or log in root with the session log in with the password you set. The sudo password will be unaffected.

---

### Post by floke on 2007-10-15
I use the gksu nautilus - and its not so much the risk of viri/uses as much as its is you screwing things up by mistake - I've seen people kill their system by mistakenly deleting system files!

---

### Post by DevEight on 2007-10-15
> **LowSky said:**
> may I ask what are you moving and why you need root privaleges to do so?

Just got WoW up and running and I wanted to install a few AddOns but it wouldn't let me move them. :(

---

### Post by tubasoldier on 2007-10-15
There is also another way you may accomplish your task.

you have to have ssh installed.

Click on the menu --> Places --> Connect to Server

basically you will connect as root to localhost or 127.0.0.1

Then it will be mounted and appear as a folder on your desktop and you will have all rights to it.

Of course you will have to have the root account activated. which means you can use just "su" in the command line. GASP! the best way to do that is simply type in "sudo bash" and then "passwd". Set the root password and your on your way.

---

### Post by aysiu on 2007-10-15
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Duck2006 on 2007-10-15
&#65279;Log in to your normal Ubuntu home.

click System/Admin, and click on Users and Groups. 
on the prompt, give your regular password.

open root. 
change root password to yours. click Priviledges, and mark them all.

go to System/Admin, 
and click Login Window

change the security section to allow local root login.

exit.

reboot.

login as root, password, 
and have fun!

---

### Post by DevEight on 2007-10-15
Thanks a lot for all the help. :)

Just a question about the sudo -i thingie - it's supposed to make me root for like 15 minutes, right?
I ran the command, tried to drag a folder without the gksudo nautilus command but it still wouldn't let me. Do I need to add something after the -i or how does that command work?

---

### Post by tdrusk on 2007-10-15
what's the difference between gksudo nautilus and just sudo nautilus?

---

### Post by akiratheoni on 2007-10-15
I don't think there is a noticeable difference, but if you're running a graphical app, it's safer to use gksu or gksudo, not sudo. Lol I don't know why exactly but that's what I heard.

---

### Post by rsambuca on 2007-10-15
You should use gksudo (or just gksu) whenever you need to run a graphical based program that requires root privileges.  Basically if you run the command in a terminal and another window opens, use gksudo.

---

### Post by steve.horsley on 2007-10-15
Not exactly. When you use sudo to run a command as root. it asks for your password just to maks sure its you and not a passser by while you're gone to get a coffee. After that, for the next 15 minutes you can use sudo without being asked for your password again. This reduces the irritation level, but I still fond typing sudo irritating, so I use sudo -i. What this does is to launch a secondary command prompt with root priviledge. As it is a full blooded root prompt, it does everything as root, and will remain a root prompt until you exit it. Don't forget to exit it when you've finished doing your sysadmin work and return to being a normal user.

Doing sudo -i or gksudo nautilus before doing sysadmin work is a small price to pay for the extra security that separating users and sysadmin roles provides.

---

### Post by rsambuca on 2007-10-15
> **akiratheoni said:**
> I don't think there is a noticeable difference, but if you're running a graphical app, it's safer to use gksu or gksudo, not sudo. Lol I don't know why exactly but that's what I heard.

In a few rare cases, running a graphical based up with just sudo can bork your system by messing some permissions.

---

### Post by aysiu on 2007-10-15
```
sudo -i
``` is for when you're running terminal commands. It logs you in as root for all functional purposes until you exit. So instead of typing ```
sudo firstcommand
sudo secondcommand
sudo thirdcommand
sudo fourthcommand
``` you would type ```
sudo -i
firstcommand
secondcommand
thirdcommand
fourthcommand
exit
``` If you want to do drag and drop, press Alt-F2 and type ```
gksudo nautilus
``` This will launch a graphical file browser as root, and it's not just for fifteen minutes--it's pretty much until you close the window.

If you don't know the difference between *sudo* and *gksudo*, read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by por100pre1 on 2007-10-15
DevEight, to make it apparently easier for you won't be without a price. You could end up having lots of files and folders with wrong permissions and you could end up breaking your own system! All the previous suggestions were given to you to make you happy, not because they are the best way to do. It is NOT safe to be root if you don't really know what you are doing. You have been warned.

---

