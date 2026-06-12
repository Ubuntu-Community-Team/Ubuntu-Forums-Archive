---
title: "Nvidia 6800GT ( I found a good how to install but...)"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by newbsaucer on 2007-02-03
First let me say that I am switching to Ubuntu, I just need some help getting it right so Ic an use it. I want to install the drivers for my Nvidia 6800gt card and I found a neat little how-to on it but i ran into a road block in the how to....and maybe I am just too used to macs and windows boxes (being a network admin and tech specialist for them for 15 years now) but this seems overly complicated to me. 

[CLICK HERE FOR THREAD I AM TALKING ABOUT]("http://www.ubuntuforums.org/showthread.php?t=336412&highlight=nvidia+6800gt")

anyway there is a section there (Section 4) that basically says I need to stop my session of Xserver and go into terminal mode......but does nothing to explain how to do this. It mentions ctrl+alt+f1 but when i depress that Key combination nothing happens. So..what am I missing?

Also, wine.....how is this used? Keep in mind i am a TOTAL beginner. I have read the how to's but they seem to be written by people who WANT to help but really don't know how to tell someone how to do things from step 1 and on. I have wine installed on my machine ( I think or hope) but no idea how to get world of warcraft to play on it....yes...I want to play my wow on linux.

any help you can provide is thankfully appreciated.

---

### Post by bodhi.zazen on 2007-02-03
To stop X :```
sudo /etc/init.d/gdm stop
```

To then re-start : ```
sudo /etc/init.d/gdm start
```

Now, to install the Nvidia driver, easy way:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And : [How to wine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by vigleik on 2007-02-03
Did you try easyubuntu? It's the easiest way to install the nvidia driver, and it also helps you with a bunch of other things. See [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by pseudonym on 2007-02-03
> **newbsaucer said:**
> anyway there is a section there (Section 4) that basically says I need to stop my session of Xserver and go into terminal mode......but does nothing to explain how to do this. It mentions ctrl+alt+f1 but when i depress that Key combination nothing happens. So..what am I missing?
Hi, when you press that key combo from within X it should take you to a console login prompt. If it doesn't try logging out first within X (to the graphical login screen) and try Ctrl+Alt+F1 again. Then just enter your user name and password and continue on with the howto.

Or just try Easyubuntu as just mentioned or [Automatix]("http://www.getautomatix.com/"). Either will make your life a lot easier.

> **newbsaucer said:**
> Also, wine.....how is this used? Keep in mind i am a TOTAL beginner. I have read the how to's but they seem to be written by people who WANT to help but really don't know how to tell someone how to do things from step 1 and on. I have wine installed on my machine ( I think or hope) but no idea how to get world of warcraft to play on it....yes...I want to play my wow on linux.

any help you can provide is thankfully appreciated.
You should check out the [Ubuntu Gaming Forum]("http://www.ubuntuforums.org/forumdisplay.php?f=93"). There are howtos on exactly this topic there. Also, if you don't know already, the bulk of the documentation relating to wine is held at their project site, [winehq]("http://www.winehq.com/").

HTH

---

### Post by newbsaucer on 2007-02-03
Thank you all for your posts!! I really appreciate the help as I try to leave windows behind for good in my home. Thank you. I will try these solutions out and see what happens and then i will post back. I hope to one day be useful with this O/S

---

### Post by igknighted on 2007-02-03
Before you try that stuff, just open synaptic and look for the package nvidia-glx.  It is the official NVIDIA driver from the Ubuntu repositories, already packaged for you.  Just install that package and you should be good to go.

---

### Post by newbsaucer on 2007-02-03
Just one tiny issue. The driver is installed but i can't seemt o get my resolution up to 1600X1200 or higher. i have a widescreen monitor so ...this ismost likely a monitor driver issue? Nevermind let me research that before i open my fat mouth.

---

### Post by bodhi.zazen on 2007-02-03
Restart X

You should see the Nvidia splash screen, no ?

OK

Open a terminal and enter : ```
nvidia-settings
```

click on "X Screen Display configuration"

viola

If that fails post your xorg.conf

---

### Post by vigleik on 2007-02-03
> **newbsaucer said:**
> Just one tiny issue. The driver is installed but i can't seemt o get my resolution up to 1600X1200 or higher. i have a widescreen monitor so ...this ismost likely a monitor driver issue? Nevermind let me research that before i open my fat mouth.

Try "sudo dpkg-reconfigure xserver-xorg" and be sure to select 1600x1200 when you get to that part.

---

### Post by newbsaucer on 2007-02-05
oh man, see i did some research and thought that i had to edit my xorg.conf so i did. but something happened and now when i boot into ubuntu i dont get into ubuntu at all. I get to a black screen with a bluw square that says I fubared my machine. It basically says "You are a dumb *** and screwed up, go back to windows"

So now, how do i get back into my xorg.conf file and replace it with the backup copy of it i made just in case prior to fiddling with it. Total newbie here to linux in case I have nto mentioned that.
 
I know linux takes a little more work than windows. I do. So please just a little patience and I am sure eventually I wont be such a total loss.

---

### Post by newbsaucer on 2007-02-05
> **vigleik said:**
> Try "sudo dpkg-reconfigure xserver-xorg" and be sure to select 1600x1200 when you get to that part.


I will try this when I get home and manage to undo the damage I have done to ubuntu somehow.

---

