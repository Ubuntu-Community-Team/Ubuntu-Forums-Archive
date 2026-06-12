---
title: "Flash-player nonfree, vmware player install issue"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by dRock1286 on 2007-03-16
When ever I run the Add/Remove Applications to install or uninstall programs, it always tries to install/configrure (?) the flash-player nonfree and vmware player.  

I get this popup...always...

> E: vmware-player: subprocess pre-removal script returned error exit status 1


And this is what the terminal says...

> 
[FONT="System"][FONT="Arial"][FONT="System"]Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~edgy1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][/FONT][/FONT]


Help please...?

---

### Post by dRock1286 on 2007-03-16
I got the flashplayer to remove but not the vmware.  any ideas?

---

### Post by dRock1286 on 2007-03-17
If I can't remove it, can I just finish the configuring so it stops this crap?

---

### Post by DarkStarAeon on 2007-06-29
I've got the same issue on my laptop, it's really annoying. In the details terminal I see the same as you, and  I have to hit "y" to every question is asks, and it repeats the process twice, then finally it carries on with adding or removing programs, but once done I get a graphical error about the the dpkg thing every time.

---

