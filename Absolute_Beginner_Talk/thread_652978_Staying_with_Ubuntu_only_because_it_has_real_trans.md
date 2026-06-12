---
title: "Staying with Ubuntu only because it has real transparent terminal windows"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by sunv on 2007-12-29
Hi
Ive been using ubuntu for about a week and i like it, but somethings bother me about it.  LIke it doesn't load fast enough, its bloated ...

I tried openbox and its fast as f**k and i would really like to use arch linux or ubuntu with openbox, making my system blazing fast.  however I noticed i couldn't get those real transparent windows that are in ubuntu, in openbox.  also the game urbanterror ran alot slower (<20 fps) in openbox vs ubuntu (>40 fps).  In addition im not sure if there is support for my wireless card using openbox.  It seems like openbox is too much of a hassle for me to dig thru to set up my system.

Is there a way i can have the minimalism, simpleness, and speed of openbox combined with the moderness, somewhat fancy graphics and great hardware recognition of ubuntu?

someone please help me out. :KS

---

### Post by Hallvor on 2007-12-29
Barebones installation + XFCE?

---

### Post by sunv on 2007-12-29
What do you mean by barebones?  where can i find this barebones distro?

and XFCE will have good hardware recognition?  like i wont have to dig through forums to find a script i need for my wireless card?

i tried XFCE, the terminal windows weren't totally transparent,  i could see the background but not the windows behind it.

---

### Post by Steveway on 2007-12-29
You need to enable a compositing-manager for the true transparent-terminals.
Like Compiz-fusion or the one integrated into XFWM4.

---

### Post by gazj on 2007-12-29
fluxbox is much better at handling true transparency than openbox.  You will also need xcompmgr for transparency.

```
sudo apt-get install fluxbox xcompmgr
```

some how to information[ here]("http://fluxbox.sourceforge.net/docs/en/faq.php")


If you want a minimuim bare bones start of ubuntu download ther server version, there will be no desktop at all, you will need to add it.

Or a distro which is designed to be bare bones from the ground up (exactly right for the lightweight custom user config) is [Archlinux]("http://www.archlinux.org").  If you choose this route please please print the handbook before you start or you WILL get stuck, it is [here]("http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide"), and post installation [here]("http://wiki.archlinux.org/index.php/Post_Installation_Tips")

I know its bad for ubuntu to post another distro as an alternative, but it's a viable very lightweight solution.  If you do decide on the Arch path, IM me if you get really stuck.

---

### Post by urukrama on 2007-12-29
Have a look at my guide (link in my signature) to help you set up Openbox. You can have true transparency and compositing (shadows, fading menus, etc) in Openbox using xcompmgr and transset. It is discussed in the above mentioned guide.

A barebones install is a command line install. You'll need the alternative install CD for this. Select 'Install a command line install' at the boot screen. You will then have only a command line, with no graphical interface. You can then add the desktop environment and/or window manager of your choice. See [here]("http://psychocats.net/ubuntu/minimal") for more details.

If you find Openbox too bare, Xfce is alternative. It is lighter than gnome, but more feature rich than Openbox or Fluxbox. I suggest installing the package 'xfce4' rather than 'xubuntu-desktop' as I find it faster.

EDIT: regarding your wireless card, I'm not entirely sure as I don't have wireless internet or the hardware to support it, but if you load the network manager or whatever it is called from gnome in Openbox, you should be able to configure and use your wireless like in Gnome. Just find out the exact command of the network manager and add it to your autostart file (in ~/.config/openbox/) to have it load whenever you start Openbox.

---

### Post by solemnavalanche on 2008-01-01
> **sunv said:**
> and XFCE will have good hardware recognition?  like i wont have to dig through forums to find a script i need for my wireless card?

i tried XFCE, the terminal windows weren't totally transparent,  i could see the background but not the windows behind it.

XFCE is just a window manager + a desktop environment, not an operating system. As such, it doesn't have anything to do with hardware recognition. That will depend on the underlying OS distribution you use, and Ubuntu is the best for automatic hardware recognition, as far as I can tell. 

That doesn't mean you can't use XFCE with ubuntu. I've never tried it, but I gather that XUBUNTU is a version of Ubuntu that uses XFCE instead of GNOME, the wm + desktop that vanilla Ubuntu uses. 

I normally use XFCE, and it _definitely does_ true transparency, as in, you can see other windows through the terminal, not just the desktop. Try installing XUBUNTU; I bet it will work right out of the box, or if not, there's almost certainly a way to turn it on with just a little bit of searching. (On My Machine, it's Settings Manager->Window Manager Tweaks->Compositor->Enable Display Compositing.) 

Another option for you might be the enlightenment window manager. It doesn't provide a desktop environment (so no icons on the desktop, and no built-in file browser), but it's even leaner than XFCE, and provides true transparency. It's probably harder to set up though.

Openbox is pretty awesome, but even with xcompmgr and transset, it still doesn't do transparency the way you probably want -- i.e. transparent background but opaque text. I could be mistaken, but I don't think that's possible with Openbox. When I tried Openbox, the text was as transparent as the rest of the terminal window, making it difficult to read. With XFCE or Enlightenment + the XFCE terminal program (inventively named "Terminal"), you get transparent background _and_ 100% visible text.

Edit: Actually, I just went back and tried uxrvt and found that it does transparency + opaque text with openbox. Nice! Now I get to switch back. Just install and run xcompmgr, and then run the command that appears in this image: [http://icculus.org/openbox/index.php/Image:TrueTransparentWindows.png](http://icculus.org/openbox/index.php/Image:TrueTransparentWindows.png) 

Sorry for the long-winded and partially wrong response!

---

### Post by JoshuaRL on 2008-01-01
Try this if you have ubuntu and want to try XFCE:

```

sudo aptitude xubuntu-desktop

```

That's what I did to get XFCE on mine.  And now that's almost all I use because it's so fast.  It's a metapackage, so it will automatically download all you need to get XFCE working as the desktop on the Ubuntu base OS.  So all the Xserver settings and programs will be the same.  If you make sure you go to Applications>Settings>Desktop and go to the Advanced Tab you can choose to launch both Gnome and KDE services at launch so those programs that need it will run well.

I enabled compositing and got a launch bar from gDesklets.  Now my laptop looks like the offspring of OSX and Vista on steroids.  Sweetness.  I love XFCE!

---

