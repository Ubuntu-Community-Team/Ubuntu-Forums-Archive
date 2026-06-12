---
title: "Networking"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-09-15
Hi guys, 
I am having trouble with networking. I am trying to connect ubuntu with win xp I followed Stormbringer's samba peer to peer networking guide and am able to access ubuntu from window by mapping a network drive however I am un able to access windows from ubuntu when I open Network Servers it shows Windows Network and inside it is mshome but when I open that it only shows ubunto not my xp box. Can someone please help me with this.

Thanks,
Rameez.

PS: I can access internet from my XP box without any problem.

---

### Post by Najand on 2006-09-15
Can't you access it using:
Places -> Connect to server 
Service type: Windows Share
Server: \\WINDOWS_COMPUTER_NAME (Change WINDOWS_COMPUTER_NAME with your computer name)
Username and Domain name: If Neccessory.

---

### Post by TiredBird on 2006-09-15
I have a similar home network - Ubuntu 6.06 mixed with Win XP.

I followed Stormbringer's excellent 'howto' in setting up Samba. It worked as  he said it would.

One thing I notice in your post is the reference to 'mshome'. In Stormbringer's 'howto' he used 'mshome' as the name for his workgroup but mine was different, yours may be too. 

Samba should have the same workgroup as the XP(s).

Samba works but it's tricky.](*,)

---

### Post by rameez on 2006-09-15
no I can't

I have a workgroup not a domain names MSHOME

Edit: both of them have the same workgroup: MSHOME
Before I upgraded to 6.06 the it was working fine

---

