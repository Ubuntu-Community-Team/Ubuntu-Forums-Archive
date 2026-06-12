---
title: "Borked My xorg.conf"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by HokkaidoHillbilly on 2007-04-06
Um, kind of embarassing, but in trying to install Beryl, I messed up my xorg.conf file and can only boot to the command line now.  I know exactly what I did and the line I need to fix, but it's been like 10 years since I've used vi and have no idea how to edit the file.

Any ideas?

EDIT:  Cool beans.  Everything up & running smooth.  Thanks for all the help!  You guys're :guitar: rock stars!

---

### Post by 67GTA on 2007-04-06
Run "sudo dpkg-reconfigure xserver-xorg" at command line and reset your xorg.conf file.

---

### Post by HokkaidoHillbilly on 2007-04-06
One thing I forgot to mention is that before this little bit of failed surgery, I made sure to make a backup of xorg.conf, so will the above command just revert back to the backup?

---

### Post by DougieFresh4U on 2007-04-06
Sorry to hear that happened!! I "borked" my x last week and I used a live cd to mount my hard drive and fetch my back up x. Don't know if this will help you out.

---

### Post by adam.tropics on 2007-04-06
Try nano.

```
sudo nano /etc/X11/xorg.conf
```

then edit, then <ctrl>o , followed by <enter>, and <ctrl>x to exit

---

### Post by 67GTA on 2007-04-06
Try to run "sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf" at the command line and see if that will work. You will have to change the "/etc/X11/xorg.conf.backup" to what you named your backup. If you didn't rename it, the command should work.

---

### Post by 67GTA on 2007-04-06
The first post is the command to rewrite the whole xorg.conf file.

---

### Post by shavenlunatic on 2007-04-06
67GTA: He mentioned that he forgot to backup his xorg.conf



failing the above suggestions..another option is to reinstall your nvidia drivers either by (if you have it installed) typing

```
envy -t
``` at the command line.. and selecting option 1

or

```
sudo apt-get install --reinstall nvidia-glx
```

---

### Post by HokkaidoHillbilly on 2007-04-06
Thanks adam.tropics!  The nano command was just what I needed!

Thanks as well to all of you for all the advice. :)  Now if I can just figure out how to get Beryl to run w/o making my screen look like a bad TV signal... :roll:

---

### Post by adam.tropics on 2007-04-06
no worries...what video card, and what guides have you used?

---

### Post by HokkaidoHillbilly on 2007-04-06
Sorry for the delay getting back to ya...really ended up screwing the pooch & had to do a total reinstall of Edgy. *sigh*

Anyhoo, I used the envy script to install nVidia drivers and [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29") page for Beryl.

---

### Post by HokkaidoHillbilly on 2007-04-07
I know this thread's dropped pretty far, but just to let those of you who helped me know, I got everything working somehow and am now enjoying all sortsa Beryl goodness.

Cheers to all of you!

---

### Post by shavenlunatic on 2007-04-08
:)

---

