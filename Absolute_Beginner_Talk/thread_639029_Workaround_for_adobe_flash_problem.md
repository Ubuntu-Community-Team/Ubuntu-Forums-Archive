---
title: "Workaround for adobe flash problem"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Afkpuz on 2007-12-12
I'm sure that this has been posted somewhere else, but there are alot of people who need help with this.  

This solution is for those of you who have installed the flash player plugin through firefox's plugin manager, only to have it not work.  You goto a flash site and it says you need to install the flash plugin.  So you try again, and it says "you've already installed flash!"  Here's the fix


Synaptics version is broken.  Until it's fixed, use the flash player version on the adobe website.




Remove Synaptics version
```

sudo apt-get remove flashplugin-nonfree gnash

```


Download the tar from the adobe website here.  Save to desktop
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

```

cd Desktop

tar -zxvf install_flash_player_9_linux.tar.gz 

sudo ./install_flash_player_9_linux/flashplayer-installer 



```


Make sure you close all firefox windows and installer should automatically install.  If it asks you where to install, install to /usr/lib/firefox

You're done!

---

### Post by aonegodman on 2007-12-12
Thank you so much for posting this. While I didn't get it to install because I don't know the PATH requested to Mozilla, I can see that it would work if I was running off a regular install and not the LiveCD(can't write). ;)

---

### Post by daradib on 2007-12-12
You can also see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669) (which has been updated) for a lot of information on this bug, fixed packages (and how to build own packages- which is a more "correct" way to fix), and information about the fixed packages which have been uploaded to all supported proposed repositories (6.06-7.10). The binary packages should soon be built, but you can use the provided binary packages in that thread, which are compiled versions of the uploaded source packages.

---

### Post by Cabbages on 2007-12-24
I was also unable to figure out the installation path. I typed in /usr/lib/mozilla, but Terminal found this an unsatisfactory response. Any help would be a appreciated, because I'm really sick of this issue. 

Oh, and kindly put your responses into n00b-sp33k.

Edit: Nevermind! I put in /usr/lib/firefox instead, and was able to complete the installation. It works perfectly, thank you!!

---

### Post by citiusaf215 on 2007-12-29
I was having these issues too, this helped a ton.  Thanks!

---

### Post by kelvin spratt on 2007-12-29
Their are some very simple instructions on this link
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
you can copy paste into terminal then just press enter and the installer does it all for you. Hope this helps somebody.

---

### Post by jotacebusta on 2008-01-04
Thanks! I wors great with firefox.

However, how do I do for Konqueror. I looked for a /us/lib/konqueror directory, but i didn't found it.  I dindn't tried to install anything else (via synaptic for instance), I don't want to create conflictsbetween the plug-ins.

Thanks,

JC

---

### Post by daradib on 2008-01-04
See [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

> 
The new version of Flash is incompatible with Konqueror because it requires XEmbed ([Launchpad Bug# 174343]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/174343")). 9.0.48.0 is the last version of flash to support Konqueror in its current state.

---

