---
title: "folder sharing with XP box on home network"
date: 2005-05-14
forum: Absolute Beginner Talk
---

### Post by soonindallas on 2005-05-14
hi.  I just installed ubuntu on my new laptop -- without a hitch :-) and I'm looking for pointers on how to share folders with my XP box on this same home network...

they both can ping each other, they each see the internet through the gateway/cable modem, but ubuntu system->administration->shared folders tells me I need to install samba, and to the  best of my knowledge, it is installed.

thanks for your help.

Peter

---

### Post by jrobcet on 2005-05-14
Samba server is not present in a standard installation of Ubuntu. You'll need to install it yourself:```
sudo apt-get install samba
``` You also might interested in this thread:
[http://www.ubuntuforums.org/showthread.php?t=26438](http://www.ubuntuforums.org/showthread.php?t=26438)

---

### Post by poofyhairguy on 2005-05-14
Did you look for help here:

[http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver)

---

### Post by soonindallas on 2005-05-14
well, i gotta say i am no further advanced.

got samba installed and running, thanks.  now my XP box sees this one and recognises me as being in the workgroup... BUT I have yet to log into this Ibuntu box.  man!

tried looking into my XP box from here, can't see a thing.

what's the reason I can see my XP box in "places -> network" but I can't see inside ?
how do I set this box up so my XP box can see a folder I have declared as "shared" ?

---

### Post by soonindallas on 2005-05-15
ok.  it is working now !! turns out I had omitted to add myself as a user with sambapwd or similar...  thx

lesson learned: follow all the darn steps! all of them!

---

### Post by noname123 on 2008-02-13
In the samba how to [http://ubuntuforums.org/showthread.php?t=26438]("http://ubuntuforums.org/showthread.php?t=26438")  I did the "sudo gedit /etc/samba/smb.conf" and got this 


[global]
workgroup = workgroup
netbios name = me_smb_server
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = yes
security = me

I did not have the [home] part of the tutorial can yall help?

---

### Post by noname123 on 2008-02-13
never mind found gssambad fixed it thanks

---

