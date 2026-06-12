---
title: "lost xorg after fatal upgrade"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by WijbrandSchaap on 2005-10-11
OK, tell me i'm an idiot, but i was tired and thougt i was invulnerable. After upgrading to breezy i got stuck with a libc6 version that came form debian unstable (tried some things with mplayer and wine in my hoary-past). I wanted to remove that, to be able to install the breezy locales. It went on to remove everything from breezy. I panicked an shut down my computer. I thought: as long as i have apt, i can reinstall everything. So i reinstalled gnome, but no luck: my display drivers got lost in the process. My question: how do i get breezy up and running again, while i now only have a command line and the ability to run apt? 
(this is sent using my laptop, whisch is running breezy in a perfect way...)
Thanks in advance!
Wijbrand

---

### Post by Knome_fan on 2005-10-11
Try to install ubuntu-desktop.
If that doesn't help, also make sure you have ubuntu-minimal and ubuntu-standard installed.

---

### Post by WijbrandSchaap on 2005-10-11
I seems to be working! I knew it had to be something simple! Thanks very much!

---

### Post by WijbrandSchaap on 2005-10-11
Sorry. I was a bit premature.
All lost  files have reinstalled, but module nvidia is still missing, so x won't start.
Also, when trying to install ubuntu-minimal, it keeps telling me that i still have the wrong libc6 installed. It is the version from debian unstable, and i can't force apt to install libc6-i686 form breezy, only at the risk of freeing up 3 gigs of ubuntu on my harddisk, and that's not nice.
What to do? apt-get install nvidia doesn't work also.

Please?!

---

### Post by Knome_fan on 2005-10-11
Ok, try to install the ubuntu libc6 with:
apt-get install libc6=2.3.5-1ubuntu12
(this is the current breezy version for me)

after that I think you need to install nvidia-glx to get nvidia working again.

---

### Post by Kyral on 2005-10-11
You are going to have to compile the NVidia module yourself I'm afraid. But fear not! Its not that hard!

Go to the NVidia site and download the 7667 driver package for Linux.

Now print out this next part because you are going to have to shutdown X (Or is it already gone)

Jump out to a Virtual Terminal with CTRL+ALT+F1 and login.

do

```
sudo /etc/init.d/gdm stop
```

This will shutdown GDM, which needs to be stopped during this time.

Now in order to compile the module you need to have gcc 3.4 installed and also the Linux Kernel Headers for your kernel.

```
sudo apt-get install gcc-3.4
```

Now find out your kernel version.

```
uname -r
```

and install the headers

```
sudo apt-get install linux-headers-(uname -r)
```

Replace "(uname -r)" with the output from it.

Now we are ready. Tell the computer to use GCC 3.4 instead of GCC 4

```
export CC=/usr/bin/gcc-3.4
```

Now cd to where you downloaded the NVidia package and run it with

```
sudo sh ./<filename>
```

Just keep hitting okay and whatnot.

When its done

```
sudo dpkg-reconfigure xserver-xorg
```

And pick the NVidia Module (as well as load every module EXCEPT dri)

Then just start X again

```
sudo /etc/init.d/gdm start && logout
```

---

### Post by Knome_fan on 2005-10-11
[QUOTE=Kyral]You are going to have to compile the NVidia module yourself I'm afraid.[/QUOTE]

Huh? Why?

Nice howto btw.

---

### Post by Kyral on 2005-10-11
Wait....NVidia GLX works in Breezy now? I said that because last I knew it was still busted. If 

```
sudo apt-get install nvidia-glx
```

works, then go for it. If not you still have to make the NVidia Module from that compile. 

Now I'm confused....

---

### Post by Knome_fan on 2005-10-11
Well, it works for me here. :D

---

### Post by WijbrandSchaap on 2005-10-11
Yep nvidia glx worked fine, i have a great breezy system working again. Thanks a lot! My computer is even talking dutch to me again. Which is nice.
Just one problem remains: i get an error at the loginscreen, telling me i get the standard login in stead of the nice one. After logging in i get this nice error message about an xkb-configuration, and also my 'Desktop' and 'Trash'-icons have gone to the dogs.
Has this already been solved elsewhere?

---

