---
title: "I just messed up my comp..."
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by nmehsr on 2006-06-22
I was looking at some ubuntu guide and it mentioned using apt-get install kubuntu-desktop to try kde. So i did but all i got was a bunch of programs that i didn't need and a different splash screen. I think i got rid of the programs in synaptic   and in doing so caused my computer to give me unintelligible lines of text on start up. I ran it in diagnostic mode (or whatever its called) and used apt-get update and i got it to start up at least. So i have 2 questions.
1) is there any way to make sure i have all the necessary packages that came with ubuntu because i may have deleted something crucial.
2) is there any way to change back the splash screen to the standard ubuntu one?

---

### Post by catlett on 2006-06-22
These are the commands I would run. The first one refreshes the apt cache. The second one uses aptitude to remove "kde". The third reinstalls ubuntu desktop just in case (it may say it is already the newest version and not do anything). The last runs an upgrade to make sure you have all the latest packages for ubuntu.```
sudo aptitude update 
``````
sudo aptitude remove kubuntu-desktop
``````
 sudo aptitude install ubuntu-desktop
``` ```
sudo aptitude upgrade
```

P.S. If you want kde with less "fluff"  aysiu's guide says to run this instead of apt-get kubuntu-desktop```
 sudo aptitude install kde-core 
``` Aysiu's site is here [http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html) About halfway down the kde-core command is mentioned.

---

### Post by rowanparker on 2006-06-22
1. Run ```
sudo apt-get install ubuntu-desktop
```
2. Yes, if you havn't removed kubuntu then do so. You need to make it use GDM instead of KDM. I'm not sure how.


Edit: Damn, shouldn't of been so slow :(

---

### Post by bruce89 on 2006-06-22
If you don't want KDE installed as well see here - [http://psychocats.net/ubuntu/puregnome.php](http://psychocats.net/ubuntu/puregnome.php), as aptitude won't remove it all, as you didn't use it to install kubuntu-desktop in the first place.
[QUOTE=nmehsr]2) is there any way to change back the splash screen to the standard ubuntu one?[/QUOTE]
```
sudo update-alternatives --config usplash-artwork.so
```
Which splash screen is it?  If it's the black one immediatly after boot, this will fix it.

---

### Post by SkyNet2029 on 2006-06-22
you can set which display manager is run by changing /etc/X11/default-display-manager. 
run 
```
$sudo dpkg-reconfigure gdm
```
 
and select kdm/gdm in the menu that will appear.

As for making certain all of the ubuntu-ddesktop is correctly installed, you can do this
```
$sudo apt-get install ubuntu-desktop --reinstall
```

And if you started out using apt--get then you should stick with that, and not use aptitude, since apt-get installed files list and whether they were installed by you or to satisfy dependencies listing would be a tad bit off, since apt-get does not keep track of what aptitude does, and vice-versa.

---

### Post by bruce89 on 2006-06-22
[QUOTE=SkyNet2029]And if you started out using apt--get then you should stick with that, and not use aptitude, since apt-get installed files list and whether they were installed by you or to satisfy dependencies listing would be a tad bit off, since apt-get does not keep track of what aptitude does, and vice-versa.[/QUOTE]
The difference is that if you install a program, then remove it with apt-get, then all the packages that were depended upon by the program are not removed.  This way you get a load of unused libraries all over the place, wasting space.
aptitude removes all the packages that are required by the package you are removing, this way there are no unused libraries left over.

---

### Post by SkyNet2029 on 2006-06-22
Thanks for clearing things up for me bruce89. I thought the only diff was what I had posted.

---

### Post by nmehsr on 2006-06-22
well thanks for everything haven't noticed problems yet so looks good :-)

edit: i just restarted and my exit splash was the standard ubuntu but my startup splash was still kubuntu.
i went back into the update-alternatives and noticed this.
```

sudo update-alternatives --config usplash-artwork.so

There are 2 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/lib/usplash/usplash-default.so
 +    2        /usr/lib/usplash/kubuntu-splash.so

```

what does the "+" indicate? can i change it back?

---

### Post by bruce89 on 2006-06-22
[QUOTE=nmehsr]well thanks for everything haven't noticed problems yet so looks good :-)[/QUOTE]
No problem, feel free to post more if you have any, but I'll be offsky soon.

---

### Post by nmehsr on 2006-06-22
Well it was working fine, just the little issue of the startup splash

---

