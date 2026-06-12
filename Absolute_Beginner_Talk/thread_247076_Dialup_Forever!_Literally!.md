---
title: "Dialup Forever! Literally!"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by MaLaKa on 2006-08-30
Well my Ubuntu CDs came today! Was very pleased with this distro! Good work dev team! But I have come across somthing that is driving me insane!

When I go to dialup using Admin Networking (It finds my modem and it dials) It will go through the whole dialing noises and then silence. I have no idea if it is connected, but after about 1min, it will dial again! over and over and over. Even after I disable it in the Admin Networking. The only way to stop it dialing is to restart hahaha. ](*,) Also nothing works internet wise :( I know winmodems are a pain in the arse to setup, but it seems that Ubuntu has support for agere/lucent modems :-k  

Any help on getting it to stay connected?
(keeping in mind I have been using linux for 40mins so far hehe)

Modem: Netcomm InModem IN5699 (PCI, red cb)

---

### Post by Bachstelze on 2006-08-30
Try using wvdial for dialup. Command-line based tool but will never fail on you (at least it never failed on me).

First, run

```
sudo wvdialconf /etc/wvdial.comf
```

to create the wvdial configuration file, then 

```
sudo nano /etc/wvdial.conf
```

to edit it entering your username, password and ISP's phone number, then *sudo wvdial* to dial, voilà :)

---

### Post by editrix on 2006-08-30
It's probably the "authentication" problem. In /etc/ppp/options comment out the line 

auth

Assuming you can stay online after that, you may want to install Gnomeppp (not sure of the name, I use KDE) or Kppp, both of which will give you some feedback on your connection.

---

### Post by MaLaKa on 2006-08-30
Thanks people! I will try it and get back to ya to see if it works :D

---

### Post by MaLaKa on 2006-08-31
Okay I used the terminal and did the following ~

sudo wvdialconf /etc/wvdial.comf
sudo nano /etc/wvdial.conf (added all the details then saved)
sudo wvdial

It dials, does what Admin Network does. Then it says somthing about "not knowing what to do" then using DPPP daemon then it failing then reconnecting.
So I set DPPP= no in wvdial.conf and this time it says DPPP Daemon fails, kinda guess its becuase ive stopped it haha. So Its set to how it was originally. 

I would of saved the complete log onto my windows drive, but it said I wasnt the owner and didnt have permission (couldnt save it, but that is another issue:rolleyes:).

Any Ideas?

---

### Post by editrix on 2006-08-31
> **MaLaKa said:**
> It dials, does what Admin Network does. Then it says somthing about "not knowing what to do" then using DPPP daemon then it failing then reconnecting.... Any Ideas?

Well, assuming you told it about your username and password ...

I never used wvdial. Have you tried sudo pon (to connect) and then sudo poff (to disconnect)?

---

### Post by b_martinez on 2006-08-31
QUOTE:
Okay I used the terminal and did the following ~

sudo wvdialconf /etc/wvdial.comf
sudo nano /etc/wvdial.conf (added all the details then saved)
sudo wvdial

:END QUOTE

You may have the wrong command
sudo wvdialconf /etc/wvdial.comf
should be
sudo wvdialconf /etc/wvdial.conf
The top command will tell wvdial to look at /etc/wvdial.comf when it needs to look at wvdial.conf.
Simpl mistake, but iyt may be the difference between success and failure.
Bill

---

