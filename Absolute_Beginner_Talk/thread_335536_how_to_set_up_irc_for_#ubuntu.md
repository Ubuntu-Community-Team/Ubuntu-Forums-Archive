---
title: "how to set up irc for #ubuntu"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by calypsogal on 2007-01-10
Hi I'm totally new to this, and to anything much beyond simple basics of XP. My ex boyfriend set me up with Ubuntu and i love the system interface and the fact that it's free, but i'm struggling with my learning curve. I'm trying to set up IRC to those who can help me when i'm pullin out my hair. 

First question:what does #ubuntu mean?

I'm apparently connected to freenode.net

I've followed the help to gaim setup and have a box pop up with my name in freenode.net, but it says i'm not registered? how do i register?

thanks so much all you gurus :D

---

### Post by jvc26 on 2007-01-10
To connect to IRC on #Ubuntu:
Download Xchat Instructions are here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_IRC_Client_.28XChat.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_IRC_Client_.28XChat.29)

Or below:
Go into terminal (applications->accessories->terminal)
Type:
```

sudo apt-get install xchat xchat-systray 

```
If it says that it cant find the package, follow the instructions here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

Then type:
```

sudo apt-get update
sudo apt-get install xchat xchat-systray 

```

It will ask you for a password (your user password) put it in and press enter, there isnt something wrong when *s dont show up, or dots or anything - that is normal.

Then go to:
Applications -> Internet -> XChat IRC

Once you have loaded Xchat it will ask for nickname and your real name etc. Then go to the server list below the names list. Here select Ubuntu Servers and then select 'connect' It will check your id and then should load you into #ubuntu.

Hope that helps,
Il

---

### Post by Seine on 2007-01-10
Once you're connected to freenode.net you can just type ```
/join #ubuntu
```. That should work for you. :)

---

### Post by xpod on 2007-01-10
Or theres always "#ubuntuforums":mrgreen:

---

### Post by calypsogal on 2007-01-10
thanks all I got on, but it look like the forums are probably a better place to get my answers for my next quest. I'm looking for a program that mimics ibook for ubuntu? 
i'll have to start another thread.

cheers

---

