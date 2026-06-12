---
title: "No longer have Desktop Effects option in menu"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by dpatel on 2007-09-03
Hi - I enabled Desktop Effects and everything was working well. So then I installed Beryl but I found it didn't work properly (main problem: couldn't see top title bar).

So, I removed Beryl, Emerald, etc and wanted to revert to just using desktop effects as that seemed to work. But now Desktop Effects no longer appears in the menu list. In fact the menu shows Emerald Theme Manager (even though I've removed it).

How do I get Desktop Effects back?

PS: I have a feeling this may be to do with the fact I installed Compiz Fusion!

---

### Post by gOLdenHaWK3D on 2007-09-04
Goto System>Preferences>Main Menu.
Search for what you need and Checkmark the item you need to display in the MAin Menu.

---

### Post by dpatel on 2007-09-04
I've just tried that and it's not listed in there any more. I also tried revert to default and that didn't work.

---

### Post by afonic on 2007-09-04
Maybe you uninstalled compiz?

Try searching for compiz in Synaptic and installing it again.

---

### Post by dpatel on 2007-09-05
So, here's the latest in this story:

- I managed to get Desktop Effects back in the menu (found it in Synaptic).
- When I click on it now, it states not able to enable desktop effects (although it worked fine first time)!
- When I do glxinfo | grep direct I get error messages (sorry at work so can't post the output). Suffice it to say, it doesn't say 3D rendering: yes!
- I've tried looking in restricted drivers for NVIDIA drivers but it isn't there anymore (it was there when I first tried Desktop effects and that's how it started working).
- I have tried everything to install NVIDIA drivers (nvidia-glx, nvidia-glx-legacy, etc). None of them work (i.e. cannot now enable Desktop Effects); also, when I install these and restart X it causes X to crash and I have to do sudo dpkg-reconfigure... in safe mode to recover!!

Please help!!

---

### Post by overdrank on 2007-09-05
> **dpatel said:**
> So, here's the latest in this story:

- I managed to get Desktop Effects back in the menu (found it in Synaptic).
- When I click on it now, it states not able to enable desktop effects (although it worked fine first time)!
- When I do glxinfo | grep direct I get error messages (sorry at work so can't post the output). Suffice it to say, it doesn't say 3D rendering: yes!
- I've tried looking in restricted drivers for NVIDIA drivers but it isn't there anymore (it was there when I first tried Desktop effects and that's how it started working).
- I have tried everything to install NVIDIA drivers (nvidia-glx, nvidia-glx-legacy, etc). None of them work (i.e. cannot now enable Desktop Effects); also, when I install these and restart X it causes X to crash and I have to do sudo dpkg-reconfigure... in safe mode to recover!!

Please help!!

Hi you can try and reinstall restricted driver manager through synaptic manager.

---

### Post by dpatel on 2007-09-05
Hi overdrank - should have said: i tried that too! I just can't get it to show NVIDIA in the list anymore. Do I need to do a more system wide update/refresh to get this working again? Not sure where to go with this now!

---

### Post by overdrank on 2007-09-05
> **dpatel said:**
> Hi overdrank - should have said: i tried that too! I just can't get it to show NVIDIA in the list anymore. Do I need to do a more system wide update/refresh to get this working again? Not sure where to go with this now!

Well have you tried Envy script to install you drivers? And what is the model of the nvidia card?

---

### Post by dpatel on 2007-09-05
No, will try Envy tonight.

Don't laugh - it's an old MX200 32Mb - got it from a friend. Just wanted to get the eye candy working...

---

### Post by Hobo Joe on 2007-09-05
> **dpatel said:**
> No, will try Envy tonight.

Don't laugh - it's an old MX200 32Mb - got it from a friend. Just wanted to get the eye candy working...

That's probably the problem there. It's a biiiiig stretch to use a card like that for desktop effects.


But yes, you need to use Envy.

---

### Post by jvc26 on 2007-09-05
I'm impressed you even got desktop effects working, I haven't ever managed to get them working on an ancient TNT2 in one of my old boxes.
Il

---

### Post by rickycodie on 2007-09-05
part of installing fusion is uninstalling the compiz manager that comes with ubuntu, just so you know for the future. about beryl, do this

```
sudo gedit /etc/X11/xorg.conf
```

then in the devices section add this to the bottom

```
Option "AddARGBGLXVisuals" "true"
```

sOption "AddARGBGLXVisuals" "true"ave the changes and then press ctrl+alt+backspace, or reboot and you should have the tops of the bars back.

---

### Post by mysticmatrix on 2007-09-05
> **dpatel said:**
> Hi - I enabled Desktop Effects and everything was working well. So then I installed Beryl but I found it didn't work properly (main problem: couldn't see top title bar).

So, I removed Beryl, Emerald, etc and wanted to revert to just using desktop effects as that seemed to work. But now Desktop Effects no longer appears in the menu list. In fact the menu shows Emerald Theme Manager (even though I've removed it).

How do I get Desktop Effects back?

PS: I have a feeling this may be to do with the fact I installed Compiz Fusion!

Yes,standard procedure to install Compiz Fusion involves removing ubuntu-desktop and hence the desktop effects.
Try this: it will restore your system packages to back as Ubuntu wants

```
sudo apt-get install ubuntu-desktop 
```

---

### Post by dpatel on 2007-09-05
Out of curiosity - which one would you recommend - nothing too flash though. Or would recommend NVIDIA over ATI or vice versa?

EDIT: Oops - posted this before seeing the other responses. Thanks all for the great support! Still - anyone want to recommend a graphics card?

---

### Post by afonic on 2007-09-05
If you want to use Linux get an nVidia. :)

ATI drivers for Linux are pretty bad.

---

### Post by dpatel on 2007-09-05
A HUGE thanks to all. I now have my (measly) MX200 32Mb running Beryl with no noticeable (bit early to be sure but...) performance degradation! =D> Thanks again!

---

### Post by dpatel on 2007-09-06
Just to summarise what I did (maybe helpful to others):

My card is a NVIDIA GeForce2 MX200

Re-installed Desktop Effects using Synaptic. Then did:

```
sudo apt-get install ubuntu-desktop
``` This is just to ensure everything is up-to-date.

Used [[COLOR="Blue"]Envy[/COLOR]]("http://albertomilone.com/nvidia_scripts1.html") to install Nvidia drivers (this is a fantastic utility, by the way). Note: this installs restricted drivers.

Edited xorg.conf ```
sudo gedit /etc/X11/xorg.conf
```

Added Option "AddARGBGLXVisuals" "true" to Device section (this ensures you don't lose the top bar in your windows)
Added Option "AllowGLXWithComposite" "True" to Screen section (this is stop the black screen issue)

Ctrl-Alt-Bksp to restart X

Installed Beryl and Emerald Theme Manager

```
sudo apt-get install beryl beryl-manager emerald-themes
```

Start Beryl Manager
```
beryl-manager
```

Replace Windows manager with Beryl by:
Alt-F2 and type Beryl --replace in the box.

Job done...!!

PS: I have to say how fantastic Linux and Ubuntu is if you can get this running on my PC with quite an old graphics card like mine whereas Vista doesn't come close to this eye candy with top grade hardware!

---

### Post by rickycodie on 2007-09-06
congrats on getting it to work!

---

