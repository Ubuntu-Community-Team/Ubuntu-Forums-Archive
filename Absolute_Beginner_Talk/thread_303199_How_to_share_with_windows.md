---
title: "How to share with windows"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by goldenatom on 2006-11-19
Whats the easiest way to share files over a local network with windows?

---

### Post by deanlinkous on 2006-11-19
right click, choose share!

---

### Post by taurus on 2006-11-19
samba

---

### Post by goldenatom on 2006-11-19
I have a shared folder on windows, how do I access it from my linux box? I tried connecting to a server under "Places." Ubuntu couldn't access the folder though. My windows box shares fine with my iBook and another windows machine, but I can't figure it out on Ubuntu...

---

### Post by taurus on 2006-11-19
> **goldenatom said:**
> I have a shared folder on windows, how do I access it from my linux box? I tried connecting to a server under "Places." Ubuntu couldn't access the folder though. My windows box shares fine with my iBook and another windows machine, but I can't figure it out on Ubuntu...
Samba...

---

### Post by deanlinkous on 2006-11-19
>places>network Servers

---

### Post by goldenatom on 2006-11-19
Perhaps you could explain Samba to me...

---

### Post by sloggerkhan on 2006-11-19
My comp seems to see windows workgroups, but errors connecting to them.

---

### Post by shanepardue on 2006-11-19
System > Administration > Shared Folders. That will share your folders across
 a windows network or even all linux computers. From the other computers, you
 go to Places > Network Servers and double click the folders til you get to your 
shared folders.

---

### Post by sloggerkhan on 2006-11-19
I figured it out... I just had to hit refresh a few times because it doesn't load quite right the first time. Don't know why.

---

### Post by sloggerkhan on 2006-11-19
Yeah, it works, (simple to use, too) but it's quite unstable.

---

### Post by shanepardue on 2006-11-19
I recommend SSH. Very simple to set up, very secure, and very stable.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by deanlinkous on 2006-11-19
unstable?

---

### Post by john262 on 2006-11-20
> I figured it out... I just had to hit refresh a few times because it doesn't load quite right the first time. Don't know why.
I am getting that same problem too. I have to refresh it, sometimes more than once, and finally my Windows machines are accessible over my home network. 

I'm using Edgy. Is this a bug? Or can this behavior be fixed somehow? I have already installed Samba, etc., and I set up a password so that I can log on to my Ubuntu box's shared folder from either of my Windows boxes without any problem, but when I try to log on to a Windows machine from Ubuntu I usually have to refresh the network file browser to get it to work.

Thanks for your help. John

---

### Post by flameproof on 2006-11-20
Funny, I have no Problem getting from the Ubu to the Xp data. However, I can not get from the Xp PC to the Ubu machine. 

Sometimes I can see the shared folder, but it asked me for a login and password when I click the folder. So far all login attempts failed.

How do I get rid of that login/password?

---

### Post by goldenatom on 2006-11-20
Same problem here...I couldn't get the shared folder to show up on Ubuntu at all, but when I turned both machines on this morning, it just worked. I did reboot both machines last night when I was attempting to get all this working before.

---

### Post by sloggerkhan on 2006-11-20
What I mean by unstable is that at every level of network navigation I must refressh anywhere from 1-7 times to get all node/machines to show up properly, sometimes the process goes dead, and I have to open a new browser window and start at the begining, and when I do connect to a windows shared folder, sometimes the connection collapses in the middle of an opperation, particularly if I am transfering a file and browse to another directory on the shared folder before the transfer is complete.

---

### Post by cdinoz on 2006-11-29
This is true - this is exactly what you have to do - keep hitting refresh until it finds the windows shares - but why??

---

