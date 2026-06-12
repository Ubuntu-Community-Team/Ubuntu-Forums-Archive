---
title: "minimalist point of view"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Dr. Cox on 2006-08-07
hi there,

here is what i would like to do with ubuntu..... and actually any help is appreciated!

i like ubuntu, its hardware support, its somewhat working plug and play options, its great community which offers three different scripts to get multimedia support working.

but here is the clue.  i don't like xfce4 too much.... or at least not the "xubuntu-desktop"; gnome is fine. i hate kde.

anyhow, even gnome comes with too many apps, that only kill perfomance;

what i would like to do is the most minimalistic install possible, that still recognizes my acer travelmate hardware. then somehow get fluxbox to work, install gaim, vlc, xmms, evolution (or something quicker but similar), openoffice; i unfortunately need vmware. vlc. that should be it then. nothing vmware. maybe something skype like in the future. gnomebaker(is it as good as kde so far?) some olympus raw file image editing tool. something to sync my palm.  and a mindmapping tool.

that's about it. don't laugh, but i feel, that this is basic and any distro out there tries to give me much much much more than that?!

any ideas?

---

### Post by catlett on 2006-08-07
Just a quick "point you in a direction" comment. All the Ubuntu variations start with the server install. Then one of the "meta-packages" are installed i.e. ubuntu-desktop, kubuntu-desktop etc
These are large packages of software. As you have noted alot of times it is stuff you don't need or stuff that affects performance.
What I would recommend is installing the Server edition. This does not come with a gui i.e. gnome, kde etc. You will just have a text based login in and a command line. But you will have access to apt-get.
Once you have the server install you can apt-get only the packages you need. You should research now what you want and check if it is in the repositories, then apt-get what you want after the server install.

---

### Post by Dr. Cox on 2006-08-07
ok, i have actually tried that; when i installed ion2 / fluxbox... it wanted xorg, or something; with debian it is x-window-system (the package)... what's the packages name in the ubuntu repos? 

before you ask: i have install xserver-xorg and similar, but it still won't wokr afterwards....... what do i need to get a simple fluxbox running? do you have a step by step guide for dummies?

thanks a lot

---

### Post by orb9220 on 2006-08-07
There is a ubuntu with fluxbox I think its called nUbuntu. Just starting and small community. Just google for link.

I think there is an iso to download.

---

### Post by Upochapo on 2006-08-07
I think that there is an unofficial ubuntu-lite out there.  I will look for the link and edit this post.  Don't know what's all in it but it's worth looking into.

lol, well, whadya know... the link is [http://www.ubuntulite.org]("http://www.ubuntulite.org")

hmmm...just read a little into ubuntulite and it seems that it uses icewm as the desktop and not fluxbox.  don't know if that is a viable alternative.  I heard that icewm is light weight and fast.

---

### Post by zxee on 2006-08-07
The fluxbuntu site is here: [http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by Upochapo on 2006-08-07
omg...that's too much :D .  all these different flavors of ubuntu.  I thought I tried them all.  has anyone tried fluxbuntu, nbuntu, or ubuntulite?  Was just curious as to how well they performed and what not.  Like doc, i wasn't too crazy about the xubuntu and settled on gnome, don't like kde either (great environment just not my personal preference).  I'm thinking about trying a lighter weight version of ubuntu too just to make my old pc feel so uber powerful.

---

### Post by Dr. Cox on 2006-08-08
wow. as always, i am thrilled about the communities quickness. thanks' foralle the different suggestions. i'll try them out.

but for my other question: how would i install an x environment from scratch? what packages do i need?

---

### Post by zxee on 2006-08-08
> **Dr. Cox said:**
> wow. as always, i am thrilled about the communities quickness. thanks' foralle the different suggestions. i'll try them out.

but for my other question: how would i install an x environment from scratch? what packages do i need?

Looking at your previous posts-apologizes for the divergence from your question-it seems like you already have. 1st thing I would check is the default runlevel in /etc/inittab, and then there are special hiiden files that can control which windowmanger starts too. I'm not sure how much that applies to ubuntu but look or list your files starting with ~
> ls ~*
And if you actually need to install the xserver then appt-get install xorg should bring it on board. Hope that helps.

---

### Post by catlett on 2006-08-08
If you ran the install, then you should only need to apt-get 2 packages to get x going. Everything else should install as a dependency.
They are xserver-xorg-core. This is synaptics description

> X.Org X server -- core server
The X.Org X server is an X server for several architectures and operating
systems, which is derived from the XFree86 4.x series of X servers.

The X.Org server supports most modern graphics hardware from most vendors,
and supersedes all XFree86 X servers.

More information about X.Org can be found at:
<URL:http://xorg.freedesktop.org>
<URL:http://lists.freedesktop.org/mailman/listinfo/xorg>

This module can be found as the module 'xserver/xorg' at
:pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg

And xserver-xorg
> the X.Org X server
This package depends on the full suite of the server and drivers for the
X.Org X server, as well as providing a configuration infrastructure to manage
xorg.conf.  It does not provide the actual server itself, but removing it
is strongly discouraged.


Just a note, I do not know the exact way the dependencies will be handled. The mete-package "ubuntu-desktop" brings everythimgh together and installs it. So I do not know if xserver-xorg is enough. For instance x-window-system-core is installed as well on my system
> 
X Window System core components
This metapackage provides the essential components for a standalone
workstation running the X Window System.  It provides the X libraries, an X
server, a set of fonts, and a group of basic X clients and utilities.

Higher level metapackages, such as those for desktop environments, can
depend on this package and simplify their dependencies.

It should be noted that a package providing x-window-manager and a package
providing x-terminal-emulator should also be installed to ensure a
comfortable X experience.

The x termulator listed in synaptic you would probably want  is xterm (the gnome terminal is installed with ubuntu but you don't want gnome
```
X terminal emulator
xterm is a terminal emulator for the X Window System.  It provides DEC VT102
and Tektronix 4014 compatible terminals for programs that cannot use the
window system directly.  This version implements ISO/ANSI colors and most of
the control sequences used by DEC VT220 terminals.

This package provides four commands: xterm, which is the traditional
terminal emulator; uxterm, which is a wrapper around xterm that is
intelligent about locale settings (especially those which use the UTF-8
character encoding), but which requires the luit program from the xutils
package; koi8rxterm, a wrapper similar to uxterm for locales that use the
KOI8-R character set; and lxterm, a simple wrapper that chooses which of the
previous commands to execute based on the user's locale settings.

A complete list of control sequences supported by the X terminal emulator
is provided in /usr/share/doc/xterm.

The xterm program uses bitmap images provided by the xlibs-data package.

Those interested in using koi8rxterm will likely want to install the
xfonts-cyrillic package as well.
```

After x you need a display manager and a window manager. There are a few display managers in the repos xdm,kdm,gdm,sdm (the others sdm,wdm etc are security based)

Then of course the window manager/desktop. The repos will have gnome, kde, xfce, icewm and fluxbox.

If I was you, I would browse synaptic for packages you want. Then I would try them now before you delete this ubuntu and start your knew install.
Once you know everything will install, keep the names of the packages somewhere. So when you login to the server installation you will know what to apt-get. 
Just make sure that you know what repositories you need. You may have to edit your repository list after install. I know vi is available with the server but that can be a pain. Try to find out if nano comes with the server install, it is easier to work than vi (at least to me)

I only did this once and it was with debian. You may want to search debian's wki because I found the commands over there before. I remember installing 2 x packages, gdm and gnome. You want to refine a little more so I would search around and experiment. When you know what you want and you know that it works on ubuntu, go for it.

---

### Post by meborc on 2006-09-04
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

there is some advice on the wiki as well... i'm going to try to build my own ubuntu from the server install today... wish me luck :)

---

