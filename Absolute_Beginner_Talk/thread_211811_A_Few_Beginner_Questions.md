---
title: "A Few Beginner Questions"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2006-07-08
I have a few just general questions which someone with just a bit more knowledge than me should be able to answer, so I am putting them all in here.  I hope that is ok.

1) The max screen res I can get with Ubuntu is 1024x768 but I have a 21" monitor and with the KVM switch on this same monitor, my XP box goes to at least 1200x1024.  How do I change this resolution?

2) How do I set a root password?  I never saw an option for it on install.  And when I use the Konsole and type "su" I don't know what password it wants.  I think that this is the same thing as the root password, but I have never set one and don't know where to do it.

3) I have Samba installed and I can access all my windows boxes fine from Ubuntu.  From my windows boxes, I can see the Ubuntu box, but when I try and open the folder, it denies me access.  I have set the permissions to what I think is right and created the user that I use to login to the Ubuntu box.  But I am not doing something right.

4) What is the best wirless card that I can use?  I have tried two of them and can't get either to work.  They are:

Netgear WG311 v2 PCI card
0000:00:03.0 0200: 1039:0900 (rev 90)

Airlink 101 USB
Bus 002 Device 002: ID 0ace:1215 ZyDAS

---

### Post by KrisDwyer on 2006-07-08
> **kc5hwb said:**
> I have a few just general questions which someone with just a bit more knowledge than me should be able to answer, so I am putting them all in here.  I hope that is ok.

1) The max screen res I can get with Ubuntu is 1024x768 but I have a 21" monitor and with the KVM switch on this same monitor, my XP box goes to at least 1200x1024.  How do I change this resolution?

2) How do I set a root password?  I never saw an option for it on install.  And when I use the Konsole and type "su" I don't know what password it wants.  I think that this is the same thing as the root password, but I have never set one and don't know where to do it.

3) I have Samba installed and I can access all my windows boxes fine from Ubuntu.  From my windows boxes, I can see the Ubuntu box, but when I try and open the folder, it denies me access.  I have set the permissions to what I think is right and created the user that I use to login to the Ubuntu box.  But I am not doing something right.

4) What is the best wirless card that I can use?  I have tried two of them and can't get either to work.  They are:

Netgear WG311 v2 PCI card
0000:00:03.0 0200: 1039:0900 (rev 90)

Airlink 101 USB
Bus 002 Device 002: ID 0ace:1215 ZyDAS

2) By default, i believe it will be the password u set up for ur own account when you installed. to change this, go to a normal terminal and type the following.

> sudo passwd root

Type your password when asked to access the superuser priveliges then it will ask you for ur current password. Once thats done, just follow the prompts.

Hope it Helps,
Kris

---

### Post by woedend on 2006-07-08
By default its set to use a random password that you will ever know.  (k)ubuntu uses sudo/gksudo for gnome and kdesu for kde.  the su command won't work until you set a root password.  I would recommend to just use the command sudo su  instead to put you where you want to be.  It will take your user password, not a root password.  But to set root password just issue command
sudo passwd


as far as samba goes, i made another ubuntu account for a user (i named him sambaman), then used samba to add the account also.
is it at least asking you for username and password when you try to access it?

---

### Post by John.Michael.Kane on 2006-07-08
> **kc5hwb said:**
> I have a few just general questions which someone with just a bit more knowledge than me should be able to answer, so I am putting them all in here.  I hope that is ok.

1) The max screen res I can get with Ubuntu is 1024x768 but I have a 21" monitor and with the KVM switch on this same monitor, my XP box goes to at least 1200x1024.  How do I change this resolution? [B]Editing your xorg should fix it 

[B]This makes a backup of the file you're about to change.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` 
This will stop GDM
```
sudo /etc/init.d/gdm stop
``` 
This will auto detect everything and you will be able to select the resolutions you wish to use.
```
sudo dpkg-reconfigure xserver-xorg
```. 
Will restart your GDM
```
sudo /etc/init.d/gdm start
``` [/B]

2) How do I set a root password?  I never saw an option for it on install.  And when I use the Konsole and type "su" I don't know what password it wants.  I think that this is the same thing as the root password, but I have never set one and don't know where to do it. **This should have been set durring the install. sudo is the pass phrase you choose durring the install.**

3) I have Samba installed and I can access all my windows boxes fine from Ubuntu.  From my windows boxes, I can see the Ubuntu box, but when I try and open the folder, it denies me access.  I have set the permissions to what I think is right and created the user that I use to login to the Ubuntu box.  But I am not doing something right. **Here are some howto's for [Samba-HOWTO-Collection]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/")**

4) What is the best wirless card that I can use?  I have tried two of them and can't get either to work.  They are:

Netgear WG311 v2 PCI card
0000:00:03.0 0200: 1039:0900 (rev 90)

Airlink 101 USB
Bus 002 Device 002: ID 0ace:1215 ZyDAS
Heres some Wifi info [**WiFiHowTo**]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

Hope this is of some help

---

### Post by IrishGangsta on 2006-07-08
for root password i was taught to just type   sudo -i
and put ur current password 
That also gets you onto root user in terminal

---

### Post by kc5hwb on 2006-07-09
Thanks for the replies....

> 2) How do I set a root password? I never saw an option for it on install. And when I use the Konsole and type "su" I don't know what password it wants. I think that this is the same thing as the root password, but I have never set one and don't know where to do it. **This should have been set durring the install. sudo is the pass phrase you choose durring the install.**

It wasn't.  I did set my user during the install, but not the root user.

> 2) By default, i believe it will be the password u set up for ur own account when you installed. to change this, go to a normal terminal and type the followin

The user password does not work.  I tried that originally when typing "su" in the Konsole.  I also tried it upon the initial login screen after booting, and entering "root" for the username.  It won't take my user password for the su or root account.

> sudo passwd root

This worked.  Thanks!

---

### Post by kc5hwb on 2006-07-09
> **woedend said:**
> 
as far as samba goes, i made another ubuntu account for a user (i named him sambaman), then used samba to add the account also.
is it at least asking you for username and password when you try to access it?

Yes, it is asking me for a username and password, and when I type my only user in, it populates the machine name in front of my username, but doesn't accept my login.

So you are saying to create a new user on the linux box, and then also where?

---

### Post by woedend on 2006-07-09
just issuing the command
sudo smbpasswd -a sambaman(or whatever username)

---

### Post by kc5hwb on 2006-07-09
Thanks, that worked great.

---

