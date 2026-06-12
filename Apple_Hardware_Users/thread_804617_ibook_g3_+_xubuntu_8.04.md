---
title: "ibook g3 + xubuntu 8.04"
date: 2008-05-23
forum: Apple Hardware Users
---

### Post by blampars on 2008-05-23
I have recently acquired an little ibook dual usb 500mhz with 128ram running os x panther (10.3 i think?)

it works well for web browsing one page at a time, but with so little memory there's not much multi-tasking going on. I want to put xubuntu 8.04 on here to try to add a little more functionality to my new little toy. :)

i've downloaded the ubuntu server ppc iso and burnt it to cd with intentions on downloading the xubuntu-desktop afterwards. is there anything in particular that i should look out for while installing, or should everything go pretty smoothly for me?

i dont have os x install disks and i want to completely wipe the drive and run xubuntu only. my only concern is that the installation screws up and i'm left with a non working machine for a while, thats why i'm asking. ;)

-b

---

### Post by oswaldkelso on 2008-05-23
if you have a spare firewire hd you can clone your osx install to it for safe keeping

[http://forums.debian.net/viewtopic.p...&highlight=ccc](http://forums.debian.net/viewtopic.p...&highlight=ccc)
__________________

---

### Post by stream303 on 2008-05-23
> **blampars said:**
> i've downloaded the ubuntu server ppc iso and burnt it to cd with intentions on downloading the xubuntu-desktop afterwards. is there anything in particular that i should look out for while installing, or should everything go pretty smoothly for me?

There is a really good guide for doing just that, even though the preface talks about Intel:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

> i dont have os x install disks and i want to completely wipe the drive and run xubuntu only. my only concern is that the installation screws up and i'm left with a non working machine for a while, thats why i'm asking. ;)

Great - when it comes to guided partitioning, just choose the "use the whole disk" option.  That'll wipe the drive for sure, so if you have anything important on it, backup now!

There's always some risk, but the help from others here can mitigate that quite a bit.

While Xubuntu is a great choice, it is not a panacea for low memory when it comes to running resource-heavy apps like Firefox, Gimp, OpenOffice, etc.  It helps though.  The best bet is to look for lighter apps to provide much the same functionality along with Xubuntu.

For example, one might want to subtitute the Epiphany-Browser instead of Firefox (uses the same rendering engine - look specifically for epiphany-browser as there is a non related package just called epiphany.  Also look for epiphany-extensions if you want to run things like ad blocker's with the filterset-G filters, etc)  There are many alternative browsers.

When burning the install image, many would suggest using the "alternate" image, burn it as an iso instead of just copying it over, use a CD-R instead of a CDRW, and burn at a very low speed.

---

### Post by blampars on 2008-05-25
well i went through with the server install, and everything went as smooth as it could possibly go. Trying to get GUI set up proved to be alot more difficult, but after lots of google i was finally able to edit my xorg.config file and make things work properly.

so i poked around with a straight install of xfce4, icewm and openbox but ultimately decided I was going to install the xubuntu-desktop package and alter programs/settings from there.  building up still seems a little too daunting for me (only been using linux for 3 months now).

"sudo aptitude install xubuntu-desktop"

300mb download and an hour install process later I"m looking at a GNOME desktop.. :confused:

anyone know what gives?

[EDIT] I logged out of the gnome desktop back into WDM and had desktop options that I didnt have the first time. Aparantly installing xubuntu-desktop installs both the gnome desktop and the xfce desktop.  I'm running xfce now. I don't understand why gnome would be loaded as well, but at least I have the fully featured xfce to stip down to my liking. Building up xfce was just too much! ;)

---

### Post by stream303 on 2008-05-25
> **blampars said:**
> building up still seems a little too daunting for me (only been using linux for 3 months now).

You did great!  Some might claim that even xubuntu-desktop is a little heavy, and that just using XFCE4 with a couple of xfce4 applets is the way to go.  At least you know how to do a DIY install and that gives you many more options - great experience.

> but at least I have the fully featured xfce to stip down to my liking. Building up xfce was just too much! ;)

Yeah, seems like you are caught in the middle like I am sometimes - do I pare it down, or build it up? :)

If you'd like to make sure that you have a pure environment, be sure to see the following:

[http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce)

I had to use the "cut-n-paste" method.  Details are available for K/X/Ubuntu if you want to get to a pure state.  Nice.

---

### Post by deamon_knight on 2008-05-25
Blampars, when you logout, remember to select XFC from the sessions list before logging back in. I'm doing much the same thing you are, and while Xubuntu works, the PPC version is a bit rough around the edges. Good stability and everything works, but trying to add some desktop icons is a lot harder that I would have though.

---

### Post by blampars on 2008-05-26
deamon_knight, you are right about it being a little rough around the edges. espically with only the one mouse button on the mac. i've actually just taken my pc mouse and plugged it into the usb for right click functionality..

for kicks before i left my computer alone yesterday i loaded fluxbox on there and checked the memory usage.. fluxbox uses 48mb ram at startup versus xfce using about 74mb ram, so i'm thinking about playing with fluxbox now too..

i do have to say though that xfce [xubuntu] is still pretty light. i'm pretty impressed with how light the memory usage is compared to os x 10.3 that was on there

stream303, the main reason i decided to just get the xubuntu-desktop instead of building up xfce was the fact that its already got a network manager, and the "password manager" that pops up whenever you need to use something like synaptic which needs root access. i couldnt for the life of me figure out how to get that, and running synaptic or something else through the terminal just leaves me with another process running. meh. ;)

---

### Post by stream303 on 2008-05-26
> **blampars said:**
> 
stream303, the main reason i decided to just get the xubuntu-desktop instead of building up xfce was the fact that its already got a network manager, and the "password manager" that pops up whenever you need to use something like synaptic which needs root access. i couldnt for the life of me figure out how to get that, and running synaptic or something else through the terminal just leaves me with another process running. meh. ;)

No problem - it's just a front-end to sudo when that pops up before using synaptic.

You can do much the same in the commandline by prefacing it with sudo:

```
sudo apt-get update

sudo apt-get upgrade

sudo apt-get install htop
```

to update, upgrade, and install the htop utility for example to see what processes are running and which might be hogging the cpu.  The normal top works ok, but I really dig htop.

---

