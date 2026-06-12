---
title: "[Easy script] Installing Java JRE1.5 Without Efforts !!"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-05-14
Hi, 

I made a easy installation script to install JAVA JRE 1.5
on Linux machine with adding a plugin for mozilla-firefox.
I hope it will be without any efforts !! :-)
  
To install Java Jre 1.5:
```
sudo bash
cd /root
wget http://patrick295767.sitesled.com/miniram/easypatrick295767install_sunjava2re1.5.sh
chmod +x easypatrick295767install_sunjava2re1.5.sh
sh easypatrick295767install_sunjava2re1.5.sh
```
  
and reply two questions, and that should be quickly installed !
 
Greetings !!
 
Patrick

========
REFERENCES:
[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java)
    
======
Other scripts without efforts: 
multimedia.sh : (signature)
e17 enlightenment : post ##  (somewhere)
engage bar : post ## (somewhere)
my fvwm desktop : [http://patrick295767.sitesled.com/fvwm/howtoinstallfvwm.htm](http://patrick295767.sitesled.com/fvwm/howtoinstallfvwm.htm)

---

### Post by Sef on 2006-05-14
i m sure you'll make a lot of beginners happy with that script.

---

### Post by bman on 2006-05-14
Yea, I'll give it a try when I need to install it.

Thanks

---

### Post by jhorner on 2006-05-14
[QUOTE=patrick295767]Hi, 

I made a easy installation script to install JAVA JRE 1.5
on Linux machine with adding a plugin for mozilla-firefox.
I hope it will be without any efforts !! :-)
  
To install Java Jre 1.5:
```
sudo bash
cd /root
wget http://patrick295767.sitesled.com/miniram/easypatrick295767install_sunjava2re1.5.sh
chmod +x easypatrick295767install_sunjava2re1.5.sh
sh easypatrick295767install_sunjava2re1.5.sh
```
  
and reply two questions, and that should be quickly installed !
 
Greetings !!
 
Patrick

[/url][/QUOTE]

Thank you for sharing.  I am still receiving errors when I try to run a Java app from the desktop or firefox.  It just says Open with firefox.  I tried adding a selection manually, like finding the java program, but to no avail.  Does anyone know what the java "program" is called and where its located?

Edit : Found it.  If anyone else is curious it is jre1.5.0_06/bin/javaws.

---

### Post by DSn0wMan on 2006-05-14
[QUOTE=patrick295767]Hi, 

I made a easy installation script to install JAVA JRE 1.5
on Linux machine with adding a plugin for mozilla-firefox.
I hope it will be without any efforts !! :-)
  
[QUOTE]

Thats verry cool! I don't know if it's appropriate at this point, but if it works for many useres, it would be helpfull to add it to the wikki.

Thanks patrick

---

### Post by patrick295767 on 2006-05-14
> 

Thats verry cool! I don't know if it's appropriate at this point, but if it works for many useres, it would be helpfull to add it to the wikki.

Thanks patrick
  
I hope it can be made effortless for most users !!
***Let's work together  :-)  to improve it !*** ;) 
==>
  If you installed it via Method 3, would a :
>  
ln -s /opt/jre1.5.0_06/bin/javaws /usr/bin/javaws
or sthg like this for /opt/jre1.5.0_06/bin/javaws  
(I dont have any linux machine here)

be helful ??
  
*(I am using fvwm, and then didnt need of desktop java link)*

---

### Post by DSn0wMan on 2006-05-14
I'll look into it, when I get home. I have a michine with a fresh ubuntu install in need of jre1.5.0_06.

If I remember correctly, the only thing I had to do was some sort of apt-get command to change the default version of java that was in use. Then everything worked great. That is of course after I did the install

I know thats pretty veague, but I am at work right now, and we only have Unix or windows.

---

### Post by mlind on 2006-05-14
I dunno, but your script could violate Sun's license. Package needs to downloaded
from Sun's mirrors, but they're about to change that license

Great contribution nevertheless!

---

### Post by DSn0wMan on 2006-05-14
[QUOTE=mlind]I dunno, but your script could violate Sun's license. Package needs to downloaded
from Sun's mirrors, but they're about to change that license

Great contribution nevertheless![/QUOTE]

Thats true, because if you go to Sun for the download you must click a button to agree to the license before you get redirected to the appropriate download.

---

### Post by patrick295767 on 2006-05-14
[QUOTE=DSn0wMan]Thats true, because if you go to Sun for the download you must click a button to agree to the license before you get redirected to the appropriate download.[/QUOTE]
   hmmm,   Indeed...
For the method 03 of the installation, you have to say YES, then it's getting installed. 
 
But for the fake root method of installation.. not... 
So, for this method,  I should mention to download it from the official website. 
  
Or in the menu, at the beginning of the script, I can recommand the SUN official website, then, give also the possibility of retrieving the .Bin file with mentioning that's a Mirror ... 
 
I can possibly also add the same stuffs from sun at the beginning, and giving choice to say Yes or No (=no install)... 
  
:-k :-k :-k
  How to make life easier to new linux users ... :-k

---

### Post by mlind on 2006-05-14
Good news I guess, Sun has opened up their licence
[http://www.ubuntuforums.org/showthread.php?p=1017009](http://www.ubuntuforums.org/showthread.php?p=1017009)

---

### Post by DSn0wMan on 2006-05-14
Does this mean that we will be able to do something like this?
```
sudo apt-get install jre1.5.0_06
```

---

### Post by mlind on 2006-05-14
[QUOTE=DSn0wMan]Does this mean that we will be able to do something like this?
```
sudo apt-get install jre1.5.0_06
```[/QUOTE]

Once it's uploaded upsteam then Yes! :mrgreen: 

packages are
```

sun-java5-demo 
sun-java5-fonts 
sun-java5-bin 
sun-java5-source 
sun-java5-jdk 
sun-java5-doc 
sun-java5-jre 
ia32-sun-java5-plugin 
ia32-sun-java5-bin 
sun-java5-plugin

```

This could only be for Dapper, atleast for now.

---

### Post by DSn0wMan on 2006-05-14
What is it that those gamer guys say.....

Woot Woot!

---

### Post by DSn0wMan on 2006-05-14
Patrick,

As I promised earlier I tried your script on a machine with a fresh ubuntu breezy install.

Method 3 worked very well. I also passed your english test perfect score. 

The only hangup, is that for jre1.5.0_06 it is installing the 586 version, instead of the 386 version. So I can see that it might be good to have a choice, as not all of us have 586 machines.

It's probably a moot point with the news of sun opening it's license.

Good job on the script!

---

### Post by Audiophiliac on 2006-05-14
Script ran normally. However Java didnt work on Firefox under Xubuntu 6.06 Dapper Beta 2. How do I go about this?

---

### Post by patrick295767 on 2006-05-15
[QUOTE=DSn0wMan]Patrick,

As I promised earlier I tried your script on a machine with a fresh ubuntu breezy install.

Method 3 worked very well. I also passed your english test perfect score. 

The only hangup, is that for jre1.5.0_06 it is installing the 586 version, instead of the 386 version. So I can see that it might be good to have a choice, as not all of us have 586 machines.

It's probably a moot point with the news of sun opening it's license.

Good job on the script![/QUOTE]
  
Good News !! :-) :KS 
  Concerning the 586 version, if you have any packages that you would like me to had to the script. (since I am rather busy these coming weeks). Do not hesitate to send it into my mail box (gmail account).
  
Concerning the Dapper, I still didn't try on this distro. I have to finish installing Dapper on a prehistoric PC (64MB), I am damn making use of compiling ... Soo prehistoric, that I am thinking to make it possible to install Netscape ;) instead of opera or mozilla. I cant promise yet when done. 
On the other hand, you can post your error msg if there was (copy paste from konsole) (?). 
  
For the English test, :) , How much you got ? If you have other tests, send the address link, why not ! :D Can be funny !
  
Greetings, 
 
Patrick

---

