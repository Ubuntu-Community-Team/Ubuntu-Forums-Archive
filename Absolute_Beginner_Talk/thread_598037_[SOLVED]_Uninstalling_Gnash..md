---
title: "[SOLVED] Uninstalling Gnash."
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Hairy Hobbit on 2007-10-31
Good morning all.

I have a freshly installed version 7.10 setup.  I came to open a videoclip within Firefox (it was from youtube which I believe from my searches is a good way to force the appropriate software installation).  When I clicked on the Firefox "Install" message I was given a choice of Gnash or Flash and chose Gnash,    I find that Firefox crashes into grey/white mode whenever I try and open a clip.  In the end, the whole session locked up and I had to use the power switch to reboot.

Two questions if I may - firstly, out of interest, any thoughts on the crash itself?

Secondly, and more importantly, I decided to have a go at uninstalling Gnash.  I went into Synaptic and filtered by "installed applications"  (another tip from on here).   If I want to remove Gnash completely from my system and get it back to a known good state, how do I know which files to remove?  Will Synaptic take care of all that for me?

Don't get me wrong, I'm not giving up on Gnash - it just happens to be that this issue made me wonder how to go about uninstalling something.  I know where to do it (my eyesight isn't good enough for command line :-)   but I'm not sure how I make sure I am removing all that I should do to revert back.

Thanks.
HH

---

### Post by rohan000 on 2007-10-31
Go to File-> History in Synaptic and look for the day and time when you installed Gnash, and it will list the packages that were installed.

---

### Post by carlosjuero on 2007-10-31
You can also go to the Console and do this:
```

sudo apt-get remove gnash
sudo apt-get autoclean

```

This will uninstall gnash, and should uninstall any dependencies that are no longer required (and are likely linked only to gnash).

Edit: You can change the remove and use purge instead for a complete removal of all package files as well for gnash.

---

### Post by jaybombalous on 2007-10-31
goto synaptic and do a search for 'gnash'.

then find the one that is labled 'gnash' and is installed (green box), then u right click and check the option for 'complete removal' this will uninstall anything that gnash installed when it installed.

---

### Post by Hairy Hobbit on 2007-10-31
Thanks to all who replied.  I suppose I was just to cynical after being victim to the trash that MS installer leaves behind.  So Synaptic and the console just work?  NO rubbish left behind?  What a novel approach :-)

Thanks all.
HH

---

### Post by ximitzu on 2008-03-10
I just installed ubunu gutsy and Gnash plugin into my firefox. When i go to this website [www.conestogac.on.ca](www.conestogac.on.ca) there is a menu on top. normally if you put your cursor on any of the options you will get a drop down menu but the flash in the midle of the page dont allow me to see it, inother words the menu its like behind the flash... how can i fix it?

---

