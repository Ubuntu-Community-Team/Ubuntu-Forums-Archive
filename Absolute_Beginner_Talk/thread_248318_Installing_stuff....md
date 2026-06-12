---
title: "Installing stuff... ?"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Zoolook on 2006-08-31
I installed Ubuntu about 2 hours ago but am getting quickly dispondent about installing additional applications.

I have failed miserably to install RealPlayer, Flash or Java.  The problem seems to be getting the relevant plugin files into the Mozilla plugin folder.  I eventually found this folder in /usr/lib/ but have no permissions to put the files there.

Can someone tell me how to do this?

I have to say the user guides on the Mozilla site and on the Ubuntu wiki are not helpful because they both assume that a newbie user will be able to move the files around using the terminal as root, but I don't feel confident doing this. You cannot log in as root using Gnome by the looks of things.

---

### Post by jordanmthomas on 2006-08-31
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Be sure to read the section on adding new repositories.  Everything here is just cut and paste.  (Which you can do by selecting and then middle-clicking in a terminal)

I'd just like to say that you should pay attention to what the guide has you do as it will help you learn how to install software yourself without having to go to a page that tells you how.

---

### Post by Zoolook on 2006-08-31
I really appreciate the swift reply.  I'll read up and try again. :p

---

### Post by blent07 on 2006-08-31
Anything you do in terminal that says you don't have permission to do, type: sudo and it'll ask for your password (when you type the password, it'll appear blank but it's actually typing, that got me for a bit).
If launching an application through terminal, use gksudo, not sudo. 

Also, search for EasyUbuntu or Automatrix, both are great for getting a lot of necessary stuff installed (i.e. playing mp3s). I'm not positive if they do plugins for Firefox, but I'm willing to bet they do. 

And when you install realplayer, make sure to type "sudo apt-get install realplay" Notice it's realplay, not realplayER. Realplayer gives you an older version (8, i believe, not 10)

Finally, i don't know what method you used to get the plugins, but using Synaptic Manager (just search for 'firefox plugin') and when you install, they should install themselves into the correct directories. Least, it seems to have with me. 

Hope something I said helps.

---

### Post by Zoolook on 2006-09-01
I get this error

hallmr@hallmr-laptop:~$
hallmr@hallmr-laptop:~$ sudo apt-get install realplay
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package realplay
hallmr@hallmr-laptop:~$
hallmr@hallmr-laptop:~$

---

### Post by jordanmthomas on 2006-09-01
Did you read this part by any chance?

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

### Post by blent07 on 2006-09-01
jordanmthomas is right, the page says:

Note: 'realplay' installs RealPlayer 10 from PLF repository, which you should be enabled if you followed this guide. 'realplayer' installs RealPlayer 8 from multiverse.

So make sure when you add the repositories, you add the PLF. Go to the link jordanmthomas posted, and there, find and click "add repositories using synaptic package manager." it's a bit easier. There it tells you how to add each other individually and adding PLF and backports repositories. 

it should make it a bit clearer if you're unfamiliar with the terminal.

---

### Post by Zoolook on 2006-09-01
I actually added everything possible to the synaptic package manager, I ticked everything... :D 

There still was no package called RealPlayer or Realplay (I was looking under Media and Media (Universe).

I must be doing something fundamentally wrong, so I'll try again later.

I have a very general question.  In which directory are applications generally installed?  If I want to manually install something and have it avaiable to all users, where is the best place to put it?

---

### Post by Mimsy on 2006-09-01
> **blent07 said:**
> 
If launching an application through terminal, use gksudo, not sudo. 


Really? When I needed to edit a file in one of the Filesystem folders last night I simply typed "sudo gedit", since I didn't know about the gksudo, and it launched the application just fine. The GUI was there, the functionality (I could edit the file no problem), what is the difference?

I'm morbildy curious about new things, and this fascinates me. If you must use gksudo to lanch an applicaiton, how come sudo worked?

/Mimsy

---

### Post by Zoolook on 2006-09-01
This is why:

NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username. 

From 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Mimsy on 2006-09-01
Oh. I'll make sure to use gksudo from now on then.

Thanks!

/Mimsy

---

### Post by blent07 on 2006-09-03
^^^ what he said. It can break the .ICE authority file. I've used sudo gedit before, too. But then I learned otherwise. 

Zoolook, if you want to install reaplayer 10 from Synaptic, then just search for "reaplay" and it lists both versions.

---

### Post by Zoolook on 2006-09-03
I've gotten my head around the package manager, it's very simple and I guess made for windows newbies like myself.  I'd like to understand what is happening though under the bonnet, but I can learn that as I go.

I am having difficulty installing Acrobate Reader, it tells we it is incompatable with me system and a software channel is not open.  Trying to get around that.

My only other issue is nothing to replace Microsoft Money.  GNUcash looks ok, but I am probably going to have to start from scratch as importing looks impossible.  MS Money is one of Microsoft's best programmes, IMO - but it integrates so heavily with IE that running it under WINE is very hard.

---

### Post by dreamsayer on 2006-09-03
> **Zoolook said:**
> I installed Ubuntu about 2 hours ago but am getting quickly dispondent about installing additional applications.

I have failed miserably to install RealPlayer, Flash or Java.  The problem seems to be getting the relevant plugin files into the Mozilla plugin folder.  I eventually found this folder in /usr/lib/ but have no permissions to put the files there.

Can someone tell me how to do this?

I have to say the user guides on the Mozilla site and on the Ubuntu wiki are not helpful because they both assume that a newbie user will be able to move the files around using the terminal as root, but I don't feel confident doing this. You cannot log in as root using Gnome by the looks of things.

The easiest way to get the all the apps installed you mentioned, plus many more is to use automatix. It's really easy. Even a newb like me was able to do it! :) 
[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

It will install your nvidia or ati video drivers, as well as all the other cool multimedia stuff needed to get a killer ubuntu box!

---

