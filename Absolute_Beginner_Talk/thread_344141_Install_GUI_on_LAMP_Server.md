---
title: "Install GUI on LAMP Server?"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by carmon_madison on 2007-01-22
How can I install the X Windows GUI on the LAMP server? I need to get Simple Machines up and running so I need some direction.

---

### Post by guysmiley25 on 2007-01-22
I've been avoiding LAMP because I though it came with a GUI.

To install GUI

```
sudo aptitude install xorg
```

then either one of gdm, xdm, or kdm.

```
sudo aptitude install gdm/xdm/kdm
```

then either xubuntu-desktop, ubuntu-desktop, kubuntu-desktop. Or xfce/gnome/kde/openbox/etc I use xfce so I did.

```
sudo aptitude install xfce4
```

the difference between xfce and xubuntu is that xubuntu comes with more apps. I think the same applies to gnome/ubuntu kde/kubuntu.

Hope that helps.

---

### Post by Hanzerik on 2007-01-22
Or if you want the default Gnome desktop
```

sudo apt-get install ubuntu-desktop

```

---

### Post by Pobega on 2007-01-22
If you decide to go the Xubuntu route, but choose to install the xfce4 package make sure to installing thunar alongside it, otherwise you'll have no file browser.

**Edit:** Although xfce4 *might* install Thunar automatically, it's probably safer to install the xubuntu-desktop metapackage.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-01-22
Not sure where your at with your setup, but this is a fairly decent HowTo: 

<<there's a lot of 'extra' stuff included within this howto; however, you should be able to skim through any non-applicable details depending on your overall needs>>

[http://www.ubuntuforums.org/showthread.php?t=331017](http://www.ubuntuforums.org/showthread.php?t=331017)

---

### Post by carmon_madison on 2007-01-23
Okay. First off, I am not dumb but be patient.

I get this message

*Couldn't find package "xorg", and more than 40 packages contain "xorg" in their name.*

Which I take that it is having a problem installing xserver? **I know, Give me my helmet before I hurt myself.**

Just keep leading the blind man.

Thanks

---

### Post by guysmiley25 on 2007-01-24
Are you using Edgy or Dapper. In edgy it should be

```
sudo aptitude install xorg
```

and in dapper, and properly other older systems its

```
sudo aptitude install x-window-system-core
```

Here the guide I learned from

[Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

Hope that helps.

---

### Post by guysmiley25 on 2007-01-24
Oh and make sure you have the right repositories setup. You could try [this]("https://help.ubuntu.com/community/Repositories"), or [this]("http://ubuntuguide.org/").

Edit: Also I found I had a problem when I installed things in the wrong order, so be warned.

I recommend installing X then gdm/kdm/xdm, then gnome/kde/xfce.

eg

```

sudo aptitude install xorg
sudo aptitude install gdm
sudo aptitude install xfce4

```

Then restart. Then when you login make sure you choose xfce or whatever from the sessions list. I have found problems in the past when not doing so.

---

### Post by carmon_madison on 2007-01-24
I want to thank everyone for their help. Your info and links helped me work through the install of the xserver. :D :D :D

---

### Post by guysmiley25 on 2007-01-25
Not a problem. In my option anything to make it better and easier to not use winblows.

---

