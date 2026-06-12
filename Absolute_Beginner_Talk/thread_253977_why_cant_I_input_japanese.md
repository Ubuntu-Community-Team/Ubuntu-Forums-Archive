---
title: "why cant I input japanese?"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by kansaibear on 2006-09-09
Hello, I'm a noobie that managed to install ubuntu 5.10 install on a old world mac (wallstreet 233 with sonnet 500 G3 card) cause OSX is just too much for the old girl...

downloaded the japanese language kid and works fine except... NO INPUT!

read the forums and got:
[https://help.ubuntu.com/community/Ja...tHowToInBreezy](https://help.ubuntu.com/community/Ja...tHowToInBreezy)

tried to download as written from the terminal and, the following is what I got.

root@ubuntu:/home/bear# sudo apt-get install uim-applet-gnome uim-xim uim-anthy uim-gtk2.0
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package uim-applet-gnome
root@ubuntu:/home/bear#

where is uim??
How do I find it??
How do I go from here and get input??

Thanks!!

---

### Post by akudewan on 2006-09-09
Try doing _sudo apt-get update_ and then running the command.

uim-applet-gnome is available in the repository, it should work.

And while you're at it, have a look here: [http://akulinux.blogspot.com/2006/06/japanese-input-in-linux.html](http://akulinux.blogspot.com/2006/06/japanese-input-in-linux.html)

---

### Post by seshomaru samma on 2006-09-09
I think the easiest way would be to install SCIM
If I remember correctly it works out of the box in Breezy
I think the pacakage you need is called anthy
try to run
sudo apt-cache search anthy
or 
sudo apt-cache search scim
to find out the package name then apt-get install it

---

### Post by kansaibear on 2006-09-10
Thanks guys, I will check that out and let you know how it goes.

---

### Post by kansaibear on 2006-09-11
> **akudewan said:**
> Try doing _sudo apt-get update_ and then running the command.

uim-applet-gnome is available in the repository, it should work.

And while you're at it, have a look here: [http://akulinux.blogspot.com/2006/06/japanese-input-in-linux.html](http://akulinux.blogspot.com/2006/06/japanese-input-in-linux.html)

OK, tried the sudo apt-get update but the uim-applet-gnome file seems to not exist, just like in my original post above.

the instructions on axulinuku are completely different than what I had at:

[https://help.ubuntu.com/community/JapaneseInputHowToInBreezy](https://help.ubuntu.com/community/JapaneseInputHowToInBreezy)

from what I read, I want to use im-switch because I want to be able to japanese input in the english environment.

I was real exicited when I first installed ubuntu but my excitement is waning.... hope someone can help me over this hump, thanks

---

### Post by shirilover on 2006-09-11
I used the guide here -> [http://www.mrbass.org/linux/ubuntu/scim/]("http://www.mrbass.org/linux/ubuntu/scim/")

I have no problems inputting &#26085;&#26412;&#35486;.

---

### Post by basilwatson on 2006-09-11
dont become sudo or sudo su, install 

sudo apt-get install libapt-pkg-perl

restartthe machine 

then 

 im-switch -z en_AU -s scim-anthy

the en_AU is your local lang and u can find that by typing 

locale | grep LANG=

least that what I just did this morning ..and its working fine 

Thanks to those people who helped me

Stephen

---

### Post by seshomaru samma on 2006-09-11
Install SCIM instead of UIM
Follow the link provided by shirilover and you should be OK
BTW - why did you install 5.10 and not the latest version?
In the latest version Japanese/Chinese input systems are very easy to configure.

---

### Post by Najand on 2006-09-11
SCIM is nice but still has some unsolved conflicts with some gnome and KDE libraries... UIM is nice when you are using gnome, but not kde. As explained in [https://help.ubuntu.com/community/JapaneseInputHowToInBreezy]("https://help.ubuntu.com/community/JapaneseInputHowToInBreezy") you need a few packages like uim-applet-gnome, uim-xim uim-anthy uim-gtk2.0 ,etc.
uim-applet-gnome is available in universe repository, so you just need to add it to your /etc/apt/sources.list

Try editing it using something like gedit.
```
$ sudo gedit /etc/apt/sources.list[CODE]

Check you have all the followings lines there... If some of them exist, but there is an # sign before them remove #.
[CODE]

deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted


deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

```

After you are done, run this command:
```

$ sudo apt-get update && sudo apt-get upgrade

```

Then follow the instruction at ubuntu WIKI.

About im-switch, you don't need to add English Environment.
So
```

im-switch -s uim_anthy

```
would be enough.

---

### Post by seshomaru samma on 2006-09-11
I am also troubled by SCIM's conflict with other libs
I want to try UIM on Dapper but I'm wondering : will UIM allow me to easily switch between English/Japanese/SimplifiedChinese/TraditionalChinese?

---

