---
title: "HELP - no or little permissions on upgrade 7.10?"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by smortaus on 2007-11-03
From a New User -

Hi all – I am a new user of Ubuntu – I installed Ubuntu when it was 7.04 – The problem is that – when we did the upgrade from 7.04 to 7.10.. We ended up with permission issues everywhere and I mean everywhere !

The system has taken away most of our rights to adjust stuff – like screen resolution's – mounting HD’s -  and most importantly the ability to mount our card reader that I require every day so as I can up load photos to my system.

I have very little understanding of the terminal command lines and I find it almost impossible to do anything in SUDO... I can log in as SU when in terminal.. but importantly don’t have enougth knowledge to know what I am doing.

I am still trying to come to terms with the basic commands and really can’t find much information on absolute beginners guide to command language. 

The most outstanding thing I have on 7.10 is this bloody permission thing – On 7.04 I had no issues at all until I installed 7.10 then the hell started.

Question is... Is there an issue with the upgrade 7.04 to 7.10 when it came to permissions?

Is there a way a can regain permissions on my System ?

Is there a quick patch to rectify the damage 7.10 did?

Or would it be easier to reload the system?

Like I said ... extremely low knowledge on Command line stuff... So if possible can any answers be in complete dummies guide type answers.

Regards 
Danny

---

### Post by gate on 2007-11-03
OK, if you  want to avoid the command line: do you have access to system->administration->users and groups?

 if so, look at your user and click properties, then look at user privileges and make sure you have all the ones you need checked,

---

### Post by haldean on 2007-11-03
That's a new one for me - it sounds like when you upgraded, you were removed from a bunch of groups. You can fix this by running ```
sudo users-admin
``` which will open the Users and Groups menu. Select your username, press "Properties" -> "User Priveleges", and check all the boxes. Restart your computer and see if that works.

---

