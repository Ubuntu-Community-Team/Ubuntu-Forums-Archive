---
title: "Trying to get my wifi working......"
date: 2014-03-28
forum: Apple Hardware Users
---

### Post by Ryan_J_Kingkade on 2014-03-28
So I have 13.10 installed on a partition of my iMac.  The wifi isn't working.  While troubleshooting I keep getting this message:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Anyone have any idea why this is happening?  

I am very new to Linux and Ubuntu.

Any help would be amazing!

Thank you!:KS

---

### Post by silex89 on 2014-03-28
Hi there and welcome to Ubuntu and Linux! :)

I'm not an expert when it comes to Apple hardware, but I think your iMac will likely be using a Broadcom wireless chip. In that case, you can go to the utility Ubuntu has to install that driver from internet by going to Software Sources > Additional Drivers tab. You need internet connection to do this. If the driver is in the repositories, it will show it to you and you can select it to fetch and install automatically.

Best of Luck! :D

EDIT: What were you doing when you got the output you showed to us?

---

### Post by pqwoerituytrueiwoq on 2014-03-28
if you are installing updates or applications wait for it to finsh
if you are not installing updates/apps run this:
```
sudo rm /var/lib/dpkg/lock
```
then continue doing what you were doing

---

### Post by Ryan_J_Kingkade on 2014-03-29
> **silex89 said:**
> Hi there and welcome to Ubuntu and Linux! :)

I'm not an expert when it comes to Apple hardware, but I think your iMac will likely be using a Broadcom wireless chip. In that case, you can go to the utility Ubuntu has to install that driver from internet by going to Software Sources > Additional Drivers tab. You need internet connection to do this. If the driver is in the repositories, it will show it to you and you can select it to fetch and install automatically.

Best of Luck! :D

EDIT: What were you doing when you got the output you showed to us?

Almost anything I would input came up with that output.  I have Googled it and it seems as though I need to alter parameters of some kind?  Again, I almost have no idea what I am doing, but I want to learn.

Thank you for you help regardless!  When I try to install the driver from Software Sources>Additional Drivers tab, it freezes up.

I believe there is a solution to this, I just need to find it!

:p

Ryan

---

### Post by mörgæs on 2014-03-29
It sounds like a minor annoyance. Have you tried a reboot? 

After that 
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by chili555 on 2014-03-30
Please find out what kind of wireless device you have from the terminal:```
lspci -nn | grep 0280
```If it is a Broadcom, check the sticky here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by PartisanEntity on 2014-03-31
*Thread moves to Apple Users.*

---

