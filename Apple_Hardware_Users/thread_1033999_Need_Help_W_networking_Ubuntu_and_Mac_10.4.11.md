---
title: "Need Help W/ networking Ubuntu and Mac 10.4.11"
date: 2009-01-07
forum: Apple Hardware Users
---

### Post by ghostofzuul on 2009-01-07
Hello, 

newbie here so bear with me...

i got the network up and running and I can see the ubuntu machine from my mac and when I first did it I could see the mac from the ubuntu machine. Now I've restarted the ubuntu machine and I can't see the mac. but i can still see th ubuntu machine.

My network connection is working as I'm using it to access the internet...

any help would be great...

sorry i don't know what i'm talking about really yet...

---

### Post by ghostofzuul on 2009-01-08
Now I can't access the ubuntu machine from the mac either. I could before, now it won't login at all.

Kind of frustrating. However, I can now see the mac from the ubuntu box. and vice versa. just can't access either one.

---

### Post by tiresia on 2009-01-08
Can you please be more specific? Describe please your network (I guess you have a router), and what do you mean with 'I can see the Mac from ubuntu box'. Which programm do you use?

---

### Post by ghostofzuul on 2009-01-08
> **tiresia said:**
> Can you please be more specific? Describe please your network (I guess you have a router), and what do you mean with 'I can see the Mac from ubuntu box'. Which programm do you use?

I have a Mac running 10.4.11 an Linux Machine running Ubuntu 8.04 and a linksys router. 

The problem I'm having more specifically is this.

On my Mac, when you click on "Network" I can see the Linux machine. When I click on the link to connect me to the Linux machine it gives me a protocol to fill in "User Name" "Password" 
The "user name" "password" i created in samba doesn't exist. If i go to the Linux machine and create a new samba user and password it doesn't matter. I can never login from the mac into the linux machine. 

From the linux machine, I can't see the Mac at all. I saw it once and clicked on it and was unable to login. After restart of linux machine, haven't been able to see Mac on network since. 

Sorry. Just started using Linux today, really not sure what the right terminology is.

---

### Post by tiresia on 2009-01-08
You should first allow to a user the access. Therefore. on your Mac, go the System Preferences > Shared and select File Sharing (if you want to access the Files on your Mac). 
[Actually I don't remember anymore how it is on Tiger, maybe someone has still Tiger on his computer and can help you more, or you can google a bit if you need - but it sould be quite easy to do it on a Mac]
Please, tell me, if it works, then we can try the other way (from Mac to Ubuntu)

---

### Post by ghostofzuul on 2009-01-08
> **tiresia said:**
> You should first allow to a user the access. Therefore. on your Mac, go the System Preferences > Shared and select File Sharing (if you want to access the Files on your Mac). 
[Actually I don't remember anymore how it is on Tiger, maybe someone has still Tiger on his computer and can help you more, or you can google a bit if you need - but it sould be quite easy to do it on a Mac]
Please, tell me, if it works, then we can try the other way (from Mac to Ubuntu)

Hi. thanks for your help. File sharing is "ON" on the MAC. If I change the folders on my linux box so that it's using "guest access for those without account" than I can access the folders on the linux box from my Mac, but I still can't access the Mac from my linux box. Also, would like to have security and not have to use "guest" as only way to view files.

Also seems if I goto the network Icon in the panel and check and uncheck "enable network" and then restart then I can see the Mac from my linux box. But should I have to do that every time?

Thanks  again.

---

### Post by tiresia on 2009-01-08
There are two ways (protocols) to set a network for file sharing between a Mac and a Linux: Samba and Apple Talk (the implementation of it for Linux being Netatalk). Though Apple Talk was 'native' developed for macintosh computers, I suggest you to use Samba - it can be also easier for you.

When you share Files between two computers, in *both* directions, both computers act as client and server at the same time. Both Mac and Ubuntu are ready to connect to other computers as client, but they need to be configured as server -  the Mac enabling it in Share as you did, Ubuntu installing a package.

**UBUNTU AS SAMBA SERVER**
Here is a link where you will learn everything you need about this. 
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

In Ubuntu 8 it's quite easy to share a Folder. Right-click on the Icon and Choose 'Sharing Options'.

**MAC AS SAMBA SERVER**
[http://docs.info.apple.com/article.html?path=Mac/10.4/en/mh1161.html](http://docs.info.apple.com/article.html?path=Mac/10.4/en/mh1161.html)

---

