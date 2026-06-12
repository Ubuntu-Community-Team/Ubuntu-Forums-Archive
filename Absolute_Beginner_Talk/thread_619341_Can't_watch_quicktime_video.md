---
title: "Can't watch quicktime video"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by frank002 on 2007-11-21
Hello:
 I am using Gutsy and am having trouble watching Quicktime movies. If I go to the Quicktime page and try to see movie trailers,  the captions underneath the trailers says "no video" and if I click on them Firefox closes. The same happens with Galeon.  I have looked at the posts here and nothing seems to remedy the situation. when i type about:plugins in Firefox, I see I have the following:
  vlc multimedia plugin
  totem web browser plugin
  quicktime plugin.

---

### Post by reckless2k2 on 2007-11-21
is libquicktime on your machine?

---

### Post by bpickel on 2007-11-21
Have you tried 

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by frank002 on 2007-11-21
I checked synaptic and I do have the libquicktime. I also got the ubuntu-restricted extras but none of this seems to help. Anyway, I will keep trying. Thankyou both for your quick reply.

---

### Post by Unterseeboot_234 on 2007-11-22
To view Quicktime movies in Firefox takes the mplayer plug-in. Because I run 64-bit Gutsy, I recommend Automatix2 for that particular install. Otherwise, MPlayer movie player -- separate downloand -- runs as a standalone movie projector to run a quicktime movie you have downloaded to your machine (much like Quicktime Player, but Quicktime, the Apple product, requires Wine on Linux).

My problem is I can't codec Quicktime to export or import movies into Kino, Kdenlive, Cinerella or Flash.:confused:

---

### Post by frank002 on 2007-11-22
Thanks. I have installed the mplayer mozilla plug in but when I do an about:plugins in Firefox, the plug in does not appear.

---

### Post by frank002 on 2007-11-22
By the way, about:plugins shows the vlc and totem plugins. The vlc plug in says it plays quicktime videos.

---

### Post by ThaDoctor99 on 2007-11-22
don't trust what it says, but look for what it does - obviously it doesn't work for you mplayer is amazing - just remember to install some gstreamer plugins - that will make it able to play almost anything....
anyway I think you should install the last plugin for mplayer under firefox that will make it rock even more!!


I use mplayer for most video things.

---

### Post by frank002 on 2007-11-22
Thanks

---

### Post by sageb1 on 2007-12-04
the following command worked for me.
After finding the plugin under Tools>Preferences:Content>Plugin Options>Find New... in Opera. 
i'll assume you know how to find and install plugins under mozilla.

$ sudo apt-get install libquicktime0 gxineplugin

---

### Post by Bishop Hill on 2007-12-10
I have the same problem.

For example, on [http://www.apple.com/se/ipodtouch/guidedtour/medium.html](http://www.apple.com/se/ipodtouch/guidedtour/medium.html), I get no video, but on [http://www.apple.com/se/ipodtouch/features.html](http://www.apple.com/se/ipodtouch/features.html) i don't even get a video, only the controls.

Typing about:plugins in firefox gives me

VLC Multimedia Plugin
Shockwave Flash
GCJ Web Browser Plugin (using IcedTea) 1.4
DivX Browser Plug-In
QuickTime Plug-in 6.0 / 7
RealPlayer 9
Windows Media Player Plugin
mplayerplug-in 3.40

All is active, and quicktime is listed multiple times. I also have restricted extras and every possible driver/app/whatever to run it, but it does not work:/

Can someone please help me=)?

---

### Post by amr2205 on 2007-12-18
> **frank002 said:**
> Thanks. I have installed the mplayer mozilla plug in but when I do an about:plugins in Firefox, the plug in does not appear.

Check inside of /usr/lib/firefox/plugins
The mplayerplugin* files must be there, but if you also find libtotem* files then delete them because for some reason Firefox takes totem files first instead of mplayer's

---

### Post by philinux on 2007-12-18
You can have too many plugins. Only one is needed.

Remove totem-mozilla and the vlc plugin.

Check about : Plugins and make sure just mplayer plugin is installed

---

### Post by gfahey on 2008-02-16
> **frank002 said:**
> Hello:
 I am using Gutsy and am having trouble watching Quicktime movies. If I go to the Quicktime page and try to see movie trailers,  the captions underneath the trailers says "no video" and if I click on them Firefox closes. The same happens with Galeon.  I have looked at the posts here and nothing seems to remedy the situation. when i type about:plugins in Firefox, I see I have the following:
  vlc multimedia plugin
  totem web browser plugin
  quicktime plugin.

FWIW, I am using Swiftweasel and had the same issue. Only, I'd click on a trailer and after it buffered, I got only sound. So, I right clicked on the screen right in the mplayer window and selected "configure". The top box under "video output" I selected x11 from the drop down menu. I also checked every box (like Quicktime etc;). That did it. Now it works fine. 

Just my .02 worth.

---

