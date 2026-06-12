---
title: "Kubuntu CD as an Ubuntu Repository?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by samare on 2006-08-11
Hi,

I want to install xwindow system on my Ubuntu Server but it doesn't have an Internet connection. But I have a Kubuntu CD with me. So, can I add Kubuntu CD as an Ubuntu Repository to install GUI:?: . How to do that? Please advice.

Thanx

---

### Post by GuitarHero on 2006-08-11
What use is a server without a connection?

---

### Post by Jagot on 2006-08-11
Yep.  Put the CD in the drive, then from Terminal:

```
sudo apt-cdrom add
```

Now update your repositories and install KDE or whatever you want.

---

### Post by samare on 2006-08-11
> **Jagot said:**
> Yep.  Put the CD in the drive, then from Terminal:

```
sudo apt-cdrom add
```

Now update your repositories and install KDE or whatever you want.

Thanks Jogot, I could add the Kubuntu CD in to the repository. Then I tried following commands but none of them worked. Please tell me the correct commands. And it doesn't seem that it's looking for the packages in Kubuntu CD. Still it asks for enter the Ubuntu Server CD. I'm still confuse about Ubuntu package installation procedure.:-( 

sudo apt-get install ubuntu-desktop
sudo aptitude install ubuntu-desktop

sudo apt-get install x-window-system-core
sudo aptitude install x-window-system-core

sudo apt-get install kde
sudo apt-get install kde

---

### Post by samare on 2006-08-11
> **GuitarHero said:**
> What use is a server without a connection?

I'm tring to put up a Ubuntu linux network using two computers at my home and hoping to get some help via this forum. I've got Kubuntu in one PC as client and Ubuntu Server in the other. I would like to install gnone/kde or at lease blackbox/fluxbox in the server. Please help

---

### Post by Jagot on 2006-08-11
Try:

```
sudo aptitude install kubuntu-desktop
```

---

### Post by samare on 2006-08-11
> **Jagot said:**
> Try:

```
sudo aptitude install kubuntu-desktop
```

This is what I get with the above command.
"0 packages upgraded, 624 newly installed, 3 to remove and 1 not upgraded. Need to get 535MB/543MB of archives. After unpacking 1484MB will be used. Do you want to continue?[Y/n/?]"

Then I pressed "y" and then I'm getting the following msg.

"Please insert the disc labeled 'Ubuntu-Sever 6.06 _Dapper Drake_-Release 1383(20060531)' in the drive '/cdrom/' and press enter"

It doesn't look for the Kubuntu CD.

---

### Post by drtvasudevan on 2006-08-11
you must have the kubuntu cd when you execute 

> sudo apt-cdrom add
did you?

---

### Post by samare on 2006-08-11
> **drtvasudevan said:**
> you must have the kubuntu cd when you execute 


did you?

Yes I did. Adding Kubuntu CD in to Ubuntu repository was ok. Now the problem is that the installation programs (apt-get and aptitude)is not picking the Kubuntu CD from the repository. Please help.

I can manualy download packages from another PC. So, please tell me what are the packages do I have to download to install blackbox/fluxbox including dependency. 

:-( 
samare

---

### Post by Jagot on 2006-08-11
From command line:

```
sudo nano /etc/apt/sources.list
```

Now comment out any repositories other than the CD by putting hash before them.  Now try and aptitude install the kubuntu-desktop package.

---

### Post by drtvasudevan on 2006-08-11
it will work **only** if it is an alternative cd
**not **the live plus install cd called desktop cd

---

### Post by samare on 2006-08-15
> **drtvasudevan said:**
> it will work **only** if it is an alternative cd
**not **the live plus install cd called desktop cd

Hi,

You are absolutely right. It worked with alternate CD. Thanks a lot for the support my friend:D 

samare

---

### Post by drtvasudevan on 2006-08-15
> **samare said:**
> Hi,

You are absolutely right. It worked with alternate CD. Thanks a lot for the support my friend:D 

samare
welcome!
=D>

---

