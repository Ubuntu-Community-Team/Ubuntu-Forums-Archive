---
title: "Installation script"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Bingo Jesus on 2007-05-16
I've partioned my hard disc into two parts, one for /home to ease re installation problems. Recently I thought that I could speed up re installation even further by writing an installation script (~/start/start.sh) for running on first boot,

```
sudo apt-get update

sudo apt-get upgrade

sudo apt-get install -y mozilla-thunderbird gnubiff banshee gstreamer0.10-plugins-ugly-multiverse flashplugin-nonfree libxine1-ffmpeg gxine gtkpod ndiswrapper-utils-1.9 wifi-radar beagle

sudo apt-get remove network-manager

sudo echo 'blacklist bcm43xx' >> /etc/modprobe.d/blacklist

sudo echo 'ndiswrapper' >> /etc/modules

sudo rmmod bcm43xx

sudo ndiswrapper -i ~/start/bcmwl5.inf

sudo /usr/share/doc/libdvdread3/install-css.sh

sudo shutdown -r now
```

Now I've made it executable with chmod -x, but how do I actually run it from the terminal? Also, do I still need to add the drivers to ndiswrapper, or is that not needed as I'm preserving my home directory?

---

### Post by FuturePast on 2007-05-16
$ cd start
$ bash start.sh

or put #!/bin/bash as the first line of the script and then just run it itself 
$ cd start
$ ./start.sh

---

### Post by blazercist on 2007-05-16
to run the script in terminal simply open a terminal, cd to the directory containing your script and do ./script

---

### Post by vigleik on 2007-05-16
Did you try fwcutter instead of blacklisting bcm43xx and ndiswrapper? It works even better. (Search the forum for many howto's.)

---

### Post by Bingo Jesus on 2007-05-16
Thanks a lot, I knew there must be a simple answer.

EDIT: I had little success with fwcutter, I might try it again some time. But for now I think I'll leave things as they are.

---

