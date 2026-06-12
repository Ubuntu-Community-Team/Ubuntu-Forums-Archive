---
title: "Emerald"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-06
How can I get the theme package with loads in? 

What is emerald?
What is beryl?

Is there any difference and which one is better? (I don't know nothing about them)



Thanks
Tom :KS

---

### Post by FuturePilot on 2008-03-06
Emerald is a composite window manager. Beryl is a composite manager which gives all kinds of neat special 3D effects. It's no longer developed though. But it was merged with Compiz to become Compiz Fusion which is installed already on Ubuntu 7.10. You can easily install Emerald with this command.
```
sudo apt-get install emerald
```
Assuming Compiz Fusion is already running
```
emerald --replace
```
will start Emerald.
You can find tons of themes here
[http://www.gnome-look.org/index.php?xcontentmode=103&PHPSESSID=160acbfd087bccb857d5cad1e715c34c]("http://www.gnome-look.org/index.php?xcontentmode=103&PHPSESSID=160acbfd087bccb857d5cad1e715c34c")

---

### Post by steveneddy on 2008-03-06
You must have a 3D graphics card installed (ATI or Nvidia) to get 3D effects.

How to start Compiz?

System --> Preferences --> Appearance

right tab (on top) "Visual Effects"

Select the option on the bottom to get 3D effects.

How to change these effects?

> sudo apt-get install compizconfig-settings-manager



Then go to

System --> Preferences --> Advanced Desktop Effects Settings

Play with that for a while.

Hope you have a couple of hours to spend because when I first got Beryl (back in the day) I wasted hours playing and configuring.

Compiz-Fusion does a better job then Beryl ever did.

---

### Post by Tom--d on 2008-03-06
```
tom@Laptop:~$ sudo apt-get install emerald
[sudo] password for tom:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
emerald is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tom@Laptop:~$ 

```

Already got it. 
I done emerald --replace and all the borders disappear :\

Also the package is different. Its a proper package which once installed, you get like 20 themes. they are the official ones, I think!

---

### Post by Tom--d on 2008-03-06
I've got it all enabled (3D effects and that). 

Emerald is good for me (changes the borders) 

How do i get compiz to do that?
Download themes etc.. 

Also I do have the advance settings for compiz

---

### Post by sillyxone on 2008-03-06
> **steveneddy said:**
> You must have a 3D graphics card installed (ATI or Nvidia) to get 3D effects.


I'm running Compiz with full visual effects on Intel 945G. It's an on-board chip, but yeah, it's 3D capable.

---

### Post by FuturePilot on 2008-03-06
> **Tom--d said:**
> I've got it all enabled (3D effects and that). 

Emerald is good for me (changes the borders) 

How do i get compiz to do that?
Download themes etc.. 

Also I do have the advance settings for compiz

To change other aspects of your theme you need a GTK theme which is independent of Compiz. You can find a bunch here
[http://www.gnome-look.org/index.php?xcontentmode=100&PHPSESSID=1c7527eaffb751e2994bb687a5017f70]("http://www.gnome-look.org/index.php?xcontentmode=100&PHPSESSID=1c7527eaffb751e2994bb687a5017f70")

---

### Post by Tom--d on 2008-03-06
Ah, got emerald working now. Just needed to restart compiz. 


With the emerald package. There is one. I had it before but dont know what happened to it. 
It was an official one. came with like 20 themes. Very good! Just want it back now :D

---

### Post by Eddie Wilson on 2008-03-06
Now you have to download each Emerald theme one at a time. Following the instructions for fetching themes stated in the Emerald Theme Manager won't work in 7.10. I kind of hate that also. Don't know why they did that.

Eddie

---

