---
title: "New Flash Player 9 Beta for Linux! (Now With acclerated Video)"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-08-22
New release "beta" of Flash Player for Linux

[http://blogs.adobe.com/penguin.swf/2007/08/h_dot_two_sixty_four.html](http://blogs.adobe.com/penguin.swf/2007/08/h_dot_two_sixty_four.html)

Somebody knows how to install it?

Do we have to copy the file libflashplayer.so inside some plugins folder?

---

### Post by overdrank on 2007-08-22
> **Kosimo said:**
> New release "beta" of Flash Player for Linux

[http://blogs.adobe.com/penguin.swf/2007/08/h_dot_two_sixty_four.html](http://blogs.adobe.com/penguin.swf/2007/08/h_dot_two_sixty_four.html)

Somebody knows how to install it?

Do we have to copy the file libflashplayer.so inside some plugins folder?

Hi it does state on that page that you must uninstall previous version and then has this page
[http://labs.adobe.com/technologies/flashplayer9/releasenotes.html#install](http://labs.adobe.com/technologies/flashplayer9/releasenotes.html#install)

---

### Post by Kosimo on 2007-08-22
Installed.

It have a very nice fullscreen mode.
If you go to youtube, and hit fullscreen it doesn't stop the video. Cool ;)

---

### Post by shavenlunatic on 2007-08-22
woo.. fullscreen.. FINALLY!!!!

---

### Post by jsully1 on 2007-08-22
Crashes my firefox as soon as anything starts playing, and doesn't let me left click on videos still :(

---

### Post by Kosimo on 2007-08-22
> **jsully1 said:**
> Crashes my firefox as soon as anything starts playing, and doesn't let me left click on videos still :(


Really?  Here's working perfectly. How did u install it?

---

### Post by jsully1 on 2007-08-22
Manually copied the files to my plugin directory

---

### Post by Kosimo on 2007-08-22
> **jsully1 said:**
> Manually copied the files to my plugin directory

You should run the installer. It automatically does everything for you.
Just double click, and (run in terminal)

---

### Post by Kosimo on 2007-08-22
Ah, remember to uninstall your current version by deleting the flash plugin in your home directory

---

### Post by jsully1 on 2007-08-22
I did uninstall.  I can't get any version to run now though, even with a clean install and nuking the .macromedia directory in home..

---

### Post by chriseo22 on 2007-08-22
Before all of this i was able to watch videos in a separate window full screen, but after the new install i can watch anything in a flash frame, but that is it.  The new version doesn't allow clicking on anything flash, so i can't even pause a YouTube video.  O well back to the old version I was looking forward to the accelerated video but I guess I will wait for another release.

I also found a little problem when uninstalling, I installed flash originally with Automatix so i had to uninstall it with AutoMatix so if you are having trouble uninstalling, that may be it.

With Crap,
Chris

---

### Post by mysticmatrix on 2007-08-22
> **chriseo22 said:**
> Before all of this i was able to watch videos in a separate window full screen, but after the new install i can watch anything in a flash frame, but that is it.  The new version doesn't allow clicking on anything flash, so i can't even pause a YouTube video.  O well back to the old version I was looking forward to the accelerated video but I guess I will wait for another release.

I also found a little problem when uninstalling, I installed flash originally with Automatix so i had to uninstall it with AutoMatix so if you are having trouble uninstalling, that may be it.

With Crap,
Chris

Confirmed on my side with Intel G965 IGP. Better to old version.
(I didn't install from automatix)

---

### Post by jsully1 on 2007-08-22
Which version are you two reverting to?
Also, I've read that if you right click first then you can left double click immediately after.

---

### Post by sumguy231 on 2007-08-22
> Confirmed on my side with Intel G965 IGP. Better to old version.
I also saw that, though restarting the browser made it work again and it hasn't happened since. Huh. Though on the other side, this beta seems to perform better than the stable version, even without accelerated video.

By the way, stupid question, how do you get to fullscreen? I can't even find any documentation on Flash or anything.

---

### Post by mikewhatever on 2007-08-22
> I can't even find any documentation on Flash or anything.
[http://www.adobe.com/products/flashplayer/productinfo/faq/](http://www.adobe.com/products/flashplayer/productinfo/faq/)

use google

---

### Post by sumguy231 on 2007-08-22
> **mikewhatever said:**
> [http://www.adobe.com/products/flashplayer/productinfo/faq/](http://www.adobe.com/products/flashplayer/productinfo/faq/)

use google
Are you replying to me, or someone else? That page doesn't actually answer my question. I know what Google is, and I even double-checked Adobe's site before asking.

---

### Post by chriseo22 on 2007-08-23
I am currently using version 9,0,48,0 of Adobe flash player which was installed through Automatix.  I can watch fullscreen on both YouTube and Google Video, it just reopens it in a new window.  I was able to revert back by uninstalling the Beta and reinstalling it through Automatix, I just couldn't get the Beta to work.

Chris

---

### Post by aysiu on 2007-08-23
> **Kosimo said:**
> 
Somebody knows how to install it? I think you'd probably paste these commands in the terminal: ```
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
wget -c http://download.macromedia.com/pub/labs/flashplayer9_update/flashplayer9_install_linux_082207.tar.gz
tar -xvzf flashplayer9_install_linux_082207.tar.gz
cd install_flash_player_9_linux/
sudo ./flashplayer-installer
```

---

### Post by TeaSwigger on 2007-08-23
> **aysiu said:**
> I think you'd probably paste these commands in the terminal: ```
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
wget -c http://download.macromedia.com/pub/labs/flashplayer9_update/flashplayer9_install_linux_082207.tar.gz
tar -xvzf flashplayer9_install_linux_082207.tar.gz
cd install_flash_player_9_linux/
sudo ./flashplayer-installer
```

Thank you, aysiu. Your handy little code, as well as the new flash, worked perfectly :)

---

### Post by chrome307 on 2007-08-24
I'm stuck with the installation of this application ie

```



Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at http://www.adobe.com/support/flashplayer/

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 



```

I need to enter the path to install :confused:

---

### Post by tgrisier on 2007-08-24
Thanks for the help!  Worked like a charm.



> **aysiu said:**
> I think you'd probably paste these commands in the terminal: ```
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
wget -c http://download.macromedia.com/pub/labs/flashplayer9_update/flashplayer9_install_linux_082207.tar.gz
tar -xvzf flashplayer9_install_linux_082207.tar.gz
cd install_flash_player_9_linux/
sudo ./flashplayer-installer
```

---

### Post by Phurious on 2007-08-24
> **chrome307 said:**
> I'm stuck with the installation of this application ie

```



Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at http://www.adobe.com/support/flashplayer/

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 



```

I need to enter the path to install :confused:

/usr/lib/mozilla-firefox

---

### Post by chrome307 on 2007-08-24
**Thanks Phurious :)**

---

### Post by aysiu on 2007-08-24
Or /usr/lib/firefox

---

### Post by werewolfzx8 on 2007-12-14
Fullscreen always starts in a restored window, and I have to maximize it myself. Is this because I'm running Compiz-Fusion?

---

