---
title: "Crazy colors - 1st gen Macbook Pro 15&quot;"
date: 2007-07-04
forum: Apple Intel Users
---

### Post by ggeneraux on 2007-07-04
Hi all, I have a 1st generation (ATI video card) MacBook Pro 15" that I'm trying to install Feisty on.  I installed reFit and Bookcamp, and then installed as normal using the alternate install disk.  Everything installed fine, except the Xserver didn't come up (as mentioned on [http://wiki.ubuntu.com/MacBookProFeisty/](http://wiki.ubuntu.com/MacBookProFeisty/)), so I did a dist-upgrade and then followed the instructions on the Feisty wiki page for installing and configuring the ATI drivers.  Right after the configuration, I was able to 'startx' and the GUI came up beautifully, resolution was correct, everything looked great.  However, the next time I rebooted, the screen looked like this ([http://flickr.com/photos/robbyt/537741087/](http://flickr.com/photos/robbyt/537741087/)), and remains that way regardless of whether I revert back to the old xconf, and also when I boot into Mac OS X.  This is definately not a NVidia video card.  Any ideas on what might be going on, and how to get rid of the funky colors (at the least, in OS X)? Many thanks in advance.

---

### Post by ronocdh on 2007-07-04
Try this command and re-enable the ATI driver and add the 1440x900 resolution (if necessary):
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ggeneraux on 2007-07-05
Thanks for the suggestion.  Unfortunately it didn't make any difference.  Since both OS X and Ubuntu were fresh installs, I blew away the partitions and reinstalled OS X, and despite this the strange colors are still there (starting from the initial splash screen with the apple icon).  Hopefully there isn't permanent damage to either the video card or the screen.  Unfortunately the computer is basically unusable until I get this straightened out.  I saw a post on the nvidia forums from someone who had some luck correcting this by putting the internal screen to sleep while attached to an external monitor, and then waking the internal screen back up.  It's a different video card, but, at least visually, the problem is identical the one this person had.  Any other suggestions are appreciated.

---

### Post by cyberdork33 on 2007-07-05
if you are getting that error before booting into any OS, then I don't know what to tell you. Most of the information I found about this applies to the Santa Rosa machines, which is completely different hardware.

What driver are you using in your xorg.conf?

---

### Post by ggeneraux on 2007-07-05
At the moment OS X is the only thing installed.  Prior to reinstalling OS X I did reconfigure the xserver to use the ATI driver as suggested above, but it unfortunately didn't make any difference.

---

### Post by cyberdork33 on 2007-07-05
yes but _which_ ATI driver. 

It sounds like either you have a hardware issue, or whatever driver you were using tried to initialize the display incorrectly, and now it is stuck that way. If you have completely wiped Ubuntu it might be easier to just take to Apple.

---

### Post by ggeneraux on 2007-07-05
I only recall there being an option for "ati" during the xserver reconfigure process, so beyond that I'm not sure which ati driver.  Over lunch I hooked it up to an external monitor and it works fine, so it appears to not be a card issue.

---

### Post by cyberdork33 on 2007-07-05
the 'ati' driver is an open source driver which is known not to work well on some Macs. (I know it doesn't work on mine)

You can trying using 'vesa' (which is just a generic driver), or you can try installing and using the 'fglrx' driver (proprietary driver from ATI that you are going to want to use anyway in the end so you can get 3D acceleration.)

I hope you get it figured out. maybe your screen connection is loose? IDK I am just guessing now.

---

### Post by ggeneraux on 2007-07-05
I appreciate your help.  I'll reinstall ubuntu tonight and have another go at it, at least now I know that I can hook up an external monitor and actually be able to read text (helpful for troubleshooting ;) ).  In the end your suggestion to take it to Apple might be what needs to happen, but I'd like to exhaust my options first.

---

### Post by ggeneraux on 2007-07-06
Just a FYI, I was able to solve the problem thanks to a helpful person on the Mactel-linux-users mailing list.  Basically it came down to reseting the P-RAM by using the following procedure:

[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

I have yet to make another stab at setting up the ati card under Ubuntu, but at least I'll know how to fix things if it happens again.  Thanks to everyone who gave suggestions.

---

### Post by cyberdork33 on 2007-07-06
ah that makes sense. Good Luck in the future!

---

