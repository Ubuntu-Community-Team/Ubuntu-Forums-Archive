---
title: "can i setup kde on ubuntu and switch between gnome and kde?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by drsyntax on 2007-06-22
can i setup kde on ubuntu and switch between gnome and kde without losing any of my data ?

---

### Post by NeoLithium on 2007-06-22
You betcha!
To install KDE from Ubuntu, you can use ```
sudo aptitude install kubuntu-desktop
```  On the login screen, just click on Sessions, and select which one you like :)

---

### Post by Nuverde on 2007-06-22
'sudo apt-get install kubuntu-desktop'
The next time you log in, you can select KDE or Gnome as the 'Session'

---

### Post by Saoshyant on 2007-06-23
I am on Ubuntu Studio, which uses GNOME.  SInce I'm not keen to GNOME I have tried doing just this, but after restarting--due to also installing the Nvidia driver--I can't get X to start at all.  I still have access to a recovery shell, but I am not sure what file to restore/change/whatever to get X up again.  I'm also not sure if this was caused by installing the Kubuntu desktop on top of Ubuntu Studio, or because of the Nvidia driver, which I never got a problem with it on my older system.

I remember that during the kubuntu-desktop install, I was asked if I wanted to use GDM or KDM, and I chose KDM because I wanted to use KDE.  Maybe this is to blame?  What file to restore, then?

---

### Post by diatribe on 2007-06-23
kdm isnt necessary to use kde, also the file you want to edit is /etc/X11/xorg.conf

---

### Post by Saoshyant on 2007-06-23
> **diatribe said:**
> kdm isnt necessary to use kde, also the file you want to edit is /etc/X11/xorg.conf

Thank you.  I'll look into that file, although past experiences showed me that it's a large file, so I'll be unsure what to change there.  I hope there are comments.  Well, if nobody else has no more advice, I'll be switching to the resuce shell on my other box and try my luck.

---

### Post by phr0ze on 2007-06-23
Right above monitor section is a section called device where it defines your video card. Change driver to nv. Here is what you may want yours to look like. Please don't modify your identifier. Remove any options too.

```
Section "Device"
	Identifier	"nVidia Corporation NV43GL [Quadro FX 540]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection
```

---

### Post by Dennis the Menace on 2007-06-23
I found this article quite interesting when I wanted to try different desktops.
[http://tinyurl.com/2smt9g](http://tinyurl.com/2smt9g)

---

### Post by Saoshyant on 2007-06-23
I'm back on my own box now.  Seems like it wasn't a GDM/KDM issue.  I didn't know what to do to fix the xorg.conf, but I found on the top of the file (under a comment) a mention to a debian tool called dexconf, and I just ran that.  A diff showed me that the only it thing changed on the xorg.conf was that "nvidia" got replaced by "vesa", and now X works.  I blame the driver, then.

> **phr0ze said:**
> Right above monitor section is a section called device where it defines your video card. Change driver to nv.

Hey, thanks for this.  I'll be trying it since the resolution is terrible under vesa.

---

### Post by Saoshyant on 2007-06-23
Hmm, this is probably _not_ the thread to ask, but I just switched to GNOME to see if everything was OK there, and lo and behold, installing Kubuntu Desktop screwed up the awesome theme Ubuntu Studio used for GNOME.  Anyone got a backup of it?  Or know how to revert the changes?

I intend to stick mostly in KDE, and its theme is alright for me, but I really liked the GNOME theme's colors, which are now gone.

---

### Post by Gideon on 2007-07-06
The really annoying thing is that nobody's seen fit to release a full qt version of the Studio theme, which would severely rock.

Apparently you can get close by using assorted different decorations and settings, but like most things, it would be nice if we just had a single package that just worked.

---

### Post by borahshadow on 2007-07-06
I think to fix the studio theme you have to deselect a setting in the kde control panel about "use my kde theme in GTK applications " or something

---

### Post by CowzRule on 2007-07-06
> **Saoshyant said:**
> Hmm, this is probably _not_ the thread to ask, but I just switched to GNOME to see if everything was OK there, and lo and behold, installing Kubuntu Desktop screwed up the awesome theme Ubuntu Studio used for GNOME.  Anyone got a backup of it?  Or know how to revert the changes?

I intend to stick mostly in KDE, and its theme is alright for me, but I really liked the GNOME theme's colors, which are now gone.

Have a look at this thread
[http://ubuntuforums.org/showthread.php?t=450156]("http://ubuntuforums.org/showthread.php?t=450156")

---

### Post by disasm on 2007-10-17
> **Saoshyant said:**
> I am on Ubuntu Studio, which uses GNOME.  SInce I'm not keen to GNOME I have tried doing just this, but after restarting--due to also installing the Nvidia driver--I can't get X to start at all.  I still have access to a recovery shell, but I am not sure what file to restore/change/whatever to get X up again.  I'm also not sure if this was caused by installing the Kubuntu desktop on top of Ubuntu Studio, or because of the Nvidia driver, which I never got a problem with it on my older system.

I remember that during the kubuntu-desktop install, I was asked if I wanted to use GDM or KDM, and I chose KDM because I wanted to use KDE.  Maybe this is to blame?  What file to restore, then?

apt-get install ubuntustudio-desktop

For future reference, don't install kubuntu-desktop. If you want kde, just install the "kde" package. then it won't install kdm, the artwork, the different bootsplash, etc...

Sam

---

### Post by R. Deegan on 2007-10-19
Terminal allows me to enter the code, but when the password is requested it won't allow my KB to enter the password.

Suggestions anyone?

Edit: Font size fixed.

---

### Post by bodhi.zazen on 2007-10-19
> **R. Deegan said:**
> [SIZE="3"]Terminal allows me to enter the code, but when the password is requested it won't allow my KB to enter the password.

Suggestions anyone?[/SIZE]

1. no need for large fonts.

2. enter you password and hit enter. The text is not reflected on the screen so you will not see anything as you type.

---

