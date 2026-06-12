---
title: "Installing Opera in Feisty fawn 7.04"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by darkrose on 2007-04-23
There's been quite a few problems with people upgrading to or installing Feisty and finding that Opera no longer works, or will not install.

A really simple solution is to install the statically linked version, this will install all of it's dependencies and get around the problems.

Download it from [_Planet Mirror_](http://public.www.planetmirror.com/pub/opera/linux/920b/final/en/i386/static/opera-static_9.20b-20070323.1-qt_en_i386.deb), then double click (Ubuntu) or right click (Kubuntu) to install.

---

### Post by GandG on 2007-04-23
The Opera "static version" DEB does install OK (in Ubuntu) , however, although the EULA is projected and Preferences, Themes etc work fine , the principal  problem remaining is it won't  allow Internet Browsing :) 

It simply hangs when any URL is typed. Quite odd!


Been a long time admirer/user  of Opera (WinME, WinXP, Linux) so hope its rectified soon.

---

### Post by kpel on 2007-04-23
Having used it on several fresh Ubuntu installs, the Opera .deb package for Edgy works fine in Feisty.  Well, look at that.  I just checked and Opera has updated their site; the Edgy and Feisty files are the same.

---

### Post by dreadlord_chris on 2007-04-23
Huh.... I got no problems with Opera. Did a fresh Feisty install on the 19th. First thing I do when my desk loads for the first time: Open Konq > Go to Opera site & dl latest (v9.20) & install it > close Konq for good.

There was a minor hiccup with Opera, a little over a week ago, when an Ubuntu upgrade (somex11 lib) broke Opera. Here, this thread deals with it:
[http://ubuntuforums.org/showthread.php?t=413352](http://ubuntuforums.org/showthread.php?t=413352)

---

### Post by IainT on 2007-04-23
Another with no Opera problems. Downloaded the Edgy package from Opera and it worked right off.

Quite like the new speed dial feature.

---

### Post by Abstraxis on 2007-04-23
Does anyone know how to install Opera 9.20 on Feisty (64bit) ?

---

### Post by Colonel Kilkenny on 2007-04-23
> **Abstraxis said:**
> Does anyone know how to install Opera 9.20 on Feisty (64bit) ?

On console: sudo dpkg -i --force-architecture path/to/operapackage.deb
And of course change the path and the file name...

---

### Post by Abstraxis on 2007-04-23
Thanks! This was the output: 

```
sudo dpkg -i --force-architecture /home/george/Desktop/opera-static_9.20b-20070323.1-qt_en_i386.deb 
dpkg - warning, overriding problem because --force enabled: 
 package architecture (i386) does not match system (amd64) 
Selecting previously deselected package opera-static. 
(Reading database ... 87274 files and directories currently installed.) 
Unpacking opera-static (from .../opera-static_9.20b-20070323.1-qt_en_i386.deb) ... 
Setting up opera-static (9.20-20070323.1) ... 
```

Apparently, Opera installed but doesn't work. I click on it and nothing happens.

---

### Post by GandG on 2007-04-24
> **GandG said:**
> The Opera "static version" DEB does install OK (in Ubuntu) , however, although the EULA is projected and Preferences, Themes etc work fine , the principal  problem remaining is it won't  allow Internet Browsing :) 

**It simply hangs when any URL is typed. Quite odd! **

Been a long time admirer/user  of Opera (WinME, WinXP, Linux) so hope its rectified soon.

Solved - looks like ' user error'  ! :redface:  When  upgrading to  Feisty I automatically replaced  the /etc/dhcp3/dhclient.conf. file - this previously had  ISP  DNS server addresses specified . 

Once  they were reinstated ,  Opera 9.20 worked fine. \\:D/   Since Firefox 2.0.0.3   worked prior to the dhclient config change,  it  clearly  makes other arrangements.

---

### Post by abelthorne on 2007-04-24
One or two days before I upgraded from Edgy to Feisty, I had a problem with Opera : some dependencies were broken and I couldn't complete a clean update of my system, so I uninstalled Opera. Then I installed Feisty.
Since, it seems that I cannot find Opera in the official (commercial) repositories anymore. Is that normal ?

---

### Post by zvacet on 2007-04-24
Unfortunatly yes.download it from Opera site

[http://www.opera.com/download/]("http://www.opera.com/download/")

---

### Post by abelthorne on 2007-04-24
But is it temporary or has Canonical dropped "support" for Opera ?

---

### Post by DracoPsycho on 2007-04-24
> **Abstraxis said:**
> Thanks! This was the output: 

```
sudo dpkg -i --force-architecture /home/george/Desktop/opera-static_9.20b-20070323.1-qt_en_i386.deb 
dpkg - warning, overriding problem because --force enabled: 
 package architecture (i386) does not match system (amd64) 
Selecting previously deselected package opera-static. 
(Reading database ... 87274 files and directories currently installed.) 
Unpacking opera-static (from .../opera-static_9.20b-20070323.1-qt_en_i386.deb) ... 
Setting up opera-static (9.20-20070323.1) ... 
```

Apparently, Opera installed but doesn't work. I click on it and nothing happens.

Same here. When launched from terminal it says 
```
exec: 264: /usr/lib/opera/9.20-20070409.1/opera: not found
```
I checked and file lies right there.

Anybody knows what might that mean?

---

### Post by Terracotta on 2007-05-05
> **DracoPsycho said:**
> Same here. When launched from terminal it says 
```
exec: 264: /usr/lib/opera/9.20-20070409.1/opera: not found
```
I checked and file lies right there.

Anybody knows what might that mean?

terracotta@Hydra:~$ opera
exec: 264: /usr/lib/opera/9.20-20070409.1/opera: not found


Same problem here.

---

### Post by DracoPsycho on 2007-05-06
Hi, I already know what to do with this. Problem is that 32bit applications don't work under 64-bit OS just like that. You have to download 32-bit environment to do so.

Here's what you have to do 

```
sudo apt-get install ia32-libs ia32-libs-gtk linux32
```

Then you launch Opera with

```
linux32 opera
```

If you want to have sound in flash applets you also have to insal libasound32 package or something similar. Well, I'm sure there's a plenty of articles about installing flash and java under 64-bit OS.

---

### Post by F-3582 on 2007-05-13
Opera works perfectly for me (using the build included in Feisty). Everything works: Flash, embedded PDF and stuff. The only thing that doesn't is embedded video and audio, although all required plugins are present and reported working. Whenever I visit a site that has an embedded video it only shows a grey (Opera-toolbar-grey) box and nothing happens. I tried disabling either the Totem or the MPlayer plugin, but nothing helped. Anyone else experiencing this problem?

---

### Post by Colonel Kilkenny on 2007-05-14
> **F-3582 said:**
> Opera works perfectly for me (using the build included in Feisty). Everything works: Flash, embedded PDF and stuff. The only thing that doesn't is embedded video and audio, although all required plugins are present and reported working. Whenever I visit a site that has an embedded video it only shows a grey (Opera-toolbar-grey) box and nothing happens. I tried disabling either the Totem or the MPlayer plugin, but nothing helped. Anyone else experiencing this problem?

The plugin-thingy is a problem. For some people they work and for others (like me) they don't.
Totem-plugin is useless.
Mplayer-plugin may work if you compile it.
xineplugin may work.
Mozplugger should work if you can configure it correctly.

Personally, I use Gecko Media Player ([http://dekorte.homeip.net/download/gecko-mediaplayer/)which](http://dekorte.homeip.net/download/gecko-mediaplayer/)which) works pretty perfectly. It must be compiled and requires also Gnome Mplayer (same site, I compiled it myself as well).

---

### Post by F-3582 on 2007-05-14
Thanks for the advice. Well, Gecko-Mediaplayer does run, somehow, unfortunately there are a few issues:

1. Whether or not it plays something is chosen at random.
2. Background sounds on [www.yourethemannowdog.com](www.yourethemannowdog.com) (and all those others) aren't looped.
3. I somehow find the idea of using a player interface forked from mplayerplug-in as a standalone player with an embedding plugin stupid. Why doesn't mplayerplug-in work in the first place?!?

By the way: I tried compiling mplayerplug-in myself, unfortunately it doesn't work, either. Could the reason be the fact that I compiled it against the Firefox dev packages instead of the Mozilla dev packages?

---

### Post by Cappy on 2007-05-19
> **DracoPsycho said:**
> 
If you want to have sound in flash applets you also have to insal libasound32 package or something similar.

```
lib32asound2
``` for future reference

---

