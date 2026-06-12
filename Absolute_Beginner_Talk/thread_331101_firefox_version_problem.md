---
title: "firefox version problem"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by madmetal on 2007-01-04
i am using dapper and firefox 1.5.0.1
at todays updates there was firefox 1.5.0.8
i downloaded the updates close the firefox but still use the 1.5.0.1 
how can i move on to 1.5.0.8 ?
(i am sure i have caused the problem :-#  )

---

### Post by oyvindaa on 2007-01-04
If you'd like to have the 2.0.0.1 version, follow the instructions on aysiu's site:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Particularly the script (option 4) is an easy way to get the newest Firefox :)

---

### Post by madmetal on 2007-01-04
> **oyvindaa said:**
> If you'd like to have the 2.0.0.1 version, follow the instructions on aysiu's site:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Particularly the script (option 4) is an easy way to get the newest Firefox :)


i know the site and the script but i would still like to use the 1.5 version.
and since i got installed the 1.5.0.8 version why use the 1.5.0.1 version..
:-k

---

### Post by ajgreeny on 2007-01-04
As of today, Jan 4th, it's firefox 1.5.0.9.  I can't imagine why you are still on 1.5.0.1, so are you certain?  Go to Help>About Mozilla Firefox, and it will tell you the version used.

---

### Post by madmetal on 2007-01-04
yes its sure 1.5.0.1..
i downloaded the updates including the 1.5.0.9 but i am still on 1.5.0.1
i think i had this version installed by myself.. so how can i get rid of it and go move on to .9?
:-k

---

### Post by petersjm on 2007-01-04
I think you should be seriously considering upgrading to 2.0.0.1 - there's nothing to hold you back. Better security, and now that 2.0 has been out a while, the majority of extensions and themes all work on it now.

---

### Post by CroEragon on 2007-01-04
> **petersjm said:**
> I think you should be seriously considering upgrading to 2.0.0.1 - there's nothing to hold you back. Better security, and now that 2.0 has been out a while, the majority of extensions and themes all work on it now.

I agree. Also i think that support for 1.5 is about to expire (i dont know exactly dont kill me if im wrong.) Anyway, why would you use old one when Mozilla is now focusing on next major release 3.0 Codename Gran Paradiso. I tried alpha it still got some bugs (e.g Internet baking) but still it is fairly good piece of software if you consider it is alpha. And it uses new Gecko 1.9, not 1.5 like FF 1.5 and FF2.0.
Cant wait 3.0

---

### Post by bikeboy on 2007-01-04
Did you install a version other than the Ubuntu one through the repos at some stage?

This should give an idea.
```
ls -l /usr/bin/firefox
```

---

### Post by goatflyer on 2007-01-04
Just to add to the previous post 
```

which firefox

```

will tell you the path of the firefox which gets loaded (in case you have more than one of them installed somewhere).

hint: if it says something like
/usr/bin/firefox
then type
```

ls -ld /usr/bin/firefox

```
to see if it is the actual binary executable, or a symlink pointing to somewhere else.  Keep following the links until you find the binary.
 
System>Preferences>Preferred Applications will tell you which firefox Gnome wants to load.  You can probably sort out your problem with this info.

---

### Post by geronimo12 on 2007-01-04
this is my first post on this fotum so first of all I want to say hello to you :)

2) I'm trying to install firefox 2.0.1 by using script from this site: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

after first step of installation following text appears: Please choose the localization (language) for firefox. Enter the number of your                                                                                      choice from the list below.

That's my problem. there is no list and I don't know what is the number of my localization. Do You have any idea about it? 

sorry fo my English :/

---

### Post by madmetal on 2007-01-04
thanks anyone for the help untill now..
well i maybe update to firefox 2.0.0.1 but first i want to remove the 1.5.0.1 version.

/usr/bin$ ls -ls /usr/bin/firefox
0 lrwxrwxrwx 1 root root 20 2006-02-11 23:31 /usr/bin/firefox -> /opt/firefox/firefox

so i guess the 1.5.0.1 version is located at /opt/firefox/ right?

i just have to erase this folder and make use of  /usr/bin/firefox/firefox 
:-k 

its easy to just upgrade to 2.0.0.1 but i want to make things right, (and learn )

---

### Post by goatflyer on 2007-01-04
Do NOT erase the 1.5 version! There are supposedly some gnome dependencies that will be broken!

---

### Post by bikeboy on 2007-01-05
Regarding the script question, it might be with checking with the authors of the script. Which I might add, is great when it works, as it did for me. Thanks aysiu :)

To the OP, yes the output you posted indicates that /opt/firefox/firefox is the 1.5.0.1 version. To upgrade it to the most recent version you should be able to open a terminal and type "sudo firefox", then go to Tools > Check for updates. Let it do its thing, then restart as root once more, after that you can run it as normal again.

Upgrading to 2.x in the long run is best though, and aysui's (psychocats) script did a great job of that on my Dapper install (I'm using it right now in fact).

---

### Post by madmetal on 2007-01-05
> **bikeboy said:**
> To the OP, yes the output you posted indicates that /opt/firefox/firefox is the 1.5.0.1 version. To upgrade it to the most recent version you should be able to open a terminal and type "sudo firefox", then go to Tools > Check for updates. Let it do its thing, then restart as root once more, after that you can run it as normal again.

Upgrading to 2.x in the long run is best though, and aysui's (psychocats) script did a great job of that on my Dapper install (I'm using it right now in fact).

thanx! it works fine ;) 
like i said i will update to 2.0 soon but first i want to know how to update to 1.5.0.9 one..
:D

---

