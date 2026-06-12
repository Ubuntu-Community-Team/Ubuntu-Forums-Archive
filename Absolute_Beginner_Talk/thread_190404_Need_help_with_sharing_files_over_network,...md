---
title: "Need help with sharing files over network,.."
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by dorts on 2006-06-06
I want to share files over a network. Between a laptop using Xp and this com using ubuntu. I hear people saying about samba but I looked at some of the tutorials and it looked very complicated. Is there another way?

---

### Post by AndyCooll on 2006-06-06
Samba is probably easier than it seems, most of it you won't need to use.

However the easiest way to start is by going through administration-->Shared Folders (or something like that, I'm not at my computer at the moment). That should walk you through it.

Obviously it will be easier if your Linux and XP name, passwords and workgroups are the same.

:cool:

---

### Post by bruce89 on 2006-06-06
Not that I know of.  Samba is easy, you just goto System>Administration>Shared Folders.

---

### Post by Iowan on 2006-06-06
[QUOTE=dorts] Is there another way?[/QUOTE]FTP?  (Personally, I prefer Samba.)

---

### Post by dorts on 2006-06-06
LOL. That is Samba? I didn't know. I tried that but the files could not be seen on the XP laptop. Can someone help me with the settings. I see stuff like general windows sharing settings which I don't know what to put. Thanks for helping anyway.

---

### Post by dorts on 2006-06-06
Bump.

---

### Post by u.b.u.n.t.u on 2006-06-07
From the XP view.

* you need to enable a shared HDD or folder. Right mouse click, "properties" "share" from memory. Have a look there. It says are you sure/do you want to - yes to everything.

* if you are running a firewall you need to allow networking. I only know sygate. 

* you need to allow netbois with your ethernet connection.

I don't know how much you know of this, so I am keeping my answer brief. If you want full instructions I can fire up my XP box and just check it all.

On the ubuntu side you need to install samba and it isn't that difficult to do.

Check this thread out:

[http://www.ubuntuforums.org/showthread.php?t=180844](http://www.ubuntuforums.org/showthread.php?t=180844)

---

### Post by rcarring on 2006-06-07
Are your two machines connected to a router or to each other?

---

### Post by dorts on 2006-06-07
To a router. And the laptop is using a wireless connection

---

### Post by Fornie on 2006-06-07
hello :)

i had the same problem before...i just followed the instructions on the link and it's working now! yey! :cool: 

[https://wiki.ubuntu.com/SettingUpSam...ht=%28samba%29](https://wiki.ubuntu.com/SettingUpSam...ht=%28samba%29)

---

### Post by dorts on 2006-06-07
It says page does not exist.

---

### Post by Fornie on 2006-06-07
[QUOTE=dorts]It says page does not exist.[/QUOTE]

hmm..please try this :)

[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

---

### Post by u.b.u.n.t.u on 2006-06-07
Hi,

Here is some basic theory as I understand it.

This applies to any box you want shared via a shared router.

You need.

* folder(s) or even the HDD status changed to "share". This share can be read only or read and write.

* if you have a firewall you need to configure it to allow the connection from the other box. (Two firewalls means two sets of configuration that need to be done).

* for windows you need to enable netbios in for your ethernet connection.

* for ubuntu you need to enable samba (server and client) with a direct path to the shared folder on XP.

I know this sounds very difficult but you can break it down into steps. A person with experience can do this in under 10 minutes. So it isn't that complex, just a fair bit to do.

I gave you the link to how I did it. Pick either ubuntu or XP to start at. If you get stuck just ask here and hopefully someone can assist.

---

### Post by dorts on 2006-06-07
Thanks for the help, I will try it soon.

---

### Post by dorts on 2006-06-07
it works. i used it with my virtual xp. but i can't access my ubuntu shared folders from xp. it wants a user and pass which i type my own and doesn work.

---

### Post by u.b.u.n.t.u on 2006-06-07
So you can see XP from Ubuntu.

You cannot see Ubuntu from XP. That sounds like you need to set up Ubuntu. Check your settings. There is something there not right.

---

### Post by Iowan on 2006-06-07
If you're running **security=user** then you'll need to set up the user in Samba, too. (via smbpasswd) **security=share** might bypass the password issues (at the expense of bypassing security, too).

---

