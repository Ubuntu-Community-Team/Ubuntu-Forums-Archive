---
title: "Is it possible to have full screen magnification in Orca + gnome-mag right now?"
date: 2007-07-06
forum: Assistive Technology &amp; Accessibility
---

### Post by Declan Moriarty on 2007-07-06
Is it possible to have full screen magnification in Feisty Ubuntu 7.04 and gnome 2.18.1?  Having tried it I get a white screen with the cross hairs appearing.  Putting 0.0 in the source display and 0.0 in the target display produces a screen where you can move the cursor, but it is magnifiying itself! As if it is magnifying the magnified screen in some sort of feedback.  In another post there was an instruction page on getting Gnopernicus to do it.  The setup looked almost identical to orca.  The instructions involved putting a dummy screen in the xorg.conf file.  Is this necessary with orca?  Does it work?

How do you check if composite is running/start it?

I have managed to get Beryl running but I haven't managed to get it to run on start up.  Putting beryl & command in the .cshrc should solve this?

Also what is the Super Key in Beryl when specifying a mouse shortcut.  I can't put a modifier key into a keyboard shortcut in Beryl.  All I can do is have a letter as the shortcut key!  This means that when the letter is typed in the normal way it switches off and on zoom - not what you want with a shortcut!

Note that I have installed Ubuntu on to a USB hard drive.

I look forward to hearing from you.

Where has the Accessibility info gone in the Wiki - This seems to have been revamped and there is a general page on the features but not detail?  It appeared to be far better under Dapper.
___________
Declan Moriarty.

---

### Post by cerdiogenes on 2007-07-09
> **Declan Moriarty said:**
> Is it possible to have full screen magnification in Feisty Ubuntu 7.04 and gnome 2.18.1?  Having tried it I get a white screen with the cross hairs appearing.  Putting 0.0 in the source display and 0.0 in the target display produces a screen where you can move the cursor, but it is magnifiying itself! As if it is magnifying the magnified screen in some sort of feedback.  In another post there was an instruction page on getting Gnopernicus to do it.  The setup looked almost identical to orca.  The instructions involved putting a dummy screen in the xorg.conf file.  Is this necessary with orca?  Does it work?

The lastest stable version of [gnome-mag]("http://ftp.gnome.org/pub/GNOME/sources/gnome-mag/0.14/gnome-mag-0.14.4.tar.gz")  correct some problems with the composite support, so you can have full-screen magnification without any modification in source/target display or dummy drivers.

> **Declan Moriarty said:**
> How do you check if composite is running/start it?

Open a terminal and type xdpyinfo. In the end of the first page you will see something like this:

number of extensions:    30
    BIG-REQUESTS
    Composite

and much more extensions. All these extensions listed, are extensions that are active. Ubuntu 7.04 comes with Composite enabled by default.

> **Declan Moriarty said:**
> I have managed to get Beryl running but I haven't managed to get it to run on start up.  Putting beryl & command in the .cshrc should solve this?

Probably yes, but I think that a better way is to launch it is to create a launch in System -> Preferences -> Sessions

> **Declan Moriarty said:**
> Also what is the Super Key in Beryl when specifying a mouse shortcut.  I can't put a modifier key into a keyboard shortcut in Beryl.  All I can do is have a letter as the shortcut key!  This means that when the letter is typed in the normal way it switches off and on zoom - not what you want with a shortcut!

In my computer is the key that have the Windows logo.

Note that I have installed Ubuntu on to a USB hard drive.

I look forward to hearing from you.

Where has the Accessibility info gone in the Wiki - This seems to have been revamped and there is a general page on the features but not detail?  It appeared to be far better under Dapper.
___________
Declan Moriarty.

Best regards,
Carlosl

---

### Post by Declan Moriarty on 2007-07-13
How do you get full screen magnification working in Orca?  When I do it, all I get is a white screen.  Also Beryl has stopped working.  I have uninstalled and re-installed it but to no avail.  I have the Emerald Themes installed but I can't get any of them to work.  I have managed to Beryl to accept a modifier key using the "Grab Key" function, but still no zoom.

Thank you very much in advance.
---
Declan Moriarty.

---

### Post by cerdiogenes on 2007-07-13
To get full-screen magnification working with Orca, download the lastest stable gnome-mag (the link in my last post) and unpack it in some folder.

In a terminal go to the folder where the tarball was unpacked and type:

$: ./configure --prefix=/usr
$: make
$: sudo make install

PS.: This will overwrite the magnifier that comes with Ubuntu. If later you want this magnifier again just reinstall the gnome-mag package throw synaptic or anyother package manager that you like. Do it at your own risk, since this is not the recommended way to install software in Ubuntu.

After this, just init orca and you will have full-screen magnification working.

PS2.: Make sure that you are not running any Window Composite Manager (Compiz/Beryl) or the magnifier will not work properly.

Best regards,
Carlos.

---

### Post by Declan Moriarty on 2007-07-15
I think I will install Gnopernicus and do it that way.  I can't compile gnome-mag.  It wants some packages that I cant install using Synaptic.  The list is:-

 ```
       libloginhelper-1.0      >= 1.5.2
        libbonobo-2.0           >= 1.107.0
        ORBit-2.0               >= 2.3.100
        glib-2.0                >= 2.11.1
        gtk+-2.0                >= 2.1.0
        gdk-pixbuf-2.0          >= 2.1.0
        gdk-pixbuf-xlib-2.0     >= 2.1.0
) were not met:

No package 'libloginhelper-1.0' found
No package 'gtk+-2.0' found
No package 'gdk-pixbuf-2.0' found
No package 'gdk-pixbuf-xlib-2.0' found


```

Are there normally packages like this that are not available when you try to compile an open source program?  I did check, Ubuntu does come with gcc and cc and make programs.  Will Gnome-mag 0.1.4.4 be available in Gutsy?

Again thank you very much for your help.  I will try to install Gnopeernicus and hope it works.  Otherwise I may have to live this USB drive on the shelf and wait for Gutsy.  If the Gutsy Live CD has half screen magnification by default, and full screen magnification doesn't work I will have to go into Windows and get Windows Disk Manager to recogines the USB drive and format an NTFS partition for the entire disk that has full screen magnification through Dolphin software I am using on Windows XP right now.

I hope I don't have to use the final option.

---

### Post by cerdiogenes on 2007-07-15
Hi Declan,

I forgot to say that you have to install some development packages to compile gnome-mag. These are:

* xorg-dev
* libatspi-dev
* libgtk2.0-dev

Also install all the dependencies.

I think that with these you can compile gnome-mag without problems, but if you still have some problem, post it here.

Best regards,
Carlos.

---

