---
title: "iMac G3 - can't log in, username/pass not found"
date: 2009-08-15
forum: Apple Hardware Users
---

### Post by eric123abacus on 2009-08-15
Hi all,
First post here. Relatively experienced with linux, dual-booting on my intel macbook and all. 

Trying to install Xubuntu 9.04 PPC Alternate on my old iMac G3. Installation goes fine and i set up a username and password but when I boot up to the login screen and try entering them it says username/pass is incorrect. 

Capslock is off, the keys are producing the right letters in the textbox. I tried logging in on a terminal too and that produces the same result. I've even tried re-installing 3 different times with 3 different usernames and passwords and none work. Installation takes like 5 hours so I'd prefer not to have to do it again. 

Can anyone help me get logged in here? My bootloader is Yaboot if you need to know. This computer is for my little brother so anyone helping me would be helping to introduce a teenager to the joys of linux.

Thanks so much for the help!!!!!!

---

### Post by ademonk on 2009-11-03
Having exactly same problems.
 
I have reinstalled several times. Certainly not 5hrs, more like 30mins.
 
Tried expert install in attempt to wipe hard disk, thinking old password files might be confusing system.
 
I did find help to reset forgotten passwords but that talked about GRUB loader, not the YABOOT used with mac. Somehow need to find a 'recovery' mode so can access a root login.
 
Still work in progress.
 
Question? - Did you do anything odd to install? My first installation failed with message "Invalid ROM contents" but did allow me to login. I then installed with option 'install video=ofonly' After that no rom errors but now cannot login.

---

### Post by roym4 on 2009-11-03
We've seen similar problems where the installation would fail (usually at the install software step). We'd resume the installation and it would appear to complete the installation fine. However it would not recognize the username/password. 

We found that setting the correct date in open firmware before the installation would prevent these failures and the installation would work correctly - no failure at login.

---

### Post by oswaldkelso on 2009-11-03
> **roym4 said:**
> We've seen similar problems where the installation would fail (usually at the install software step). We'd resume the installation and it would appear to complete the installation fine. However it would not recognize the username/password. 

We found that setting the correct date in open firmware before the installation would prevent these failures and the installation would work correctly - no failure at login.

[http://forums.debian.net/viewtopic.php?f=17&t=46527](http://forums.debian.net/viewtopic.php?f=17&t=46527)

Other options

You could try booting into rescue mode if it's the same as Debian?

also to get root try ctl+alt+F1 

```
sudo -i 
```

and see if you get root access.  ( I can't remember exactly the situation I used that so google)

---

### Post by Vlammetje on 2009-11-04
Yes, there is a thread around here about that, it seems the 9.304 alternate does not create the user (try a live disk, you will probably find no /home directories created for you user either) 

I'll go find a link to that thread (and yes I'm having the same problem on an iBook G3, have not been bale to solve it as yet, nor have I succeeded at any other installations of other distros)

---

### Post by Vlammetje on 2009-11-04
[http://ubuntuforums.org/showthread.php?t=1126463](http://ubuntuforums.org/showthread.php?t=1126463) have a read through this topic, it will explain how to (re)create users and passwords and so on. Be carefull with shadow passwords, having those on prevented me from deleting any test users I had added.

---

### Post by ademonk on 2009-11-07
> **roym4 said:**
> We've seen similar problems where the installation would fail (usually at the install software step). We'd resume the installation and it would appear to complete the installation fine. However it would not recognize the username/password. 

We found that setting the correct date in open firmware before the installation would prevent these failures and the installation would work correctly - no failure at login.


Yes, setting the correct date before yet another install, did the trick but, wow, was it hard to find instructions about using 'open firmware' so for anyone else reading this thread, to access the G3 iMac open firmware:

Reboot machine and hold command-option-O-F during the boot process.
Hear a chime and get the open firmware prompt.
Use time&date command to set correct time and date; time&date hh:mm:ss mm/dd/yy
The open firmware prompt should respond ok
and you can boot the mac typing mac-boot and pressing Enter.

---

