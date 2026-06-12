---
title: "Install Nvidia graphics card"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by lostinub on 2007-04-24
Hi 
I am trying to install a grapics card for the first time. If i put the card in the comp, Ubuntu loads untill I get to the point where the login should appear, then the screen goes blank. Should I install drivers before I put the card in?
Do I need to do something on boot up?
Card isFX5200
Cheers.

---

### Post by Fidelio on 2007-04-24
I'm a bit new to this myself, but I had the same problem. I changed the graphics driver to vesa by editting the xorg.conf file which let me boot with the new card, then I installed the nvidia drivers. There may be an easier way than this, but that's how I did it. Be sure to back up your xorg.conf before you edit it.

---

### Post by markitect on 2007-04-24
when it hist the blank screen hold down ctrl + alt and jab some any of f2 though f6 until it comes up with a prompt.

log on with your usual user and password

type in apt-cache search nvidia
what it displays will depend on which version your using, but you should see something saying display driver then type

sudo apt-get install display-driver-name 

then ctrl+alt+f7 should give you your blank screen back and do a crtl+alt+bksp

---

### Post by bongobonga on 2007-04-24
NVIDIA drivers are not automatically installed in the kernel, you will have to install them youself; this is because of licence problems.

The hard way to do this is to go to the nvidia website and manually install the drivers. But there is a ubuntu package called 'envy' which you can download which is much better and is much easier.
 From a command line do a 
```

apt-get install envy 

```

then just run the command envy at a terminal command line. This package 'envy' is just brilliant. It goes to the nvidia website and automatically downloads any drivers that you need and then configures xorg to work with the new drivers. 
If you have any problems, just do a search for envy on this site and you will find a rather complete instruction set for the package.

---

### Post by lostinub on 2007-04-24
Thanks for the pointers. I got it sorted by runining envy in text mode fron the recovery startup. All lovely with wobbly bits.

Cheers Peeps.

---

