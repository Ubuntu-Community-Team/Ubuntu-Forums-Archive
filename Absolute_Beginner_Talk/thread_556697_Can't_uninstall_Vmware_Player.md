---
title: "Can't uninstall Vmware Player"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by hotweiss on 2007-09-21
Ok I've tried all of the solutions on the internet with no luck. I'm one of the unlucky ones who have an Atheros wifi card which is not supported by VMWare now. The installation failed half way through and I could not uninstall it. Here's the error message I get when I try to uninstall it:
> 
Writing extended state information... Done
(Reading database ... 115900 files and directories currently installed.)
Removing vmware-player ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--purge):
 subprocess pre-removal script returned error exit status 1
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Any ideas?

---

### Post by SpiritIsReality on 2007-09-21
howdy
this any help
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22uninstall+vmware%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22uninstall+vmware%22&btnG=Google+Search&meta=)
[http://ubuntuforums.org/showthread.php?t=230566](http://ubuntuforums.org/showthread.php?t=230566)
oh, you said you tried all that, ..
you could try the find command, or the updatedb then slocate to see if there are any
vmware files on your partition(s)
for example
```
sudo find / -name vmware
```that didn't work
or 
```
sudo updatedb
``` then
```
slocate vmware
```
then delete them?
> me@p3:~$ sudo updatedb
Password:
me@p3:~$ slocate vmware
/usr/lib/xorg/modules/drivers/vmware_drv.so
/usr/share/doc/xserver-xorg-video-vmware
/usr/share/doc/xserver-xorg-video-vmware/copyright
/usr/share/doc/xserver-xorg-video-vmware/changelog.Debian.gz
/usr/share/app-install/desktop/vmware-player.desktop
/usr/share/app-install/desktop/vmware-server.desktop
/usr/share/app-install/icons/vmware-player.png
/usr/share/app-install/icons/_usr_share_pixmaps_vmware-player.png
/usr/share/app-install/icons/vmware-server.png
/usr/share/man/man4/vmware.4.gz
/var/lib/dpkg/info/xserver-xorg-video-vmware.list
/var/lib/dpkg/info/xserver-xorg-video-vmware.md5sums
but I checked in synaptic and I don't have vmware installed.

```
man rm
```
heard virtualbox is good. if it works, the atheros chip could be a blessing in disguise

do you know the terminal and linuxcommand.org stuff?

trails

---

### Post by hotweiss on 2007-09-21
Tried that and the other methods... Going to try Kubuntu now anyways.

PS-Ubuntu is awesome

---

### Post by SpiritIsReality on 2007-09-21
ya I like being able to choose between kubuntu and ubuntu at startup

---

### Post by SpiritIsReality on 2007-09-21
link to virtualbox if you decide to give it a try
[http://ubuntuforums.org/showthread.php?t=340113](http://ubuntuforums.org/showthread.php?t=340113)

trails

---

### Post by hotweiss on 2007-09-24
> **fmat said:**
> link to virtualbox if you decide to give it a try
[http://ubuntuforums.org/showthread.php?t=340113](http://ubuntuforums.org/showthread.php?t=340113)

trails

I'm trying Virtual Box now. I'll try it with all my hardware first and then if everything works, I'll stop dual booting.

EDIT: Dam, I can't eliminate my dual boot config because of my external NTFS hard drives... Since GNome doesn't support NTFS, I'll never be able to delete anything

---

### Post by SpiritIsReality on 2007-09-24
howdy
sorry I didn't catch you earlier.
I'm kind of new to this game.
glad to hear you got virtualbox workin'. way to go.
ya, networking is quite the science.
samba is still a four letter word to me.
I multiboot ubuntu, debian, and wxp.
I don't have enough memory on this rig to run virtualbox or the others as far as I know.
until I figure out how to do without the xp, I'll live with it.
I figure leavin it behind in degrees is better than where I was.
I don't seem to use it very much.
I'm looking forward to kickin' it out.

just on the other side of the rocks from you,
trails

---

