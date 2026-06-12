---
title: "Screen Resolution help"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by falonyn on 2007-04-05
I just installed Ubuntu on a laptop running Intel GMA and I am only able to run 1024 x 768 on my widescreen laptop. I saw some of the post regarding this, but they were in reference to nVidia graphics, and not intel GMA. Can someone please give me an idea of how to fix this. Last time I had Ubuntu on this laptop there was no problem. Thanks.

---

### Post by %hMa@?b&lt;C on 2007-04-05
sudo dpkg-reconfigure xserver-xorg
run that from terminal

---

### Post by falonyn on 2007-04-05
I ran it, but I am not totally sure what I am looking for once this program is running. What are these options?

---

### Post by jerrylamos on 2007-04-05
> **falonyn said:**
> I just installed Ubuntu on a laptop running Intel GMA and I am only able to run 1024 x 768 on my widescreen laptop. I saw some of the post regarding this, but they were in reference to nVidia graphics, and not intel GMA. Can someone please give me an idea of how to fix this. Last time I had Ubuntu on this laptop there was no problem. Thanks.

Ubuntu Feisty Beta as of about April 3 has changed X windows support which on my desktop with Intel graphics chip now supports 1280x1024 LCD monitor  (It used to be stuck at 1024x768).  The fix is on all three configurations, Kubuntu, Ubuntu, and Xubuntu.  You can find them at:

cdimage.ubuntu.com/cdimage/dailiy-live/current
cdimage.ubuntu.com/cdimage/xubuntu/daily-live/current
cdimage.ubuntu.com/cdimage/kubuntu/daily-live/current

Note these are Beta a couple of weeks away from the release candidate, and do have some problems yet.  Also note the Ubuntu is 711 mb which doesn't fit on a CD; use a DVD.  The others fit.

I have a Feisty Ubuntu install which I did before the graphics fix.  I get a bunch of updates automatically every day or two, and the fixed X window support was in one of the updates.  You could try System, Administration, Update Manager to see if that would help.

An alternative is to try "safe graphics mode" on the initial bootup screen which supports resolutions better than 1024x768 by using a generic graphics driver VESA.  It's a bit slow especially scroll wheel but works for more situations than the default.

The X window configuration support problem comes from some code Ubuntu development picked up from Debian.  While Ubuntu is based on Debian originally, I get the impression they went back to Debian last fall some time and got some code which from my perspective had more bugs than the earlier Ubuntu Dapper level.

Cheers, Jerry

---

### Post by falonyn on 2007-04-05
So you are saying that I should update to Feisty Fawn beta and let the updates potentially take care of the problem?

---

### Post by kyphi on 2007-04-05
To change resolution from the Terminal window, type

sudo dpkg-reconfigure -phigh xserver-xorg

On the resulting screen, use your up/down keyboard buttons to scroll to the resolution that you want and press the spacebar.  Press Enter and then exit.

Please note the space before -phigh.

---

### Post by falonyn on 2007-04-05
When I typed that into the Terminal I got: 

xserver-xorg postinst warning: overwritin possibly-curtomized configuration fule; backup in /etc/X11/xorg.conf.20070405201846

However nothing really happened. I got the screen to flash black and then back to what it was before.

---

### Post by kyphi on 2007-04-05
Press Ctrl + Alt + Backspace

or

Log Out

When you log back in you should have access to your chosen resolution.

---

### Post by ramjet_1953 on 2007-04-05
Try this first. [http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647)

It's far less perilous than fiddling manually with your xorg.conf file.

Regards,
Roger 8)

---

### Post by falonyn on 2007-04-05
This has given me several normal screen resolutions, but no widescreen resolutions. How do I get it to give me some widescreen resolutions and ones that are higher than 1024 x 768?

---

### Post by falonyn on 2007-04-05
> **ramjet_1953 said:**
> Try this first. [http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647)

It's far less perilous than fiddling manually with your xorg.conf file.

Regards,
Roger 8)

I am trying this, but I am not sure which repositories to enable in the synaptic. I tried using the apt-get way someone posted in this thread you linked me to, but that didn't work either. Sorry, but I am a total noob to this and need some major walk-through for this operation. 

After knowing what repositories to enable I think I might be able to follow the rest. Thanks.

---

