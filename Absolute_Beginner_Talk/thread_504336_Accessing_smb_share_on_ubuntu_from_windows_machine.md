---
title: "Accessing smb share on ubuntu from windows machine."
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by gig2856 on 2007-07-19
I have 2 computers behind a router, WinXP and Ubuntu 7.04 Server
I have this shared folder on Ubuntu: /home/user/Desktop/sharedfolder

So from my XP machine I type "\\ubuntu\home\user\Desktop\sharedfolder" and it gives me a login prompt.  "ubuntu" is what i named the server when i set it up last night, I really havent had time to configure much on it yet.  Now the login box looks like this:[http://img201.imageshack.us/img201/7060/smbloginwl1.jpg]("http://img201.imageshack.us/img201/7060/smbloginwl1.jpg")

It puts the lv.cox.net after the computer name.  Obviously cox is my cable provider, but I'm not sure why it would be like that since I'm on my own private network.  Anyway, I try logging in with my normal user that is setup on the ubuntu machine (root is shown in the picture, i tried both) and the corresponding passwords, but no dice, it just brings up the login box again each time I try to login.  So it isnt authenticating I suppose.

Just to test, I went onto my ubuntu box and removed lv.cox.net from the DNS settings and tried again but I still cant get in.


My question: What am I doing wrong here?  Is this the correct way to access a samba share on a linux box from Windows?

Btw, I can access my windows shares from Ubuntu just fine.
Any help would be appreciated.

Thanks

---

### Post by kilkraze on 2007-07-19
I just want to make sure, did you add the samba users as well?

---

### Post by gig2856 on 2007-07-19
> **kilkraze said:**
> I just want to make sure, did you add the samba users as well?

Figures I would miss something..
I did a search for adding samba users and found [this page.]("http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/")
After adding a user it works now :)  I just dont know how I was supposed to know you need to edit smbusers to setup access...

Any ideas on the dns adding lv.cox.net to my server name?  It it ok that I got rid of that?

Thanks

---

### Post by kilkraze on 2007-07-19
I am assuming (correct me if i am wrong) that the cable provider provided the router as well, and that a domain with the name lv.cox.net is set up on the router. If this is true, you can log into the router and change the domain to whatever you like, or remove it altogether.

---

### Post by gig2856 on 2007-07-19
> **kilkraze said:**
> I am assuming (correct me if i am wrong) that the cable provider provided the router as well, and that a domain with the name lv.cox.net is set up on the router. If this is true, you can log into the router and change the domain to whatever you like, or remove it altogether.

Nah, I own the router (which is running DD-WRT firmware).  lv.cox.net is the WAN domain name (given out by Cox dhcp).  I actually just checked the router settings for DHCP/DNS and there is an option called "Used domain" which was set to "WAN".  The setting details say that this is the domain that dhcp clients will get as their local domain.
Anyway, I changed the setting to LAN domain, which is blank anyway.  So that should solve that problem.  I'm not sure why anyone would want to use the WAN domain for their internal network anyway..

---

