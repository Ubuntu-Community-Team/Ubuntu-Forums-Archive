---
title: "Where is Skype?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2008-02-11
Hi!
I'd like to use Skype, but I can't find it in the Add/remove... Where is it?

---

### Post by PmDematagoda on 2008-02-11
Add the Medibuntu repositories according to this [guide]("https://help.ubuntu.com/community/Medibuntu"). Then install Skype using:-
```
sudo apt-get install skype
```

---

### Post by LowSky on 2008-02-11
go into terminal and copy and paste this

```
sudo apt-get install skype
```

if that doesn't work you might need to copy paste this first the go back and add skype

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

---

### Post by Zdravko on 2008-02-11
> **PmDematagoda said:**
> Add the Medibuntu repositories according to this [guide]("https://help.ubuntu.com/community/Medibuntu"). Then install Skype using:-
```
sudo apt-get install skype
```
This is not working for me. I get:
> 
zdravko@ubuntu:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for zdravko: 
--18:04:34--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:04:35 ERROR 404: Not Found.


---

### Post by PmDematagoda on 2008-02-11
You get that error because a Hardy repository is still not present. Try using the repository for Gutsy, though I cannot be sure of it's reliability and it's risks. Also, you may be better off just downloading the Skype installer for Ubuntu from the Skype website and installing it.

---

### Post by Zdravko on 2008-02-11
It has a deb for Feisty fawn only.
Is there any alternative to Skype that I can use?

---

### Post by PmDematagoda on 2008-02-11
> **Zdravko said:**
> It has a deb for Feisty fawn only.
Yes, but incidentally I am using the Skype version for Feisty on Hardy Heron.

> Is there any alternative to Skype that I can use?
You can try Ekiga Softphone which is included in Hardy, I am not sure about other alternatives.

---

### Post by hyper_ch on 2008-02-11
> **PmDematagoda said:**
> You get that error because a Hardy repository is still not present. Try using the repository for Gutsy, though I cannot be sure of it's reliability and it's risks.
works fine for me...

---

### Post by Zdravko on 2008-02-11
OMG! This is Skype? It looks horrible. The fonts are... The functionality is far below than the Windows version... I am leaving it...

---

### Post by ferdostar on 2008-02-11
> **Zdravko said:**
> OMG! This is Skype? It looks horrible. The fonts are... The functionality is far below than the Windows version... I am leaving it...

You can try the beta version of skype [http://www.skype.com/intl/en/download/skype/linux/beta/](http://www.skype.com/intl/en/download/skype/linux/beta/)
Work fine for me.

---

### Post by LowSky on 2008-02-11
what did you really expect... they built that version like 5 years ago, and never update it, same thing with AOL's AIM... they dont care about linux... so we make our own... ie: Pidgin

---

### Post by HebrewTheHammer on 2008-02-11
So just To clear things up.


Is there no skype via medibuntu for gutsy?

because i dont have it either.  I want it because im going to get it on my PSP i could make free calls to my home(texas) when i leave for work this summer(alaska).

---

### Post by Aurora@FleetBuzz on 2008-02-11
I installed Skype via the Synaptic Package Manager.  Works fine.

---

### Post by Zdravko on 2008-06-27
I will give it a try one more time. Hope that it got better...

---

### Post by Zdravko on 2008-06-27
I downloaded it from the official website and... I see some good progress. It looks slightly better. The options menus are only accessible from the tray, however. I didn't see an option to autostart skype and no remember password feature as in the Windows version. But overall - it is good.

---

