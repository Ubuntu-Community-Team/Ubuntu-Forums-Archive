---
title: "quick question about flash plugin"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by wasp on 2006-04-09
Ok, I saw I needed the flash plugin for some websites to display correctly, so I entered "sudo apt-get install flashplugin-nonfree" in the command line. Tried Firefox again, and flash didn't seem to be installed. Ran sudo again. It said flashplugin-nonfree is the newest version. Tried actually going to Macromedia's site and downloading it there, but the directions it gave after downloading the file didn't seem to work, either.

Anyone have any ideas?

---

### Post by trent dillman on 2006-04-09
Open firefox and visit ```
about:plugins
``` and see if it's listed....

also, the flash you are trying to watch might be version 8. If so, you may be SOL...

---

### Post by Sef on 2006-04-09
From Restricted Formats:

> or Ubuntu 5.10 (Breezy Badger)

    *

  sudo apt-get install flashplayer-mozilla
  



---

### Post by wasp on 2006-04-09
[QUOTE=trent dillman]Open firefox and visit ```
about:plugins
``` and see if it's listed....

also, the flash you are trying to watch might be version 8. If so, you may be SOL...[/QUOTE]

Shockwave Flash is listed. Might be version 8 stuff I suppose, but any sites with flash don't seem work.

---

### Post by Perfect Storm on 2006-04-09
[QUOTE=wasp]Ok, I saw I needed the flash plugin for some websites to display correctly, so I entered "sudo apt-get install flashplugin-nonfree" in the command line. Tried Firefox again, and flash didn't seem to be installed. Ran sudo again. It said flashplugin-nonfree is the newest version. Tried actually going to Macromedia's site and downloading it there, but the directions it gave after downloading the file didn't seem to work, either.

Anyone have any ideas?[/QUOTE]

The flash file from macromedia, for firefox use path **/usr/lib/mozilla-firefox** if you use the firefox which comes with ubuntu.

---

### Post by wasp on 2006-04-09
[QUOTE=Artificial Intelligence]The flash file from macromedia, for firefox use path **/usr/lib/mozilla-firefox** if you use the firefox which comes with ubuntu.[/QUOTE]

Both the flashplayer.xpt and libflashplayer.so files are there. It seems like it should be installed. It just doesn't work. :confused:

---

### Post by Perfect Storm on 2006-04-09
Just to rule it the option out: You ran the script install (sudo sh flashplayer-installer) and installed the x11 gsfonts?

---

### Post by trent dillman on 2006-04-09
Do you by any chance have the NoScript or FlashBlock extensions installed?

My guess is Flash 8, but maybe we're overlooking something...

Also, go in Synaptic and search for 'swf-' and see what's there....

---

### Post by wasp on 2006-04-09
[QUOTE=Artificial Intelligence]Just to rule it the option out: You ran the script install (sudo sh flashplayer-installer) and installed the x11 gsfonts?[/QUOTE]

Umm...no. I just ran "sudo apt-get install flashplugin-nonfree". It seemed to install, and firefox says it's installed in about : plugins. I could run the script install if that might solve the problem...I'm not even sure what x11 gsfonts are. (excuse my noobishness) If it's a type of font, I installed everything that came in the default Ubuntu installation.

---

### Post by Perfect Storm on 2006-04-09
Uninstall the previous flash first.

Download flash here to desektop: [http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

```
cd Desktop
tar zxvf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
sudo sh flashplayer-installer
sudo apt-get install gsfonts-x11
sudo fc-cache -f -v

```

---

### Post by wasp on 2006-04-09
[QUOTE=trent dillman]Do you by any chance have the NoScript or FlashBlock extensions installed?

My guess is Flash 8, but maybe we're overlooking something...

Also, go in Synaptic and search for 'swf-' and see what's there....[/QUOTE]

No, I didn't install those extensions. I just installed Adblock. Synaptic lists swf-player, and the "apply" is greyed out, so I assumed it's installed.

Edit:

Meh, the greyed out "apply" doesn't mean what I thought it did.

---

### Post by aysiu on 2006-04-09
Make sure **obj-tabs** isn't checked in your Adblock Options.

---

### Post by wasp on 2006-04-09
Ok, I'm not even sure what did it, but after checking and following the advice in the thread, it seems like flash is working now. Thanks everyone for the help. :)

---

