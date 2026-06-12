---
title: "Unable to turn on Desktop Effects with nVidia Card"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Vegabondsx on 2007-12-14
Hi, I've recently installed Ubuntu 7.10 on one of my older PCs and things seem to be running ok (some things are a little sluggish) but desktop effects no longer work while they did in 7.04 which I tried a few months ago. I'm using an nVidia card, so its not a backlisted card.

The error message: Desktop effects could not be enabled

Here are my Specs:

AMD Athlon XP 2400+
nVidia geForce 2 MX 100/200
6gb ATA Hard Drive
256mb PC3200 DDR RAM

I have installed the restricted drivers and still no luck. I typed compiz in the terminal and this is what I got back:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:06.0 0300: 10de:0111 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x960) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

```

I have also tried SKIP_CHECKS=yes compiz and that didn't work either.

Any help would be appreciated.

:)

---

### Post by fs3rp4 on 2007-12-14
Forget it. Nvidia driver isn't workin with 7.10. The system freeze (hang) everytime.

Look this post: 

[http://ubuntuforums.org/showthread.php?t=587905&goto=newpost](http://ubuntuforums.org/showthread.php?t=587905&goto=newpost)

---

### Post by MangasColoradas on 2007-12-14
> Checking for Xgl: not present

You would need xgl even if there was no other reason for it not working.

This the 'how to' for ATI cards. (Iknow yours is Nvidia but...as you can see xgl is needed).
[http://ubuntuforums.org/showthread.php?t=580748&highlight=install+compiz](http://ubuntuforums.org/showthread.php?t=580748&highlight=install+compiz)

---

### Post by rfurman24 on 2007-12-14
Nvidia drivers are working in Gutsy. I am using them. I just installed the Nvidia drivers via synaptic then enabled the drivers with restricted manager and rebooted and everything works great.

---

### Post by Vegabondsx on 2007-12-14
With 7.04 all I had to do was enable the restricted drivers.

Anyways, I was able to get it to work! This is what I did, hopefully it'll help others who have the same problem:

Using the Terminal I typed in ```
sudo apt-get install xserver-xgl compiz-gnome
```

After that I typed in ```
compiz
``` in the terminal and it gave me;

```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting gtk-window-decorator

```

I then got a notification that my XGL settings have been changed and that I need to log out for the effects to work. I then logged out and logged back in and now I can select Normal and Extra Desktop effects without any problems!

Thanks everyone for your help!

---

### Post by Vegabondsx on 2007-12-14
I wrote up what was said here for reference at this address: [http://www.chithe.net/?p=86](http://www.chithe.net/?p=86)

---

### Post by bfowler on 2007-12-16
i am having the same problem.
nvidia geforce fx 5200

after entering in compiz, i get

Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback:  usr/bin/metacity

?

---

### Post by abicash on 2007-12-20
Yes the same thing for me
[COLOR="Red"]Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0028 (rev 15) (prog-if 00 [VGA])
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
aborting and using fallback: /usr/bin/metacity [/COLOR]

I have nvidia legacy (RIVA TNT2/TNT2 Pro)

---

### Post by IndianaThreepwood on 2007-12-28
abicash, I'm having the exact same problem as you.
And when I rebooted, nVidia crashed Ubuntu, throwing me back to the login/welcome screen. I had to log on in 'safe mode' and uninstall xserver-xgl.
Now I'm back to square one, but at least Ubuntu is running!
Can anyone help me?

---

### Post by ingram on 2007-12-28
This may sound redundant but have you:

1. installed the restricted drivers for your NVIDIA card
2. installed compizconfig

if you have done those two things please let us know.

---

### Post by abicash on 2007-12-29
Hi 
I have been following up on this thread 
[http://ubuntuforums.org/showthread.php?p=4033117#post4033117]("http://ubuntuforums.org/showthread.php?p=4033117#post4033117")

---

### Post by thamood on 2007-12-29
HI....**there is a "nvidia-glx" package**...look for it in synapatic manager if it's not installed then install it......and try to enable Desktop Effects.....good luck

---

### Post by IndianaThreepwood on 2007-12-30
I have the restricted drivers installed, along with compizconfig.
Plus my resolution is fine, unlike other users with this driver problem. I just cannot enable visual effects (I get the "Desktop effects could not be enabled" error message)
I have the nvidia-glx-legacy driver installed, as I have an older TNT2 card (hence I no longer have the nvidia-glx driver installed - already tried that). I also tried the whole xserver-xgl thing, but that crashed my Ubuntu, and I needed to use the Failsafe session to get back to 'normal'. I even tried updating the /etc/X11/xorg.conf file, and ended up reseting my keyboard layout. Man, did I have a hard time finding the forward slash to get my german keyboard working again! :)
Thanks for the suggestions, any more?

---

### Post by abicash on 2007-12-30
> **IndianaThreepwood said:**
> I have the restricted drivers installed, along with compizconfig.
Plus my resolution is fine, unlike other users with this driver problem. I just cannot enable visual effects (I get the "Desktop effects could not be enabled" error message)
I have the nvidia-glx-legacy driver installed, as I have an older TNT2 card (hence I no longer have the nvidia-glx driver installed - already tried that). I also tried the whole xserver-xgl thing, but that crashed my Ubuntu, and I needed to use the Failsafe session to get back to 'normal'. I even tried updating the /etc/X11/xorg.conf file, and ended up reseting my keyboard layout. Man, did I have a hard time finding the forward slash to get my german keyboard working again! :)
Thanks for the suggestions, any more?

I think we are travelling in the same boat (seems I am having the very same system as yours and so the same problems as yours)..I tried a lot but cannot turn on Desktop effects..
Did you check my thread where a fellow ubuntuer helped me a lot (although I could not solve it)

---

### Post by IndianaThreepwood on 2007-12-30
Thanks, I did have a look at the other thread, but only went round in circles. I  installed ENVY, and that installed a bunch of drivers, but same result.
Funny thing is, my direct rendering is working like a charm (code: "glxinfo | head") and "glxgears" runs smoothly at around 250 FPS (this is a 32MB TNT2 card after all!)
Oh well, no visual effects for me then. Come to think about it, I'm probably better off with them disabled, with such an old computer! :)

---

### Post by abicash on 2007-12-30
I m having the same thing and happy with a gtk theme which looks somewhat like vista.And that is it for me now.Better off with this than spending energy on compiz unless someone has a sure shot answer/solution to it

---

### Post by diafygi on 2008-01-01
I am having the same problem as you, and it seems to be narrowed to the installation of xserver-xgl. You shouldn't need XGL for 2D stuff. If you want Compiz-fusion, look on Free Software Magazine's [chart]("http://www.freesoftwaremagazine.com/blogs/bored_with_3d_desktops") for what you need to enable 3d effects for your video card. It says my video card (Nvidia GeForce2 Ultra) should work with XGL, but I can't seem to get XGL to work. So if you have found a solution for this problem that doesn't involve uninstalling XGL, please post it.

[This]("http://ubuntuforums.org/showthread.php?p=4053221#post4053221") is where I'll be posting any solutions I find.

---

