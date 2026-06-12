---
title: "Confused: X.org, gdm, metacity, GNOME...? What is what for?"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by mpat on 2005-10-21
Hi everybody,

I've been using Linux on servers for about 7 years now (moving thru SuSE, RedHat, Fedora, Gentoo, Debian and finally ubuntu), and for a year I (almost) completely said good bye to Windows - except for Photoshop and InDesign... So I'd say I know quite a lot about Linux.

But a moment ago I've read something about "metacity". I have heard about it before, looking into my session settings in GNOME. Looking up in Synaptic it says metacity is a "window manager". Now I'm a bit confused, that's why I find myself back in the "Absolute Beginners" forum:

What's this all about? - Please correct me if I got this wrong:

X11/X.org is for the graphics mode itself, the client/server architecture of showing something somewhere on a graphical screen, the handling of attachted devices such as monitor, keyboard, mouse, tablet and graphics card and interacting their input/output... right?

xdm/gdm/kdm is for the login procedure, starting X, showing a nice (maybe themed?) login screen and actually starting the window manager, the user wants to use, after a successful login... right?

Now that's what metacity confuses me - I THOUGHT:

...then xdm/gdm/kdm starts KDE or GNOME or whatever, which is actually called the "window manager", usually including some panels, menues and a "desktop" and a file manager. So the "window manager" is for making you pc controlable, being able to maintain your files (file manager), creating folders in a user-friendly way, starting applications by clicking on icons - well, a graphical user interface. This "window manager" is based on a widget library it uses, for example GTK/GTK2 in GNOME...

GTK/GTK2 for instance, can be "skinned" as well by choosing how the controls (buttons, lists, sliders, scrollbars) should look like. The window manager themes can only control the appearance of "windows" - their "borders"...

BUT: What's metacity? What does it do? Where does it fit inbetween. Or do I have a completely wrong imagination of how this beautiful little icons on my screen come to my appearance...?

Please help me out! I hate getting in touch with things which I do not know how they work... It's sometimes hard enough with my girlfriend...;) 

Thanks a lot!

---

### Post by Kyral on 2005-10-21
You have X and the *DMs right.

Now a "Window Manager" (WM) is something that controls how windows are laid out. Metacity is one. (You notice if you go to Gnome-look.org that there is a section for Metacity themes)  Now GNOME doesn't provide its own WM like KDE does, so it needs a Window Manager. GNOME, KDE, and XFCE are considered "Desktop Enviroments", meaning that they provide the whole shabang. Menus, panels, etc. (KDE stands for K Desktop Environment). Now some people run only WMs for a desktop, which is perfectly fine and very cool sometimes. Enlightenment 17 for example kicks the socks offa Metacity. Now I told you that GNOME doesn't provide a Window Manager. Thats why it comes with Metacity by default, and yes you can replace it. One of the more popular tweaks to GNOME on this Forum is to do that, by replacing Metacity with either Openbox or Enlightenment (the latter being referred to as "Enlightenend GNOME")

I hope I cleared this up for you....

---

### Post by SilentCacophony on 2005-10-21
Hi. Just thought I'd post some more info on the subject. This may help in understanding the different components and options involved in setting up a desktop environment.

**Kyral** mentioned a couple of popular window manager replacements for metacity. Here are links to threads which describe the process:

Openbox: [http://ubuntuforums.org/showthread.php?t=75471](http://ubuntuforums.org/showthread.php?t=75471)
Enlightenment: [http://www.ubuntuforums.org/showthread.php?t=54476](http://www.ubuntuforums.org/showthread.php?t=54476)

As he also mentioned, some people opt for using a 'lighter' setup, without all of the 'Desktop Environment' overhead, by using just a window manager. I use such a setup by doing a 'server' (minimal) install, and then installing only those packages that I want, including my preferred WM, openbox. Here is a link describing that type of process:

[https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

There is also a work-in-progress Ubuntu varient call Xubuntu, which uses XFCE4 as a DE, and applications more suited to that environment. Here are a couple of links about the xubuntu-desktop:

[http://ubuntuforums.org/showthread.php?t=75971](http://ubuntuforums.org/showthread.php?t=75971)
[https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)

Any of these options will require varying amounts of additional tweaking and editing that you won't normally do using gnome, so they are not for everyone.

---

### Post by mpat on 2005-10-22
Thanks a lot for the information. I've had a look at "Enlightened Gnome", but I guess I'll stay with Metacity, I like the "clear look" of "clearlooks". ;-)

---

### Post by Lars A E on 2005-10-22
[QUOTE=mpat]Thanks a lot for the information. I've had a look at "Enlightened Gnome", but I guess I'll stay with Metacity, I like the "clear look" of "clearlooks". ;-)[/QUOTE]

I agree with you on this one. I use metacity when using gnome because I feel this gives me the most consistant look/behaviour on my desktop.
I quite like the openbox desktop for it's speed, but only when run totally on it's own...

I sometimes get this urge to totally change my desktop and switch to enlightenment, xfce or openbox, but somehow I always return to gnome...

---

