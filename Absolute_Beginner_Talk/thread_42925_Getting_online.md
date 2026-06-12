---
title: "Getting online"
date: 2005-06-19
forum: Absolute Beginner Talk
---

### Post by TheAnonymousx on 2005-06-19
So I abandoned the wireless USB adapter and have wired myself in to the router in the main room with a long freakin' cable. I have a new problem though, the Linux box is an old Duron with everything onboard. The motherboard is an old Amptron that I put in the equally old case a few years ago when I was in need of a PC.

My question is this, what's the best way to identify the NIC in the system and install drivers for it.

---

### Post by ltmon on 2005-06-20
Hopefully calling the command line program "lspci" will print out some useful information.

Try: 

> lspci | grep Ethernet

And see what comes up.

That should give some hints about which module needs to be loaded to access the device.

L.

---

### Post by TheAnonymousx on 2005-06-20
sis 9000 fast ethernet (rev 82) 

Okay, so that's the on-board card that exists in my linux box. I'm currently hunting down drivers for it. But before I even get that far, I should ask whether or not I'll have to set up anything or if it should pretty much work after loading approprirate drivers.

**edit**

Okay so I found the driver (conveniently on SIS' homepage under the driver link marked "linux") and it's in a tar file all nice and compressed with a couple of other files.
I will delve more into this tomorrow, but for now, can someone give me an idea of how to  extract and install the drivers from this file (via the CLI)?
thankx

---

### Post by wvslkr on 2005-06-20
That driver should be already available."sudo modprobe sis900" to bring it up.  Ifconfig will show if it is working.  Look in the guide to finish and make permanent. Or post back if 
you need more help.  GL. :)

---

### Post by TheAnonymousx on 2005-06-21
Okay, pardon me for sounding just plain stupid here, but I am not sure of which guide you're referrring to. I'm gonna search the ubuntu web in a bit as well as the forums.

Also, is there some place that has this kinda information so I don't have to keep bugging you guys...heh I feel so needy. Currently I'm using the unofficial ubuntu 5.04 Starter Guide, but it doesn't help in this area.

---

### Post by wvslkr on 2005-06-21
That is the guide I meant.  To start your card open a terminal and type
 [sudo modprobe sis900]no brackets.  If no errors are generated, type 
[ifconfig] if your card is working, you will have two entries.  One for the local loopback interface and one for the nic. If the card is there then do this:from the menu.

System -> Administration -> Networking 

Connections Tab -> Select "Ethernet connection" -> Activate/Deactivate

Connections Tab -> Select "Ethernet connection" -> Properties

Connection -> This device is configured (Checked)
Connection Settings -> Configuration: Select "DHCP/Static IP address"

DNS Tab -> DNS Servers -> Add/Delete

To make permanent you will have to add sis900 to /etc/modules conf. in the text editor of your choice.

Hope that helps a bit more. :)

---

