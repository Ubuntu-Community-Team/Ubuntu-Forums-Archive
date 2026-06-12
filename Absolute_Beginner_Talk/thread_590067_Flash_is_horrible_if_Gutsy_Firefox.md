---
title: "Flash is horrible if Gutsy Firefox"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by borovy3488 on 2007-10-24
Does anyone know how to make flash work any better in firefox?  So far, it is impossible for me to play any flash games, and hardly any movies.  For example, I simply can not play this game: [http://portal.wecreatestuff.com/]("http://portal.wecreatestuff.com/") at all.  It will load, but will be SO SLOW and eventually crash firefox.  So far, I have tried everything I could dig up, including disabling ipv6. 

Thanks,
Wayne

---

### Post by Seisen on 2007-10-24
What extensions and add-ons do you have in firefox?

---

### Post by chamberlain2006 on 2007-10-24
As far as I know, Gutsy uses Gnash by default.  Have you run the installer for Adobe Flash Player yet?

---

### Post by Inxsible on 2007-10-24
> **chamberlain2006 said:**
> As far as I know, Gutsy uses Gnash by default.  Have you run the installer for Adobe Flash Player yet?
No it doesn't by default. The first time you go to a flash enabled web page, it asks you if you want to install Adobe Flash Player or Gnash SWF Player. 

If you choose one or the other, then it becomes the "default" for you.

---

### Post by borovy3488 on 2007-10-24
I'm pretty sure I installed the other version of flash.  I did an upgrade from feisty so I think I had to of.  Here is the output of my about: plugins page:: Shockwave Flash, GCJ Web Browser Plugin 0.92, Totem Web Browser Plugin 2.20.0, Windows Media Player Plug-in 10 (compatible; Totem), DivXÂ® Web Player, QuickTime Plug-in 7.2.0, DivX Browser Plug-In, QuickTime Plug-in 6.0 / 7, RealPlayer 9, Windows Media Player Plugin, and mplayerplug-in 3.40.

THANKS FOR THE FAST RESPONSES!!!

---

### Post by chamberlain2006 on 2007-10-24
Ok.  I've read suggestions in the forums that say to open Synaptic and uninstall both "flashplugin-nonfree" and "gnash".  Then open Firefox, go to a flash page (ie. YouTube) and click the "Install Plugin" thing, and go through the wizard.

---

### Post by hardyn on 2007-10-24
flash in linux sucks.... there is not much that we can do about it until flash or gnash gets better.

gnash was not working at all for me... and flash is about the same as it has allways been, unstable and not very good.

---

### Post by philinux on 2007-10-24
i've got the shockwave plugin from the repo and the site in question loads in a second.

I'd try from the terminal firefox -safe-mode and see what gives.

---

### Post by alienexplorers on 2007-10-24
I can't see why you would be having problems using flash.  On my old k6-III 450 Mhz with a Nvidia FX5200 card flash runs so smooth and clean.  I can sit and watch youtube video's with no problem I have also given wecreatestuff.com a try with no lagging with flash.

---

### Post by hardyn on 2007-10-25
ahh... but have you ever noticed that menus sometimes appear behind things, like the nvidia site?  and i find it crashes all over the place if you don't watch a whole video on utube, or by clicking forward / back on the browser

---

### Post by jenhsun on 2007-10-25
HA HA, I just solve the flash problem recently. Let me tell you guys mine.

My PC is 64 bits. It's more difficult to have flash player running. We have to have Gnash or nspluginwrapper. However, gnash sometimes not goes very well. And for me, to manually do the wrapper sometimes not work. The funny thing is I just clean every flash plugin out.
And do a  

sudo apt-get install flashplugin-nonfree 

That's it. it will automatic use nspluginwrapper wrap the libflashplayer.so for you.

My little experience.

---

### Post by magicman5421 on 2007-10-25
flash works fine for me...(32 bit user)

---

### Post by jenhsun on 2007-10-25
> **chamberlain2006 said:**
> Ok.  I've read suggestions in the forums that say to open Synaptic and uninstall both "flashplugin-nonfree" and "gnash".  Then open Firefox, go to a flash page (ie. YouTube) and click the "Install Plugin" thing, and go through the wizard.

It won't work. We are in the Linux world, not windows

---

### Post by d-_-b on 2007-10-25
one way that i managed to get flash working perfectly was to install sun-java6 AND flash-nonfree. no menu behind bars or any other problems when ive installed both :) amd64 here:D

---

### Post by macogw on 2007-10-25
Gran Paradiso (FF3) + Flash + Gutsy = when you close a YouTube tab, the sound keeps playing and sometimes the sounds play doubled so you hear it like they're doing a round

---

### Post by jenhsun on 2007-10-25
> **macogw said:**
> Gran Paradiso (FF3) + Flash + Gutsy = when you close a YouTube tab, the sound keeps playing and sometimes the sounds play doubled so you hear it like they're doing a round

Gran Paradiso has new layout Gecko 1.9. That's why.
Adobe flash has it's layout engine too. I think they just conflict with each other.

---

### Post by Soarer on 2007-10-25
> **jenhsun said:**
> HA HA, I just solve the flash problem recently. Let me tell you guys mine.

My PC is 64 bits. It's more difficult to have flash player running. We have to have Gnash or nspluginwrapper. However, gnash sometimes not goes very well. And for me, to manually do the wrapper sometimes not work. The funny thing is I just clean every flash plugin out.
And do a  

sudo apt-get install flashplugin-nonfree 

That's it. it will automatic use nspluginwrapper wrap the libflashplayer.so for you.

My little experience.

Yep, that works fine for me too, including the game mentioned.

---

### Post by jis on 2007-10-25
> **jenhsun said:**
> It won't work. We are in the Linux world, not windows

It worked for me in Gutsy. See also "Firefox plugins in Ubuntu" at
[http://www.ubuntu.com/getubuntu/releasenotes/710tour](http://www.ubuntu.com/getubuntu/releasenotes/710tour)

---

### Post by jenhsun on 2007-10-25
> **jis said:**
> It worked for me in Gutsy. See also "Firefox plugins in Ubuntu" at
[http://www.ubuntu.com/getubuntu/releasenotes/710tour](http://www.ubuntu.com/getubuntu/releasenotes/710tour)

jis, Thank you. I know that, in both 32 and 64 bits.
But I don't think you know whom i am talking to and what I mean. 
Please follow the thread from the beginning.

---

### Post by Endolith on 2007-10-27
> **chamberlain2006 said:**
> Ok.  I've read suggestions in the forums that say to open Synaptic and uninstall both "flashplugin-nonfree" and "gnash".  Then open Firefox, go to a flash page (ie. YouTube) and click the "Install Plugin" thing, and go through the wizard.

I tried this, but the video still plays.

When I go to about:plugins, it says:

> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes


So Flash 7 is still installed somehow?  And was overriding Flash 9, which is why it kept saying to upgrade?  I'm running Gutsy upgraded from Feisty upgraded from Edgy.

---

### Post by Endolith on 2007-10-27
And when  I reinstall nonfree plugin it lists two entries for Shockwave Flash in the about:plugins

---

### Post by Ubuntoob on 2007-10-28
Flash has been fine for me apart from I noticed that at [http://www.adobe.com](http://www.adobe.com) if you mouse over the top menu options - the dropdown menus appear behind the top animation.

---

### Post by jenhsun on 2007-10-28
> **Ubuntoob said:**
> Flash has been fine for me apart from I noticed that at [http://www.adobe.com](http://www.adobe.com) if you mouse over the top menu options - the dropdown menus appear behind the top animation.

Same here.

---

### Post by jis on 2007-10-28
And here. I have flashplugin-nonfree and sun-java6-bin installed (on 32bit x86 system).

---

### Post by jenhsun on 2007-10-28
[http://blogbeebe.blogspot.com/2006/03/annoyance-using-firefox-on-linux.html](http://blogbeebe.blogspot.com/2006/03/annoyance-using-firefox-on-linux.html)

---

### Post by jis on 2007-10-28
It is bug [49613]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/49613").

---

### Post by Endolith on 2007-10-28
> **jis said:**
> It is bug [49613]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/49613").

That's not the problem I'm having.  Every site I visit says "Please update your Flash Player", and about:plugins says:

> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes


Edit: 

I fixed it by: 

1. Removing flashplugin-nonfree completely
2. Remove libflashplayer.so and flashplayer.xpt from ~/.mozilla/plugins
3. Reinstalling flashplugin-nonfree

---

### Post by jenhsun on 2007-10-28
> **Endolith said:**
> That's not the problem I'm having.  Every site I visit says "Please update your Flash Player", and about:plugins says:



Edit: 

I fixed it by: 

1. Removing flashplugin-nonfree completely
2. Remove libflashplayer.so and flashplayer.xpt from ~/.mozilla/plugins
3. Reinstalling flashplugin-nonfree

We should be careful about the plugins for firefox. The problem which you have because you did have previous installation, then install twice. The symbolic link in between is crash. Same as Java plugins in any kinds.
Great to see you figure out by yourself. I think you should be proud of it.

---

### Post by Endolith on 2007-10-28
> **jenhsun said:**
> Great to see you figure out by yourself. I think you should be proud of it.

Got it from this thread: [http://ubuntuforums.org/showthread.php?t=339828&page=2#13](http://ubuntuforums.org/showthread.php?t=339828&page=2#13)

---

### Post by jeremy1138 on 2007-11-04
I had a problem with flash working for a long time because i installed gnash at first and then i installed the nonfree flash plugin.  The video player on youtube looked all messed up and the volume control and all that wouldn't work.  I fixed it by using synaptic package manager to search for "gnash" and I uninstalled everything that had anything to do with gnash (3 entries).  Flash seems to be working perfectly now.

---

### Post by amoghvc on 2007-12-17
Flash did not install properly at all when I did the following: 

1. used Synaptic package manager to install flashplugin-nonfree.
2. when I visited a page and clicked on install plugins to install.
3. when I ran "sudo apt-get install flashplugin-nonfree"

Then I when to Adobe website and downloaded the tarball and installed Flash Version: 9,0,115,0 from link: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash). But it was very very unstable and it gave me all sorts of errors, The standalone debugger for flash was unstable too.

So I downloaded this tarball which has older archived versions of Flash Player for Linux ([http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)) and ran the installer in shell for flash version 9,0,48,0. It installed correctly and everything is now fine.

If you have multiple plugin versions problem, check the following locations for Firefox and see if the library is repeated / different versions exist and remove multiple copies / the version you don;t want :

1. /usr/lib/mozilla/plugins/
2. /usr/lib/firefox/plugins/
3. /home/username/.mozilla/plugins/

That is the order in which plugins get loaded from the locations. Hope this helps.

cheers,
Amogh

[EDIT] if you are installing flash from sources other than the Ubuntu standard repositories, then do not install anything newer than 9,0,48,0 since I'm not sure that they are stable for Firefox 2.0.0.11.

---

### Post by dvo on 2008-01-02
I can confirm that flash version 9,0,48,0 works fine with Firefox  on Gutsy.
To install it on an x86_64 architecture, I did the following:

```
tar xzf install_flash_player_9_linux.tar.gz
```
then commented out the error exit in the architecture check:
```
#   exit_cpu $TEMPARCH
```
in install_flash_player_9_linux/flashplayer-installer, then
```
install_flash_player_9_linux/flashplayer-installer
sudo apt-get install nspluginwrapper
nspluginwrapper -v -a -u
```

---

