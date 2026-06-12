---
title: "Connect Edgy to a vmserver WinXP with samba"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by eiraku on 2006-11-06
Sorry if this has been asked before, but I'm stuck here trying to connect my Edgy with my vmserver WinXP with samba (which is on the same box)... I've tried various howto's but the main problem here is I don't know how to set up samba to use eth0, which is also used by my PPPOE connection... I've also tried using localhost (which in my mind tells me is futile) to connect...

After endless googling, the HOWTO I tried to follow would be the one here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) ... Not much success there either... I just don't know what IP to tell samba to use (with eth0 busy handling my PPPOE connection)... ](*,) 

Is there any alternative to doing this, or do I have to settle for disconnecting my PPPOE connection and reconfiguring eth0 every time I want to connect my vmserver WinXP with a shared folder on my Edgy box?

Right now I'm stuck doing things the hard way by transferring stuff using a usb drive (Edgy ---> usb drive ---> vmserver WinXP)... Any ideas as of how I can setup samba? Any help would be appreciated... :)

---

### Post by jstueve on 2006-11-06
How is the VM networked? bridged? NAT?

Do you have both SAMBA and WINXP assigned to the same workgroup?

---

### Post by eiraku on 2006-11-06
> **jstueve said:**
> How is the VM networked? bridged? NAT?

Do you have both SAMBA and WINXP assigned to the same workgroup?
I first tried bridged, and then NAT... no avail... On a sidenote, the vmserver WinXP can't seem to connect to the internet using both too...

As to are they assigned to the same workgroup, I tried doing so in smb.conf... 

[global]
    ; General server settings
    netbios name = localhost <--- this is wrong too, I know...
    server string =
   ** workgroup = WORKGROUP**
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

Any ideas? My gut feeling is that I'm doing something terribly wrong here... O_o

---

### Post by jstueve on 2006-11-06
Mine works in bridged mode only, so you first need to get WinXP to get an IP from the bridged connection.

---

### Post by eiraku on 2006-11-06
I'll try to do that... The bridged connection would show up in Windows as the LAN connection right? If I use that IP as the required static IP, samba should work, right?

---

