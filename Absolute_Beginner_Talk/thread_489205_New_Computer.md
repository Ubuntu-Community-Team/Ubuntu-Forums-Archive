---
title: "New Computer"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by thelemech on 2007-07-01
Hello been trying out linux now for 2 weeks plus on a P2 and a P3 and have few problems in fact it works wonderfully on the P3.
My problem is this - my main computer a P4 running Xp Pro SP2 had some major issues and I was almost frustrated into a stroke -so I have taken the plunge- and installed Ubuntu on my main rig;)
- but it will not access the internet without the live cd -what can I do to change this
thank you in advance.

---

### Post by Soarer on 2007-07-01
I think we will need a bit more information to be able to give pointers :)

How is it connected to the Internet? Wired or wireless? If wireless, using what security? If you know, what is the interface card? Does it use a dial-up modem, ADSL modem, router or gateway through another PC?

Are you saying that if you boot of the Live CD it works on the Internet, but not on the installed verion?

If you can provide this information, we may be able to help. Thanks.

---

### Post by expatCM on 2007-07-01
During the install process, were you connected to your Internet service (such as Ethernet cable connected to a router)?  If so, did you see any errors as the install process identified and updated the repositories?

---

### Post by thelemech on 2007-07-01
> **Soarer said:**
> I think we will need a bit more information to be able to give pointers :)

How is it connected to the Internet? Wired or wireless? If wireless, using what security? If you know, what is the interface card? Does it use a dial-up modem, ADSL modem, router or gateway through another PC?

Wired connection -ethernet card is intel Pcl(?)100/1000 connected to a Linsys 5 port hub connected to cable modem

Are you saying that if you boot of the Live CD it works on the Internet, but not on the installed verion?  Yes exactly - it works fine with Live cd but will not work in the installed version.

If you can provide this information, we may be able to help. Thanks.


Was having similar problems with the XP install - tried different ether cards even a USB adapter - but nothing would put that darn machine online - with XP Pro on it. Invested much time and money on software(office2003/Games etc,,, but I literally thought I was going to fly away to loonie land after attempt after attempt. Then  I noticed that the live Ubuntu Cd seemed to have no problem accessing the internet - on the original ether card and the Usb adapter.:(
But after install it would not access internet 
connected to the internet wired via 5 port workgroup hub connected to cable modem

---

### Post by thelemech on 2007-07-01
> **expatCM said:**
> During the install process, were you connected to your Internet service (such as Ethernet cable connected to a router)?  If so, did you see any errors as the install process identified and updated the repositories?
yes I was connected and no errors reported during install.

---

### Post by expatCM on 2007-07-01
Have you checked that the IP address of your Ethernet card is the same as the IP address range of your network?

---

### Post by thelemech on 2007-07-01
> **expatCM said:**
> Have you checked that the IP address of your Ethernet card is the same as the IP address range of your network?
:confused::-\" - how ?

---

### Post by expatCM on 2007-07-01
from the command line try 

ifconfig

your Ethernet card will be probably eth0.  This will show the IP address.

Then see if this is in the same range as the network settings you are connected to ....

---

### Post by Bartender on 2007-07-02
Look into disabling IPV6.

---

