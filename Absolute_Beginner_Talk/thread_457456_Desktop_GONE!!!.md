---
title: "Desktop GONE!!!"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by tll_2k on 2007-05-28
I just installed ubuntu yesterday. No prior Linux experience, but I made the plunge. Brand new Gateway E-4601D, now dual booting Windows XP and ubuntu. Everything was working fine. I added some games, configured gaim, installed firestarter, and played with beryl. Last night, I went back into windows before going to bed, and this morning, when I logged into ubuntu, my desktop was gone! I still have my panels, but the desktop doesn't have the hard drives and walpaper anymore. When I right click, nothing happens. Could someone walk me through how to fix it?

Thanks in advance,
Tyler

---

### Post by aktiwers on 2007-05-28
Does Beryl start on boot normally?
Have you tried loggin in, in save mode?
Pick it under session before you log in.. and then try to disable beryl. That way we know if Beryl is causing the problem.

EDit:
To disable beryl from startup go to:
System => Preferences => Sessions
And remove it from there.

---

### Post by tll_2k on 2007-05-28
I disabled beryl. My desktop is still gone, but now it's black. before, it was light blue.

---

### Post by BobLand on 2007-05-28
A while ago I messed up my panels pretty bad so I wanted to restore the desktop to the default.  Note that I am not very experienced.  I was advised to run the following steps which worked for me:

mv .gconf .gconf-old
mv .gconf2 .gconf2-old
mv .gnome .gnome-old
mv .gnome2 .gnome2-old
mv .gnome2_private .gnome2_private-old

ctrl+alt+backspace
ctrl+alt+F1

I was able to reconfigure my panel with a clean default desktop.

Hope this helps.

---

### Post by aktiwers on 2007-05-28
Or try run this from Terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Tuvic on 2007-05-28
Try opening a terminal and type
```
nautilus & 
```

[(I also had the problem, and this worked for me.)]("http://ubuntuforums.org/showthread.php?p=2560042#post2560042")

---

### Post by misfitpierce on 2007-05-28
Can also try enabling config editor under system on drop down and going to nautilus desktop - icons and see if you can tinker with some stuff..

---

### Post by tll_2k on 2007-05-28
Hey BobLand. Thanks for the idea. It didn't fix my desktop, BUT it did fix another problem I was having with highlighting text, because I messed up the colors. Thanks again!

---

### Post by regomodo on 2007-05-28
definetly a beryl misinstall i'd say. I had exactly the same issue when i cocked up a beryl install in edgy. I tried resetting x and removing beryl but nothing really worked. A fresh Ubuntu reinstall was the easiset and quickest solution

---

### Post by tll_2k on 2007-05-28
> **aktiwers said:**
> Or try run this from Terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

I tried this, but when I got to the screen that says:

> Configuring xserver-xorg   

Users of PowerPC machines, and users of any computer with multiple video 
devices, should specify the BusID of the video card in an accepted      
 bus-specific format.

it won't let me continue. I hit enter, like all the other pages, but nothing happens. 
What am I doing wrong?

---

### Post by tll_2k on 2007-05-28
> **Tuvic said:**
> Try opening a terminal and type
```
nautilus & 
```

[(I also had the problem, and this worked for me.)]("http://ubuntuforums.org/showthread.php?p=2560042#post2560042")


it says nautilus not installed. so "sudo apt-get install nautilus"?

---

### Post by Nikron on 2007-05-28
Hold on guys, when that happens something very simple has gone wrong.  Nautilus didn't start up when he started gnome.  Nothing to do with X.  He needs to fix his session to have the default nautilus start up and make his Desktop work

Edit: someone beat me to it.  Yeah install nautilus if you don't have it

---

### Post by aktiwers on 2007-05-28
> **tll_2k said:**
> I tried this, but when I got to the screen that says:



it won't let me continue. I hit enter, like all the other pages, but nothing happens. 
What am I doing wrong?

Sounds like you have to reinstall nautilus then?

Well I dont know why it doesnt take you any longer than that.. did you try to use the arrows on your keyboard to go to the "ok" botton?

EDIT:
Nikron.. It think you are right!
Wouldnt a reinstall of Nautilus fix this?

---

### Post by tll_2k on 2007-05-28
Ah-ha! i had to press the right arrow to get to the ok. just reinstalled nautilus, now log out and back in, or what?

---

### Post by aktiwers on 2007-05-28
> **tll_2k said:**
> Ah-ha! i had to press the right arrow to get to the ok. just reinstalled nautilus, now log out and back in, or what?

Yeha try that :) 
And get back to us and tell if it worked :popcorn:

---

### Post by tll_2k on 2007-05-28
YAY!!!! it worked! Thank all of you SOOOO much!

---

### Post by aktiwers on 2007-05-28
Your Welcome! :)
Glad it worked.

---

### Post by pospam on 2007-05-30
Just to say that I had the same problem and  now it is fixed.
I uninstalled beagle and pidgin and I guess one of those took nautilus with it
without me noticing. I hope nothing else is gone that I will need.
Do you guys know how you can check if your install is not corrupted?
I mean if there is a way to know if I am missing any necessary software or dependency.
Cheers P.

---

