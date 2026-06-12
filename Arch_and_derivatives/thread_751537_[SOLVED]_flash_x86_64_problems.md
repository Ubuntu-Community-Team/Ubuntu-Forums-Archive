---
title: "[SOLVED] flash x86_64 problems"
date: 2008-04-10
forum: Arch and derivatives
---

### Post by chris200x9 on 2008-04-10
I'm following the wiki to gt flash but when I'm trying to install the nnspluginwrapper-flash the install flash tarball always fails a validity check???

---

### Post by Bliepo32 on 2008-04-10
So you tried
```

sudo apt-get install flashplugin-nonfree

```

?

---

### Post by chris200x9 on 2008-04-10
no, but I'm using arch so I have no apt-get

---

### Post by Gigamo on 2008-04-10
> **chris200x9 said:**
> no, but I'm using arch so I have no apt-get

Try editing the pkgbuild and removing the "md5sums" line.

---

### Post by chris200x9 on 2008-04-10
thanks that worked, but I still don't have flash installed, I ran
```
 nspluginwrapper -v -a -i
 
```

but I get 

```
 
[root@LinuxBox nspluginwrapper-flash]# nspluginwrapper -v -a -i
Auto-install plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Install plugin /usr/lib/mozilla/plugins/libflashplayer.so
  into /root/.mozilla/plugins/npwrapper.libflashplayer.so
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libnpsoplugin.so: wrong ELF class: ELFCLASS64
Auto-install plugins from /usr/lib/firefox/plugins
Looking for plugins in /usr/lib/firefox/plugins
*** NSPlugin Viewer  *** ERROR: /usr/lib/firefox/plugins/libnullplugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/firefox/plugins/libunixprintplugin.so: wrong ELF class: ELFCLASS64
Auto-install plugins from /root/.mozilla/plugins
Looking for plugins in /root/.mozilla/plugins
[root@LinuxBox nspluginwrapper-flash]# 

```


and when I shutdown my browser and restart it, I can't get flash.

---

### Post by fwojciec on 2008-04-10
Adobe released new version of flash, and the PKGBUILD for nspluginwrapper-flash hasn't been updated yet, it seems (it's flagged out of date -- I'd expect the maintainer to update it soon).  Maybe this is the source of the problems.

In either case, I'd suggest looking into setting up 32bit chroot rather than having to deal with lib32 packages -- it's more work at first but the end result is better, IMO.  This is what I use on my Arch64 system to run 32bit-only software.

Finally, if you don't want to deal with these sorts of issues the best thing is to install the 32bit version of Arch.  Despite popular myths to the contrary 64bit systems are *not* perceptibly faster than 32bit systems in general use -- except for specific tasks like multimedia encoding and such -- and tend to be more difficult to maintain.

---

### Post by K.Mandla on 2008-04-11
At the risk of sounding like a real elitist snot, I don't install Flash when I run Arch64. 

Hmm. I think that made me sound like a real elitist snot anyway. Sigh. :|

---

### Post by RedMist on 2008-04-11
Just download the new flashplayer from [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

then place the file in your extracted nspluginwrapper-flash folder. Now you need to edit the PKGBUILD file in order to change the MD5 sum. Scroll down until you see the MD5sums, there should be two, and change the 1st one. 
Do "md5sum install_flash_player_9_linux.tar.gz" in a terminal to get the correct sum. Replace and save.
That should do the trick. Hope this helps.

---

