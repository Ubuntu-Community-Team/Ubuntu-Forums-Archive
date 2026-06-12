---
title: "Beryl-Project Themes and Tarballs: How do you use them?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-24
[b][COLOR="darkblue"]I know Beryl is already on Ubuntu (Gusty) 7.10, but I want to know how to upgrade it and/or install it (if I ever need to do so).

I went to Berly-Project.org, and I got their latest tarball, so mow I have 3 questions:

1. *What is a Tarball?*
2. *How do you open a tarball and make it do what it's designed to do once you have downloaded it from that website?*: [http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php)

3.** Do you know where or how I can get my desktop to appear like that with Ubuntu 7.10 running on my computer with AMD64 (x64)?**

I'm just trying to find out how I can change the appearance of my folders, and add a dock to my desktop, like the people, who make their top & bottom desktop-panels & desktop appear fancy like this one:

[img]http://www.compiz-themes.org/CONTENT/content-pre1/74487-1.png[/img][/COLOR][/b]

---

### Post by northern lights on 2008-02-24
The Beryl project is no longer active.

Gutsy does not ship with Beryl either, it ships with compiz-fusion, a fuse of compiz and Beryl. If you wanna enable Beryl like features (that cool cube you're yearning for :)), run ```
sudo apt-get install compizconfig-settings-manager
```
And do your thing under "System > Preferences > Advanced Desktop Effects Settings"

[EDIT]

Just saw the screenshot:

The terminal background and foreground color and opacity can be altered in the terminal menu under "Edit > Current Profile", "Colors" Tab.

The "bottom panel" is not a panel. In the screenshot, the native panel has been removed (right click) and is replaced by a dock. This particular one appears to be [AWN]("https://launchpad.net/awn"), I'd recommend cairo-dock though. Download these two files:
[cairo-dock_v1.4.6.3_i686-32bits.deb]("http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.4.6.3_i686-32bits.deb")
[cairo-dock-plug-ins_v1.4.6.3_i686-32bits.deb]("http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.4.6.3_i686-32bits.deb")
Choose "Open With GDebi Package Installer". If that option doesn't appear, run this first: ```
sudo apt-get install gdebi
```

You can download icon packs for instance at [gnome-look]("http://www.gnome-look.org")

[/EDIT]

---

### Post by ahuman on 2008-02-24
**[COLOR="DarkRed"]How do I add a dock like the one in that screenshot (referring to that screenshot-image I provided above)?[/COLOR]**

---

### Post by overdrank on 2008-02-24
> **ahuman said:**
> **[COLOR="DarkRed"]How do I add a dock like the on in that screenshot (referring to that screenshot-image I provided above)?[/COLOR]**

HI and there are several docks but you may like 
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)
I use it on Hardy and I use Kiba-dock on Feisty

---

### Post by northern lights on 2008-02-24
> **ahuman said:**
> **[COLOR="DarkRed"]How do I add a dock like the on in that screenshot (referring to that screenshot-image I provided above)?[/COLOR]**

Check my edited post above...

---

### Post by steveneddy on 2008-02-24
Check out the Desktop Effects and customization portion of the forums.

There you will find all of the questions you are about to ask about Compiz-Fusion.

Some cool and useful tips there, also.

But, yeah, dump Beryl. Beryl is dead.

---

