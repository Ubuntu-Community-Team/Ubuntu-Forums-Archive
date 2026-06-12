---
title: "Ok So I think Ubuntu is Installed now..."
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Sonastylol on 2008-01-31
I went thru the installation process, did my partitioning stuff, took the disk out like it said and then rebooted.  My VGA cable flashed while starting up and then the display came. 

** I have 2 issues**

**1)**I finally found out how to change the display resolution, and it looks correct- 1280x768, BUT, the resolution on my screen is not complete. I have a 26" TV and on XP my resolution looked fine on 1280x768, but now its getting cut off on the right side... I cant see my windows scrollers or anything.

**2)** I was never asked to install any video drivers, sound drivers, etc.. so I dont know if they are fully functional.. websites seem to be loading a BIT slower than normal... IDK if my graphics are on correctly then.

I have a Q6600 quad 2.4ghz  w/ an 8800GTS, 2GB ram etc etc..

Am I installed completely? Do I have to do anything or am I done once the CD runs?

---

### Post by jseiser on 2008-01-31
if you can boot up without the cd in the drive then it is installed.  Since you have a nvidia card i would imagine you are currently using the "nv" driver for your graphics card.  You can also install the driver from nvidia which is closed source, but i believe you need for 3d Acceleration and opengl things.  In a normal ubuntu install, if you have a nvidia card, in your top panel their should be a 'restricted drivers manager' icon, which you could click on, and it will show you that you can install the closed source driver, it would also show wireless drivers etc.  You can always check /etc/X11/xorg.conf and see what driver you are using.

---

### Post by jan quark on 2008-01-31
when your internet connection is up, you can check the graphic drivers
via the restricted driver manager

 I would suggest the application envy for nvidia card, it installs everything automatically

---

### Post by Sonastylol on 2008-01-31
Ok I did the desktop search for the driver manager and found it, it found my video card and asked me to enable - doing that now. This should fix THAT problem...

The reason I ask about the other stuff is because I saw a topic that said to install Ubuntu I had to open some file and edit a few things with "fiesty" but learned that fiesty is an old version of Ubuntu, so I decided NOT to do that...was I wrong?

---

### Post by size6 on 2008-01-31
You could install the Nvidea drivers to see if that makes a difference.

1. if you are using 7.1, try going to Sytem -> administration ->  Restricted Devices Manager and see if you can install them from there, if not:

2.Try [this]("http://ubuntuforums.org/showthread.php?t=432056&highlight=nvidia+8800GTS+install") thread for installing them, or look around the forums or help.ubuntu.com:

[http://ubuntuforums.org/showthread.php?t=432056&highlight=nvidia+8800GTS+install]("http://ubuntuforums.org/showthread.php?t=432056&highlight=nvidia+8800GTS+install")

---

### Post by Sonastylol on 2008-01-31
The graphical issue has been resolved thank you.

Please address 2nd issue, after that, closed topic !   :)

---

### Post by jseiser on 2008-01-31
> **Sonastylol said:**
> 
**2)** I was never asked to install any video drivers, sound drivers, etc.. so I dont know if they are fully functional.. websites seem to be loading a BIT slower than normal... IDK if my graphics are on correctly then.


you should now have the nvidia driver installed,  ubuntu detects your sound for you, so thats taken care of.  Everything should be good to go.

---

### Post by Sonastylol on 2008-01-31
Thank you!

I saw a post I saved on windows that I bookmarked before I deleted the partition... something about someone asking how to make his theme and desktop look nice, the post was great and had links to things called eye-candy, gnome something customize, and some other links to resources.


I cant find it, do you know what I'm talking about?

---

### Post by jan quark on 2008-01-31
I think  you mean the compiz effects

compiz is preinstalled with gutsy

I had to do the following to enable the effects

run synaptick package manager
can be found in system > administration > synaptic

install the following package

xserver-xgl
just type this into the search

now log out and select during the login the xclient session

go to system > preferences > appearance and select visual effects normal or extra

to further tweak the effects install the Advanced Compiz Desktop Effects via the add/ remove application 

ask for more

---

### Post by billgoldberg on 2008-01-31
> **Sonastylol said:**
> Thank you!

I saw a post I saved on windows that I bookmarked before I deleted the partition... something about someone asking how to make his theme and desktop look nice, the post was great and had links to things called eye-candy, gnome something customize, and some other links to resources.


I cant find it, do you know what I'm talking about?

This website should help

[http://www.gnome-look.org](http://www.gnome-look.org)

to change the look of the windows -> gtk2 theme (install that in system -> prefer. -> appereance
you also install the icons there
under beryl you find the emerald themes.

---

### Post by Sonastylol on 2008-01-31
Thanks for the post man, gnome-look looks like an awesome website.

But one thing that I'm looking for again - was a post that taught the user how to make those bars on the desktop with icons on them, and how to make those transparent bars have changable icon sizes.. it looked really nice. I dont necessarily want to download someone's pre-made theme from the gtk2 selection.

---

### Post by Sonastylol on 2008-01-31
I also cant seem to download those GTK2 files for the themes...


I click to download and it tries to open them, if I right click to download ( save target as ) it says it cant download...


I dont know why... am I not allowed to save files from the internet to my desktop in linux?

please help... going to class so I'd love the solution by the time Im back

---

### Post by Sonastylol on 2008-01-31
forgot to add that this post ALSO taught how to create custom splash pages.. Thank you!!! I am very interested in that.

---

### Post by Sonastylol on 2008-01-31
:( bump, thanks guys

---

