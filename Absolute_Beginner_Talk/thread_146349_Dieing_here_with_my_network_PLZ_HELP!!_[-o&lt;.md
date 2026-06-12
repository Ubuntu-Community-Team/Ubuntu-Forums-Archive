---
title: "Dieing here with my network_PLZ HELP!! [-o&lt;"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by dodge78 on 2006-03-18
Hi there,
Firstly, Im new to Linux (Ubuntu) and love it so far :-D , but right now Im having serious issues with trying to get it networked with my XP box. I have pretty much tried every thing: mounting manualy, mounting with the wizard (if you want to call it that), I even had a friend come over and try to network it, he got it to work and then with out me look upgarded Ubuntu to 6.04, Dapper Drake! :mad: . Now no matter what i try now i get 
qutoe:
"smb://MSHOME%3BAdministrator@192.168.2.100/c" is not a valid location.
Please check the spelling and try again.

thats one of them i have tried about every combination you can think of. Still cant get it to work. Thinking it might be a Samba issue (after the unwanted upgrade) I reinstalled Samba, still nothing. Whats wierd is that I can print from Ubuntu, thou the printer is connected to the XP box.:confused: 
Every thing is connected to a Lynsys router Internet works fine configuration correct no issues their.

Someone Plz Help [-o<

---

### Post by chuckyp on 2006-03-18
What if you try to just browse tot he share via. gnome i.e. Places>Network Servers>Whatever?

---

### Post by Jimmey on 2006-03-18
I'd not advise using Dapper Drake.

I'd make sure that the XP box you're trying to connect to has a static LAN IP.  You can get some information on how to do this [here.]("http://www.portforward.com")

Then, you want to make sure that the Ubuntu box can see the XP one - 

> ping wxp.box.ip.addy 
( Replacing 'wxp.box.ip.addy' with the new IP ).

Then try again.

---

### Post by dodge78 on 2006-03-18
i try to acces the Windows Network icon and i get:

"smb:///" is not a valid location
Please check the spelling and try again.

and that was set up by Ubuntu

---

### Post by dodge78 on 2006-03-18
[QUOTE=Jimmey]I'd not advise using Dapper Drake.

I'd make sure that the XP box you're trying to connect to has a static LAN IP.  You can get some information on how to do this [here.]("http://www.portforward.com")

Then, you want to make sure that the Ubuntu box can see the XP one - 


( Replacing 'wxp.box.ip.addy' with the new IP ).

Then try again.[/QUOTE]
i can ping the XP box fine but cant access it

---

