---
title: "fglrx 8.42.3 How To (64bit)"
date: 2007-10-25
forum: Apple Intel Users
---

### Post by cyberdork33 on 2007-10-25
Ok, since ATI&#8217;s new drivers have a lot of weird things preventing install on Gutsy in 64 bit, I am posting this here as help for those that want to try it out.
 P.S. Compiz works without XGL!

**[COLOR=Red]WARNING: THIS IS NOT RECOMMENDED UNLESS YOU KNOW WHAT YOU ARE DOING![/COLOR]**

[http://www.rickycampbell.com/2007/10/24/fglrx-8423-in-64bit-gutsy/](http://www.rickycampbell.com/2007/10/24/fglrx-8423-in-64bit-gutsy/)

---

### Post by two00lbwaster on 2007-11-03
Now I need a way to get Linux working again, after I've lost graphical output following the linked article.  Any chance of an  article to reverse this, that I can do from the console.

Currently Gutsy gets to loading the login screen and then my monitor shows loss of connection.  So to get it back I'm thinking that the recovery console is the only way.

---

### Post by two00lbwaster on 2007-11-03
Thanks to the backup procedures in the script booting into the live distro you can undisable the fglrx module and rename your xorg.conf.original-0 to xorg.conf.  I now have graphical desktop back but obviously not ATI's latest drivers :(

---

### Post by cyberdork33 on 2007-11-03
> **two00lbwaster said:**
> Thanks to the backup procedures in the script booting into the live distro you can undisable the fglrx module and rename your xorg.conf.original-0 to xorg.conf.  I now have graphical desktop back but obviously not ATI's latest drivers :(

it doesn't offer much improvement right now anyway other than not needing XGL for compositing.

---

### Post by two00lbwaster on 2007-11-03
Cheers for the answer cd33.

I found that I was suffering from the restricted drivers boot bug.  I have them loaded but no splash as this is where it falls down

---

### Post by cyberdork33 on 2007-11-04
> **two00lbwaster said:**
> I found that I was suffering from the restricted drivers boot bug. 

I don't really know what this is.

---

### Post by two00lbwaster on 2007-11-08
essentially you have to add one of the vga=XXX line to the /boot/grub/menu.lst kernal line to get a boot screen and functioning monitor display.

---

### Post by md_lasalle on 2007-11-10
Hello all, I've been experiencing with this new fglrx driver aswell(not 64bit tho), here's a quick description of what I did and what problem I'm running into


```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.43.2-x86_64.run
sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
chmod +x ati-driver-installer-8.42.3-x86_64.run
./ati-driver-installer-8.42.3-x86_64.run --buildpkg Ubuntu/edgy
sudo dpkg -i xorg-driver-fglrx_8.42.3-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb
sudo dpkg -i fglrx-amdcccle_8.42.3-1_i386.deb
sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

That built the distro specific for my Edgy on my mac book pro with the X1600 PCIe

after a reboot, fglrxinfo outputs :

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6958 Release
```

So I *think* everything went fine. glxgears seems to run smoothly, but best of all, VSync finally works for ATI card!

My problem is this. I'm currently developing a game using SDL/OpenGL for rendering. Before the driver update, asking the linker to link against -lGL would link to /usr/lib/libGL.so.1  ... but now, it links to /usr/lib/libGL.so.1.2, so now some people with only libGL.so.1 need to create a symlink just for this, which is quite annoying.

Another thing, things that worked in my game (simple rnedering of certain object) doesn't work anymore, the same behaviour can be seen when i try the game on another computer i have with a geforce fx5600 ultra, which used to run perfectly.

My guess is that there are bugs in the libGL.so.1.2 that comes with the new fglrx drivers. Is there anyway I could get the libGL.so.1 that I had with 8.27.10 ?

Thanks for any help on this. I don't wanna start trying to fix my code to display some GL_QUADS that used to work before if the problem lies elswhere.

---

