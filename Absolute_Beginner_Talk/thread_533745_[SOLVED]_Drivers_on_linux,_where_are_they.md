---
title: "[SOLVED] Drivers on linux, where are they?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-08-24
Hello, another topic : )

Where are the drivers in linux? Are they treated like packages? Or there is a certain place that contains these drivers?

I think that I have a little problem with my video driver, because when I try to play chess 3d, it shows a few bugs.

And in the videos that I play with VLC media player or with Movie Player it also show some bugs, almost never it shows the video properly.

Thanks again.

Bruno Krebs

---

### Post by igknighted on 2007-08-24
What video card do you have?  Chances are it is in the repositories, so search in synaptic.  If you have anything other than ATI/Nvidia though you might be stuck with what you have (with some tweakable performance options here and there).

---

### Post by brunoskrebs on 2007-08-24
Hi,

now I have a real problem. I was following some step from a website, I dont know wich, because now I'm back in Windows, trying to fix my problem.

Then the site told me to do thisÇ
> 
# sudo /etc/init.d/gdm stop
# dpkg-reconfigure xserver-xorg
# sudo /etc/init.d/gdm start


So I did it, tried to put what I thought was the right configuration, and then when I started the gdm again, the bug become worse. Now I cannot see anything after the login. Until the login it shows properly, then when I put my user a psswd it begins loading, and then the screen becomes all the same collor, and its impossible to see anything now.

What should I do?

Thanks again.

---

### Post by r4ik on 2007-08-24
Please post you're machine specs,like graphic card as Igknighted requested.

---

### Post by shearn89 on 2007-08-24
when you get to a login screen, press "ctrl-alt-f1", then do the middle command again, and let it choose defaults. It should get you back to a working config, although it will be the same as before you tried to change it.

---

### Post by brunoskrebs on 2007-08-24
Oh man sorry, I totally forgot to put the specs...

My laptop is a Toshiba Satelite a135-s4656

The video card is Mobile Intel 945GM/GU Express Chipset Family

I tried to put all on the default, but there is no default the program asks a lot of stuff and I have toi choose.]

Thanks again

---

### Post by igknighted on 2007-08-24
Ok, you shouldn't need to install any drivers.  The intel drivers are fully open-source and are included.  If you are having screen res issues, there is a package called 915resolution (IIRC) that might help you out.  I don't know much about the intel drivers, but I think there are a few lines you can add to xorg.conf to help out video playback and the like.  Hopefully someone with more experience with them will see this.

---

### Post by dca on 2007-08-24
> **igknighted said:**
> Ok, you shouldn't need to install any drivers.  The intel drivers are fully open-source and are included.  If you are having screen res issues, there is a package called 915resolution (IIRC) that might help you out.  I don't know much about the intel drivers, but I think there are a few lines you can add to xorg.conf to help out video playback and the like.  Hopefully someone with more experience with them will see this.

Exactly, you should be able to apt-get install 915resolution right from the repos via the CLI...  Be sure to update (refresh) repos prior..  My Acer laptop had the same issue where the default display was set to 640x480.  After installing the 915 package, restart the laptop, it went to 1280x800...

---

### Post by brunoskrebs on 2007-08-25
How do I reset the default configuration of my video: Because I tried a lot of times to reconfigure it with "# dpkg-reconfigure xserver-xorg" but I am not doing it right. Because my video still doesnt works. And now I have to post from windows :P

---

### Post by daverich on 2007-08-25
try the new intel drivers.

remember to remove the old ones first ;)

so try

sudo apt-get install xserver-xorg-video-intel

you might try removing the ones that are currently installed which will be either

sudo apt-get remove xserver-xorg-video-i810

or

sudo apt-get remove xserver-xorg-video-i740

Kind regards

Dave Rich

---

