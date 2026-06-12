---
title: "Setting up separate X sessions on dual screens"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by swedishlf on 2007-06-03
Hey guys, running Feisty here on an NVidia card with 2 monitors hooked up to it.  I'm not a big fan of the way the NVidia drivers span the desktop across both monitors, so I was wondering if it is possible to start a second X session (using gnome) on my other monitor.

I'm not concerned about dragging windows between the two, I'd just like to be able do something like watch video on one while working on the other.

My questions:
How do I run a second X session on a second monitor?
How do I switch between the two?
Will I be able to get sound from both simultaneously?
Can the two sessions have different resolutions? Backgrounds? Window Managers?

Answers to any of these would be fantastic.

Thanks!

---

### Post by Happy_Man on 2007-06-03
Twinview or Xinerama. They both allow for dual-screen setups.

---

### Post by swedishlf on 2007-06-03
I've tried twinview but I don't really want the "two monitors behaving as one big display" thing, I'd rather have two separate gnome sessions running.

---

### Post by annda on 2007-06-03
there is an option in nvidia-settings to configure both monitors as separate displays.

and to the best of my knowledge you can't have two X sessions at the same time.

---

### Post by txcrackers on 2007-06-03
> **swedishlf said:**
> 
How do I run a second X session on a second monitor?
How do I switch between the two?
Will I be able to get sound from both simultaneously?
Can the two sessions have different resolutions? Backgrounds? Window Managers?

If your video card is dual-head, then you want what I have. Note that I have not actully done this with Gnome, but, since it works just fine with KDE, I don't think there will be any problems.

Make sure in xorg.conf that you have two Screen sections, two Monitor sections, and two Device sections. Make sure that the **BusID** for both Device sections is the same. Do *not* use any MetaModes, TwinView, etc.

My sample ServerLayout section:
```
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
```

What this does is provide X with two "independent" outputs that share the same input devices (keyboard, mouse).

When you restart X, GDM/KDM will appear on Screen0. Once you log in, you'll have **two** independent window managers running (but only one X). On KDE, each will have their own desktops, panels, etc. The only desktop-related item that gets "shared" is the screen saver.

The mouse will move freely between the two, but no dragging windows between them.

---

### Post by swedishlf on 2007-06-03
Thanks TXCrackers,

I have edited the xorg.conf file to include two device, monitor, and screen sections I've also made adjustments to the "ServerLayout" section.  I have a monitor section for each "Monitor0" and "Monitor1."  Screen section for each "Screen0" and "Screen1."  But I am unclear, my Device section does not have a BusID entry, should I have one each for "Videocard0" and "Videocard1?"  I have tried both and neither seem to be working. In both cases I get no output on my 2nd monitor.

Your setup sounds exactly like what I'm wanting, thanks for the continued assistance!

---

### Post by Opz on 2007-06-16
Don't know if you got it working for you already, but maybe this could be of help.
I think i have the same setup that you want, two independent monitors. Perhaps like me, using independent resolutions and refresh rates as well.

I've just started to use Ubuntu and this is what i did: [[COLOR="Blue"]Check here how i changed my xorg.conf file[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2857569&postcount=45")

Although my graphics card is an Matrox P650, you can get a good idea what needs to be changed. Also, type the following in the terminal: 
```
man xorg.conf
```
This gives you a manual describing the functions you can input/change in xorg.conf

This could be of help, it has a nvidia section: [HOWTO Dual Monitors: Setting up Two Graphics Cards]("http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_Two_Graphics_Cards")

In the terminal type the following to determine you bus id for your graphics card.
```
lspci
```
Add that bus id in the appropriate place in xorg.conf

I also got a lot of info coming from a support readme document coming from the manufacturars website, Matrox in my case. It described pretty nicely what options there are and what is essential to change.
Since you don't have a Matrox card, the file i'm linking to below might not be of that much help, but again this gives you an idea what kind of information you have to find for your particular graphics card.
[[COLOR="Blue"]How to modify xorg.conf for Matrox P650 and multiple displays[/COLOR]]("ftp://ftp.matrox.com/pub/mga/archive/linux/2006/readme-1.4.4.txt")

Like someone else posted, i think it's one X session, just divided over two independent desktops. The panels are duplicated but behave separately, atleast on my system.

Good Luck

---

