---
title: "visual effects on my inspiron"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by fetisha on 2008-03-28
I installed heron and they worked, so did my sound, suprisingly, but the wireless did not. So, not I've installed gutsy on my inspiron 1521 and the ristricted driver for my wireless worked fine and I fixed the audio. However, I noticed the visual effects weren't working (neither is the sleep/hibernate, but one thing at a time I suppose), so I went and tried to change them from none to normal and it gave me this message:
The Composite extension is not available.

Any suggestions?

---

### Post by jan quark on 2008-03-28
try this small guide
install the drivers via the restricted drivers manager if you have not done so yet

[http://ubuntuhelp.piranho.de/xserver.html](http://ubuntuhelp.piranho.de/xserver.html)

---

### Post by wolfen69 on 2008-03-28
from here [http://ubuntuforums.org/showthread.php?t=436110&page=2](http://ubuntuforums.org/showthread.php?t=436110&page=2)

"I have a Dell Optiplex 745 that has a ATI X1300 in it and I am running Gutsy 7.10.

I was also getting the Compsite Extention not available message.

I now have it working.

In order to get the desktop effects to work I first had to install the ATI driver using the Restricted Drivers Manager.

Then I had to install xserver-xgl using the Synaptic Package Manager located under System-->Administration-->Synaptic Package Manager. Just do a search for xserver-xgl in the Synaptic manager to find it.

While you are there you might want to install the compizconfig-settings-manager as well.

After those are installed reboot and then you should be able to select Extra in the Visual Effects tab under System-->Preferences-->Appearance.

Worked for me.

To run the CompizConfig Settings Manager, you just run /usr/bin/ccsm (I created a entry for it in the menus using the System-->Preferences -->Main Menu tool.

Hope that works for you."

---

