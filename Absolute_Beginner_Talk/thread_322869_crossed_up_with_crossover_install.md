---
title: "crossed up with crossover install"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by electrodad on 2006-12-21
Hi,
    I have attempted to install the beta version of crossover office through terminal window, but without success. i have searched for info on this matter in the newbie section and did try what others had done, but still no go. I would like to run MS office for the info path invoices I have up as well as a few other things. I also wish to play the wma/wmv files the windows people email me. Eventually I want to leave Windows behind and go totally Linux. Any help would be appreciated.:confused:

---

### Post by hyper_ch on 2006-12-21
For the wma files please see here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by NewbieLearnLinux on 2006-12-21
In short, some media format is restricted by law so their codecs is not supplied offically in the CD. 

You may download those codecs in various sites, but you use them at your own risk. Automatix (or EasyUbuntu) is a great tool for download and installing such things.

hope this helps,

---

### Post by Jussi01 on 2006-12-21
> **electrodad said:**
> Hi,
    I have attempted to install the beta version of crossover office through terminal window, but without success. i have searched for info on this matter in the newbie section and did try what others had done, but still no go. I would like to run MS office for the info path invoices I have up as well as a few other things. I also wish to play the wma/wmv files the windows people email me. Eventually I want to leave Windows behind and go totally Linux. Any help would be appreciated.:confused:

What your problem is it giving you that you dont have permission or something? try running 

```
sudo (insert sh command given on crossover website here)
```

Failing that ( which mine did), being very careful when you do this, try:

```
sudo su root
```

then enter your password to continue.

then try and enter the sh script command given on the crossover website - make sure the crossover file is in your "home" directory

Hope this helps

---

### Post by electrodad on 2006-12-21
> **Jussi01 said:**
> What your problem is it giving you that you dont have permission or something? try running 

```
sudo (insert sh command given on crossover website here)
```

Failing that ( which mine did), being very careful when you do this, try:

```
sudo su root
```

then enter your password to continue.

then try and enter the sh script command given on the crossover website - make sure the crossover file is in your "home" directory

Hope this helps

I ran the sudo us root and it did not ask for a password. Then I pasted the script from the web this is what I got....


Verifying archive integrity...OK
Uncompressing CrossOver Linux
........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


Setup requires an X display to run.  There is a display variable set, however
you have no permissions to access the X server (:0.0) it points to.
Try running xhost +localhost before su'ing to root.

The setup program seems to have failed on x86/glibc-2.4
Check the system requirements at:
[http://www.codeweavers.com/products/cxoffice/requirements/](http://www.codeweavers.com/products/cxoffice/requirements/)

 @ this point I don't understand what it is asking. my system is as follows a Dell XPS m140 , 1,67 Centrino Processor, 1.5 gig RAM, 60 Gig HD (7200), etc.... it should be enough to run just about anything.
Any advice?

---

### Post by Jussi01 on 2006-12-21
It looks like your missing "Glibc 2.3.x or greater" try searching for that in synaptic and then installing it again...

---

### Post by electrodad on 2006-12-21
Well, I have good news,no..... i did not save a ton of money by switching to the Lizard insurance company, but I did get Crossover office installed on my system. I have installed office and it's running fine except Outlook.:D  I explored the user properties and assigned my user to the root group and found my root profile was not enabled as administer etc.... Anyway thank you very much for your help. I have performed numerous desktop support for end users. When I use linux I feel computer illiterate.

---

