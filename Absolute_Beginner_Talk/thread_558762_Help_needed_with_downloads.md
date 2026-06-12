---
title: "Help needed with downloads"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by FOBBEDOFFWITHCRAP on 2007-09-24
HELLO PEOPLE
Why is it that linux makes it so difficult for noobs like me to get onthe linux ladder.
No sooner have you downloaded the program you have to set up this file that folder , commands for various programs that you haven't a clue how to do.
Its like sending a learer driver on a trip down the motorway , they haven't a clue what to do.
Ever time it try to install a program on my linux pc like avg anti virus for example , i downloaded the deb file in firefox it loaded up all ok and i try to do an update for it and all i get is that i don't have permissions , sorry but i am the only user on the pc am i missing something here.
The same with firestarter i downloaded it through snypix or whatever it is called and it download ok spent nearly all of last night to try and work out how to get the thing to load on boot up with piles of different answers but no success.
I have to say i like the whole ubuntu os apart from the permissions / files folders / sudo kawasaki cobblers.
Please help an avid ubuntu noobie
Cheers Dave

---

### Post by por100pre1 on 2007-09-24
First, AVG current version is buggy and needs superuser to work, use avast instead.

Second, you don't need to setup Firestarter to run at startup, the firewall is actually iptables and it runs at startup.

Ubuntu is not Windows, you are already secure! ;)

---

### Post by master_kernel on 2007-09-24
Yup. It's almost pointless to have antivirus in Ubuntu, but I think there is an open source one out there, but I can't recall it's name.

---

### Post by FOBBEDOFFWITHCRAP on 2007-09-24
hello
thank you for your answers / i feel a bit better now

---

### Post by sailor2001 on 2007-09-24
clam or klam . learn to search in synaptics. it's loaded with apps

---

### Post by FOBBEDOFFWITHCRAP on 2007-09-24
just seems alien to not have any protection thats all
Currently i download my programs through firefox which downloads them to the desktop.
Do i need to make a folder for my downloaded files and if so how do i do this.
Many Thanks Dave

---

### Post by FOBBEDOFFWITHCRAP on 2007-09-24
hello again
I tryed to download a program through  wsynaptic and nearly on completion it said failed inerror code 1 whatever that means

---

### Post by por100pre1 on 2007-09-24
The permissions system is in fact a security measure. It makes difficult to a malicious script to take control of your system.

---

### Post by FOBBEDOFFWITHCRAP on 2007-09-24
so even if it is a trusted program it seems like the os give you a hard time installing any program even if it is from synaptic

---

### Post by por100pre1 on 2007-09-24
> **FOBBEDOFFWITHCRAP said:**
> hello again
I tryed to download a program through  wsynaptic and nearly on completion it said failed inerror code 1 whatever that meansClose everything and try this (in terminal):


```
sudo apt-get update && sudo apt-get upgrade
```

and then try again.

EDIT:Only one package manager can be running at the same time... :-k

---

### Post by FOBBEDOFFWITHCRAP on 2007-09-24
hello
i have done that but it has an error which is as follows
errors were encounted as follows
clamav-base
clamav-freshclam
clamav
E: Sub-process /user/bin/dkpg returned an error code (1)

---

### Post by Rahmat on 2007-09-24
Hi

Those previous responses are quite alrite! Make sure you visit the synaptic i.e the magic orange icon at the panel on the same line with the Applications.

You can also visit this link when you download some other packages and you want to install anything on Ubuntu. [http://monkeyblog.org/ubuntu/installing/#package_manager](http://monkeyblog.org/ubuntu/installing/#package_manager) It has been working for me and i think it should work for you.

Besides, make sure you are connected to the internet 24/7 to get softwares update.

This link might be useful in order to get softwares from most angles [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Hope that helps!!!

---

### Post by por100pre1 on 2007-09-24
Try this:

```
sudo aptitude remove clamav
```

---

