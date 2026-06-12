---
title: "Can't install feisty macbook pro cd"
date: 2007-04-19
forum: Apple Intel Users
---

### Post by muchmusic on 2007-04-19
I can't get the graphical installer to work by default, in safe graphics mode, using dexconf from command line, or dpkg-reconfigure xserver-xorg.

This is on the release download, not beta or RC or nightly.

Anyone else encounter this or have ideas?

Will the alternate installer work?

I may try it but it takes a long time to download even from the torrent.

Thanks for any input.

---

### Post by stickboy3k on 2007-04-19
I'm also having the same issue. no matter what I try I get the same "Fatal server error: no screens found." I suppose I could just boot into 6.10 and use Update manager to install the update to 7.04 but since I've already downloaded the cd I'd rather save my bandwidth...

---

### Post by ronocdh on 2007-04-19
> **muchmusic said:**
> I can't get the graphical installer to work by default, in safe graphics mode, using dexconf from command line, or dpkg-reconfigure xserver-xorg.

This is on the release download, not beta or RC or nightly.

Anyone else encounter this or have ideas?

Will the alternate installer work?

I may try it but it takes a long time to download even from the torrent.

Thanks for any input.
Ugh, I was never able to get Feisty Beta running. I'll try tonight with Final, but I've made sure to download both the Live and the Alternate. I recommend you give both a shoot, too.

And of course verify the checksum on the CD, wear your coat when you go outside, brush your teeth, stay in school...

---

### Post by Chowbow on 2007-04-19
I'm having the same issues on my Macbook Pro (C2D). I downloaded the i386 version, the most "common" install. 

Booted from the CD, and I could not use my keyboard to select any of the options. A USB keyboard did not work either. Since I'm a big Linux noob, I got to the console, and pretty much didn't do anything from there and just quit.

Would love to be able to tripleboot OSX / XP / Ubuntu though. Please post if anybody has any success!

TIA.

---

### Post by muchmusic on 2007-04-19
It looks like we will *NOT* have success with feisty final release. See this bug [https://bugs.launchpad.net/bugs/89853](https://bugs.launchpad.net/bugs/89853) ... [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/95253](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/95253) is a duplicate most likely.

Boils down to a bug not fixed or didn't make the fix into the final release.

---

### Post by muchmusic on 2007-04-19
[http://ubuntuforums.org/showthread.php?t=413713](http://ubuntuforums.org/showthread.php?t=413713)

Is about this issue, it is not limited to macbook pros =0

Alternate cd did not work for me. I am trying a solution at the end of page 2 of that thread, namely being connected to the internet and at the command line:

sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx

Of course you will be using the proprietary driver at this point.

NOTE: Due to this being feisty release date the download of xorg-driver-fglrx from the main archive may take a very long time or not begin at all. Try back or use a mirror I think.

---

### Post by muchmusic on 2007-04-19
It worked ... installing now =) Alternate CD install also works, just login at the command line and then enter the same code as in the post above.

---

### Post by Chowbow on 2007-04-19
Thanks for the tip, I'm going to try that now.

---

### Post by muchmusic on 2007-04-19
Just a quick update to say install worked. Now I get to try to get wireless working. Don't forget this is a WORKAROUND and not a fix, as we are using the proprietary driver to install (unless using the alternate install cd) and then again to startx

Good luck all

---

### Post by Chowbow on 2007-04-19
Got the LiveCD working with your instructions... But I have not installed it yet. I'm hoping there may be a true "fix" for this issue in a later build possibly? Since I'm new to Linux I'd rather not get too crazy with it yet and try to fix workarounds! 

Additionally, I have OSX and XP via bootcamp, and was unsure how to partition. I know I could use rEFIt but it seems complicated and I would only have Ubuntu to "dink around with" first. Can I just partition the "Windows" partition and basically have 2 bootloaders? Eg. I could turn my mac on and choose between OSX and Windows, and if I choose Windows, I can choose between Ubuntu and Windows. I'm assuming there's no problem with this chain-loading, and I have no issue with doing it this way myself. I don't want to butcher up my OSX partition though. If I lose the XP partition I could live with it and reinstall... 

I realize the above is a little OT, if somebody could give me a quick answer that would be appreciated, otherwise, please ignore and continue on with the main topic of this thread. 

TIA.

Brian.

---

