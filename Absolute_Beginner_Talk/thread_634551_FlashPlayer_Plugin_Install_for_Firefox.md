---
title: "FlashPlayer Plugin Install for Firefox"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by berencamlost on 2007-12-07
I'm Trying to install the flashplayer 9 plugin for firefox but i'm having some problems. I downloaded the RPM from adobe then i converted it to DEB with alien and i tried to install it. The installation (the GUI one) claims it installed correctly but it didn't work. I tried to install it then using the Terminal and when it finished  the install it still didn't work. Any idea how i can get the flash player plugin to work or what might be going wrong.
Thanks for the Help...

---

### Post by Majorix on 2007-12-07
Have you tried
```
sudo apt-get install flashplugin-nonfree
```
?

---

### Post by berencamlost on 2007-12-07
No, but when i did try it it gave me the message that it was already installed (the most current version if it) i went to test it on youtube but still nothing.

---

### Post by Majorix on 2007-12-07
Can you please check in Firefox Tools > Add-ons > Plugins if Flash Player is disabled?

---

### Post by berencamlost on 2007-12-07
There isn't anything their but ubufox

---

### Post by berencamlost on 2007-12-07
bump

---

### Post by erfahren on 2007-12-07
> **berencamlost said:**
> No, but when i did try it it gave me the message that it was already installed (the most current version if it) i went to test it on youtube but still nothing.
ok, you made this a little (a lot) more difficult than it needed to be. There really isn't much to the Flash plugin.

The Flashplayer install usually just makes a directory /usr/lib/flashplugin-nonfree and then puts a symlink (symbolic link) to the file(s) in the /usr/lib/firefox/plugins directory.

If I were you I'd go ahead and uninstall the .deb you made. The easiest way is to go to Synaptic Package Manager (under System > Administration) and click the "Status" button on the lower left. In the list on the left pane you should see "Installed (local or obsolete)". Click on that and see if it's listed. If it is, uninstall it and then install as Majorix said.

---

### Post by nadamsieee on 2007-12-07
[LIST=1]
[*]download [adobe flash]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") by hand
[*]extract **libflash.so**
[*]cut and paste the .so to **/usr/lib/firefox/plugins/**
```
sudo nautilus /usr/lib/firefox/plugins/
```
[*]make sure the .so is readable by everybody
[*]restart firefox
[/LIST]

---

### Post by Amstell on 2007-12-07
> **nadamsieee said:**
> [LIST=1]
[*]download [adobe flash]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") by hand
[*]extract **libflash.so**
[*]cut and paste the .so to **/usr/lib/firefox/plugins/**
```
sudo nautilus /usr/lib/firefox/plugins/
```
[*]make sure the .so is readable by everybody
[*]restart firefox
[/LIST]

Worked perfectly.  Thank you I have been trying to get this working for a while.  Thanks

---

### Post by Famicommander on 2007-12-07
> **nadamsieee said:**
> [LIST=1]
[*]download [adobe flash]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") by hand
[*]extract **libflash.so**
[*]cut and paste the .so to **/usr/lib/firefox/plugins/**
```
sudo nautilus /usr/lib/firefox/plugins/
```
[*]make sure the .so is readable by everybody
[*]restart firefox
[/LIST]

I was having the same problem, and that fixed the problem for Fire Fox.

But do you know how to make the plugin work in Opera? 

In Feisty, Opera used the FF plugins, but those plugins won't work in Opera for some reason.

---

### Post by Majorix on 2007-12-07
Installing from source is against the idea of Ubuntu and its package management system. They are not updateable and may sometimes require compilation.

---

### Post by Bigtimexpower on 2007-12-07
I too am having trouble installing flash.. But i don't understand the instructions given here. can you explain? I get lost on the step about extracting the .so. sorry just installed ubuntu 30 mins ago

---

### Post by erfahren on 2007-12-07
> **Famicommander said:**
> I was having the same problem, and that fixed the problem for Fire Fox.

But do you know how to make the plugin work in Opera? 

In Feisty, Opera used the FF plugins, but those plugins won't work in Opera for some reason.
as I said earlier. When installing Flash it makes the directory /usr/lib/flashplugin-nonfree and creates symlink(s) to the file(s) in /usr/lib/firefox/plugins.

So if installed that way all you need to do is:
```

sudo ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/opera/plugins 

```
and (if it exists)
```

sudo ln -s /usr/lib/flashplugin-nonfree/flashplayer.xpt /usr/lib/opera/plugins

```
(the newest Flash doesn't have that second file (I have no idea what it does - lol )

Anyway, I've tested the newest Flash 9 from Adobe with Opera and it didn't work at all. (I thought it was a little buggy in Firefox as well.) 

Actually the older Flash 9 was buggy with Opera, caused crashes, etc. so I started using Flash 7 for Opera and Flash 9 for Firefox. Just making seperate directories /usr/lib/flashplugin-nonfree-7 /usr/lib/flashplugin-nonfree-9 and linking them to Opera and Firefox respectively.

---

### Post by erfahren on 2007-12-07
> **Bigtimexpower said:**
> I too am having trouble installing flash.. But i don't understand the instructions given here. can you explain? I get lost on the step about extracting the .so. sorry just installed ubuntu 30 mins ago
The Flash plugin is available in the repositories. Just open Synaptic (System > Administration) and search for Flash. 

Or just install ubuntu-restricted-extras which includes Flash and Java.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You may need to correct or enable your repositories to find it, see:
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)

---

### Post by NickGray on 2007-12-08
**erfahren**, I believe the issue is with Flash 9. A previous version of Flash was available on the repositories - perhaps Flash 7.

All of my attempts to use Package Manager to install Flash have been unsuccessful. There is an MD5 mismatch of the hash. Still trying to figure out a hack so that I can use YouTube again...

---

### Post by aafont70 on 2007-12-08
Thanks nadamsieee, I didn't realize it was that simple. I've been working on this for a month.

---

### Post by erfahren on 2007-12-08
> **NickGray said:**
> **erfahren**, I believe the issue is with Flash 9. A previous version of Flash was available on the repositories - perhaps Flash 7.

All of my attempts to use Package Manager to install Flash have been unsuccessful. There is an MD5 mismatch of the hash. Still trying to figure out a hack so that I can use YouTube again...
The version available in the Feisty and Gutsy repositories is Flash 9 (pls include your Ubuntu versions folks!) 

Anyway, there is a *new* version of Flash 9 available from Adobe. It just got released, there is a thread about it here: [http://ubuntuforums.org/showthread.php?t=631310](http://ubuntuforums.org/showthread.php?t=631310)

I'm not sure what issue you're talking about. I really think you guys are making this too complicated. It really only consists of one file - libflashplayer.so (two if you count  flashplayer.xpt - which isn't present in the newest version).

If you have problems installing it with Synaptic then it's most likely you have other issues. How as it been unsuccessful? What's happening exactly?

---

### Post by daradib on 2007-12-08
This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by NickGray on 2007-12-10
Thanks **daradib**! That worked like a charm for me on Ubuntu 7.10.
 Thanks to **erfahren**, too - sorry if I was vague with my problem description. I believe my issue was unique to the Flash 9.0.115.0 install as daradib suggested.

---

### Post by buntunub on 2007-12-10
> **daradib said:**
> 
If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

Can you expand on that a bit please? How would you go about doing that?

---

### Post by erfahren on 2007-12-10
> **buntunub said:**
> Can you expand on that a bit please? How would you go about doing that?
there's a post on the bug report that has that information
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890)

---

### Post by erfahren on 2007-12-10
note: there is a thread dedicated to that bug issue here:
[http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)

---

### Post by buntunub on 2007-12-10
The build instructions just build the package that I already linked you to, which does not work properly. This package needs to be tested before it goes to upstream for release because its extremely buggy.

---

### Post by daradib on 2007-12-10
Yes, apparently it does not work with sites like nick.com and disney.com. I have not had problems as I don't use those sites. It would be good if someone tests Windows with the new flash player.

---

