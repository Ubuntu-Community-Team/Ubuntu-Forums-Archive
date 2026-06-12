---
title: "power failure during update"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by brewer on 2007-08-07
I had an power surge while updating and seem to need a "superuser privilege" to run the command lines in the terminal having trouble finding out what that is or how to get it my package manager  and updater are unuseable I am using Feisty Fawn 7.04

---

### Post by overdrank on 2007-08-07
> **brewer said:**
> I had an power surge while updating and seem to need a "superuser privilege" to run the command lines in the terminal having trouble finding out what that is or how to get it my package manager  and updater are unuseable I am using Feisty Fawn 7.04

HI in the terminal use the command
```
sudo apt-get update
```
Post back if you get errors!

---

### Post by Brunellus on 2007-08-07
for an explanation of superuser privileges (and user privileges in general) see

[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

you could then try getting the upgrade running again.  from the command-line, that's

sudo aptitude upgrade

or you can run synaptic and do it graphically--assuming you you have a GUI.

---

### Post by brewer on 2007-08-07
> **overdrank said:**
> HI in the terminal use the command
```
sudo apt-get update
```
Post back if you get errors!

thank you but it is when I type that in it then tells me I need superuser privileges I cannot find out what these are or how to obtain

---

### Post by Brunellus on 2007-08-07
> **brewer said:**
> thank you but it is when I type that in it then tells me I need superuser privileges I cannot find out what these are or how to obtain
please read the wiki page I linked you in my first post

---

### Post by lisati on 2007-08-07
> **brewer said:**
> thank you but it is when I type that in it then tells me I need superuser privileges I cannot find out what these are or how to obtain

Part of the design philosophy of Ubuntu and other similar Linux-based platforms is the idea that it's a good idea to protect your computer against damage, whether by accident or by someone being malicious. One of the ways Linux achieves this is by only allowing a "super user" to perform certain things, everyone else is blocked. The "sudo" you will see in front of many commands mentioned in these forums is the way your typical system administrator gains temporary "super user" powers.  When used it will ask you for a password. Don't panic if nothing shows on the screen when you type in your response - your response WILL be recorded.

NOTE: you will normally only be able to use "sudo" if you are currently logged on as a "system administrator" (usually the user account you set up when you first installed *ubuntu.)

It might be a nuisance at times, but it's there for your protection.

---

### Post by brewer on 2007-08-07
Thanks a lot for your time I guess I am in over my head I am going to save files and format and reinstall .One question is Beryle something I should leave out?

---

### Post by overdrank on 2007-08-07
> **brewer said:**
> Thanks a lot for your time I guess I am in over my head I am going to save files and format and reinstall .One question is Beryle something I should leave out?

Hi as to the posted link just use 
```
sudo -s  
```
And this will give you root privileges during that session. As for Beryl I use and comp-fusion so it is up to the User. :popcorn:

---

### Post by Brunellus on 2007-08-07
> **brewer said:**
> Thanks a lot for your time I guess I am in over my head I am going to save files and format and reinstall .One question is Beryle something I should leave out?
see my sig.

---

