---
title: "Newbie Firefox Prob"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by DRHamp on 2007-01-05
Ok, last week I completed my first Linux install -- a dual-boot with XP on a HP Laptop.  After several mistries, I finally got wireless working and all was well ... until

Im using the packaged Firefox browser and upgraded it to the latest version -- not sure were I got the instructions to do that, but it seemed to work fine.

Today, at a frequently visited website - I got the message that I need Flash plugin installed and again after several mistries I got it installed -- or so I thought.

I have that site set up in one of my browser tabs and now when it acccesses that tab the browser immediately shuts down.

Being a real newb here -- i'm not even sure how to unstall and reinstall firefox  -  I assume that's where I need to go.

Any guidance is appreciated:confused:

---

### Post by taurus on 2007-01-05
You probably installed flash 7 and that site is using flash 8!  However, you can install flash 9 for Ubuntu if you wish.  Go to this site and install automatix2.  Then use automatix to install the latest version of flash for your browser...

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by energiya on 2007-01-05
For firefox crashing visit this [link]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox").

---

### Post by DRHamp on 2007-01-05
> **taurus said:**
> You probably installed flash 7 and that site is using flash 8!  However, you can install flash 9 for Ubuntu if you wish.  Go to this site and install automatix2.  Then use automatix to install the latest version of flash for your browser...

[http://www.getautomatix.com](http://www.getautomatix.com)
Thanks Taurus.  The problem with that is -- I can't keep the brower up -- it shuts down immediately, so I cant' go to another site.

---

### Post by quasismart on 2007-01-05
I am not able to help you with your current problem. However, I was hoping you could help me with mine: wireless. I have been trying to get this working for months now and I am about to pull my hair out and well never mind that. Any help or advice would be great.

---

### Post by MkfIbK7a on 2007-01-05
you could try to do 
sudo apt-get install opera
then go to that website from opera

---

### Post by DRHamp on 2007-01-05
> **quasismart said:**
> I am not able to help you with your current problem. However, I was hoping you could help me with mine: wireless. I have been trying to get this working for months now and I am about to pull my hair out and well never mind that. Any help or advice would be great.

I followed this link:  [http://www.ubuntuforums.org/showthread.php?t=185174&highlight=Broadcom+Wireless+Cards+without+Ndiswrapper]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=Broadcom+Wireless+Cards+without+Ndiswrapper")

I had several mis-tries, but it eventually worked.  If you don't use  Broadcom wireless card it may be of no use to you -- good luck.  Check out all the links for your config or similar in the "Faqs, Howto, Tips & Tricks" under other support.  I've found it very usefull

---

### Post by DRHamp on 2007-01-05
> **wert613 said:**
> you could try to do 
sudo apt-get install opera
then go to that website from opera

Thanks wert613 -- I'll try that

---

### Post by DRHamp on 2007-01-05
> **wert613 said:**
> you could try to do 
sudo apt-get install opera
then go to that website from opera

I'm sure this will really show what a newbie I am -- when I run sudo apt-get install opera

I get the message package opera is not available .....

So, where would I get it and how to install it.

---

### Post by taurus on 2007-01-05
You probably need to enable both universe and multiverse by removing the # in front of all the lines with those two words at the end or near the end (with deb at the beginning)...

```
gksudo gedit /etc/apt/sources.list
sudo apt-get update
sudo apt-get install opera
```

---

### Post by compwiz18 on 2007-01-05
You could install internet explorer: however, this is probably a bad idea ;) : [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

so then I would probably suggest Epiphany: **sudo apt-get install epiphany-browser**

also, there is dillo (wouldn't recommend, no JavaScript support): **sudo apt-get install dillo**

if you're feeling brave, you could use a terminal based browser, **sudo apt-get install links**

hope one of those will work for you :D

---

### Post by DRHamp on 2007-01-05
> **energiya said:**
> For firefox crashing visit this [link]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox").

Thanks energiya -- that fixed firefox so that I can at least get it up without crashing.

---

### Post by DRHamp on 2007-01-05
> **taurus said:**
> You probably need to enable both universe and multiverse by removing the # in front of all the lines with those two words at the end or near the end (with deb at the beginning)...

```
gksudo gedit /etc/apt/sources.list
sudo apt-get update
sudo apt-get install opera
```

Thanks taurus -- I did the above and got a lot of updates, but still no Opera.

I think I'm rambling this thread all over the place and aplolgize for that.  I did get firefox where it would stay up by following energys suggestion.

So, then I downloaded the Opera install from Opera for Ubuntu 6.1 and executed it.
It fails with the following error message:
Error: Dependency is not satisfiable: libqt3-mt

Any ideas -- and I promise not to extend this thread any further.

---

### Post by energiya on 2007-01-05
> **DRHamp said:**
> Thanks taurus -- I did the above and got a lot of updates, but still no Opera.

I think I'm rambling this thread all over the place and aplolgize for that.  I did get firefox where it would stay up by following energys suggestion.

So, then I downloaded the Opera install from Opera for Ubuntu 6.1 and executed it.
It fails with the following error message:
Error: Dependency is not satisfiable: libqt3-mt

Any ideas -- and I promise not to extend this thread any further.

just write in the terminal
```

sudo apt-get install libqt3-mt

```
and try again installing the .deb file

Cheers

---

### Post by DRHamp on 2007-01-05
> **taurus said:**
> You probably installed flash 7 and that site is using flash 8!  However, you can install flash 9 for Ubuntu if you wish.  Go to this site and install automatix2.  Then use automatix to install the latest version of flash for your browser...

[http://www.getautomatix.com](http://www.getautomatix.com)

That did it -- thanks taurus.  Once I got firefox back, I downloaded Automatix2 -- really cool app -- it installed Opera -- even took care of the last prob I mentioned.

Very cool -- thanks again --- as promised, I won't extend this thread further

---

