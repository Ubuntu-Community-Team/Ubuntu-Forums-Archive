---
title: "computer name comes up UNKNOWN on router ?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by lupgop on 2008-01-06
my computer comes up with UNKOWN as the name - rather than it's set name.
I am conecting via STATIC IP so changing  /etc/dhcp3/dhclient.conf  wont help.

i have name set up in network settings under Host Name
(i also added one under Domain Name - not sure if i should have ???)

so how do i make the router see it ???

---

### Post by blueridgedog on 2008-01-06
What type of router?  Is is capable of having a "hosts" type of file?

You see, from the router's perspective it deals with IP's and can translate those IP's into computer and domain names via the DNS system.  The ISP/entity that assigned your your IP can assign a name to your IP, ie putting in what is referred to as a "reverse" but typically these have cryptic names.

Perhaps if you tell the forum more about where you are seeing the "unknown"more help can be offered (a screen shot?).

---

### Post by lupgop on 2008-01-06
?? i mean the pc name - when i look at the conections to the router the other pc's come up with there name. ie living room or study.

---

### Post by houstonbofh on 2008-01-06
Depends on the router and the mothod for the other systems.  If they are dhcp, it is getting them from the dhcp request.  If they are static, it could be getting them from NBT, which you can fake with samba.  You might want to tell us what router...

---

### Post by lupgop on 2008-01-06
it a thomson 585 .
sorry for my ignorance - what is samba ?

---

### Post by houstonbofh on 2008-01-06
Samba is fake Windows networking.  [http://samba.org](http://samba.org)  And I have never (nor am I likely to) seen your router.  Seems to be somewhat regional. :)  However, if the only difference between the systems that work, and you linux box is the fact that it is linux, try samba.  You can access it via System --> Administartion --> Shared Folders

---

### Post by Gabn on 2008-01-06
The hostname for the Ubuntu boxes are set, and yet the router recognizes them as &#8220;unknown&#8221; or &#8221; &#8220;.

I fixed this problem by editing the

/etc/dhcp3/dhclient.conf

file to uncomment the following line and editing it as follows:

send host-name "hostname"


change the word hostname inside the " " to what it's set. 

not sure where i got this information but it's part of my private wiki of useful linux information.

edit: didn't see the part about static ip .... it might still work..

---

### Post by houstonbofh on 2008-01-06
Gabn, your fix only works if you are using dhcp.  The OP said it was a static address.  :)  Good information, but not applicable in this case.  Also, as of Gutsy (perhaps Feisty) it is set by default.

---

