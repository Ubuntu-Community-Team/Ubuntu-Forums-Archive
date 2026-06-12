---
title: "How to install Automatix in Dapper"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Vega on 2006-05-30
the details for installation were kind of brief (can be found here [http://ubuntuforums.org/showthread.php?t=177650)](http://ubuntuforums.org/showthread.php?t=177650)). Can anyone guide me through this process?

Thank you!

---

### Post by richbarna on 2006-05-30
Hi Vega,
First, on that guide you have to download the [http://www.beerorkid.com/arnieboy/automatix_6.0-5rc4_i386.deb]("http://www.beerorkid.com/arnieboy/automatix_6.0-5rc4_i386.deb") file (either to your home folder directly, or download to your desktop and then put it in your home folder).
If you haven't already done it install build-essential like this :-
Open your terminal/console and type :-
> sudo apt-get install build-essential
and let it download and install.
Now in your terminal/ console type :-
> cd /home/vega (or what ever your user name is) 
you should be at :-
> vega@ubuntu:~$
Now type :-
> sudo dpkg-i automatix_6.0-5rc4_i386.deb
This will install automatix :)

---

### Post by Vega on 2006-05-30
> Setting up build-essential (11.1) ...
redsteel@redsteel-d5150:~$ cd /home/redsteel
redsteel@redsteel-d5150:~$ sudo dpkg-i automatix_6.0-5rc4_i386.deb
sudo: dpkg-i: command not found


so close. something must be wrong.

---

### Post by Jagot on 2006-05-30
needs to be a space between the 'dpkg' and the '-i'

```
sudo dpkg -i automatix_6.0-5rc4_i386.deb
```

---

### Post by Vega on 2006-05-30
[QUOTE=Jagot]needs to be a space between the 'dpkg' and the '-i'

```
sudo dpkg -i automatix_6.0-5rc4_i386.deb
```[/QUOTE]
alright it looked liked it worked

> redsteel@redsteel-d5150:~$ sudo dpkg -i automatix_6.0-5rc4_i386.deb
(Reading database ... 75413 files and directories currently installed.)
Preparing to replace automatix 5.8.4 (using automatix_6.0-5rc4_i386.deb) ...
Unpacking replacement automatix ...
Setting up automatix (6.0-5rc4) ...
redsteel@redsteel-d5150:~$


---

### Post by richbarna on 2006-05-31
Damn !! sorry vega (typo) :)
It was late and I was typing as fast as I could, I should of checked the post.

---

