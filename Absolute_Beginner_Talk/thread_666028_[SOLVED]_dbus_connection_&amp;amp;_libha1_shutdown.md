---
title: "[SOLVED] dbus_connection &amp;amp; libha1_shutdown failed"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Semong on 2008-01-12
Ok Im running Xubunutu 7.10 Gutsy.
Everytime I shut down or restart my computer I'm faced with an error message that dissappears so quickly I can barely read it all. Anyways I restarted a few times and wrote down what I could:


Network Manager: caught signal terminated
(then it displays some long number and something about a 'socket'

Network Manager: nm_ha1_deinit libha1_shutdown_failed

Network Manager: assertion_cddata_data->dbus_connection_failed

Network Manager: nm_dbus_signal_device_status_change
(it says this a few times oddly enough then continues shutting down)

I have no idea what this is or why its happening. I'm pretty sure its not supposed to be happening though because I used Ubuntu 7.04 for a few months on a friend of mines computer and there were no messages like this on shutdown. Any help or suggestions would be greatly appreciated.

---

### Post by p_quarles on 2008-01-12
I get similar shutdown messages on one of my computers. Unless there are problems with the network manager's functionality, I wouldn't worry about. 

I'm guessing (correct me if I'm wrong) that this is a laptop, and that the wifi card needs a restricted module. As a consequence of the fact that the driver is not open source, it's not communicating optimally with the kernel.

Again, unless there's a problem *aside* from the error messages, I wouldn't worry about it.

---

### Post by Semong on 2008-01-13
eh I should've said that my machine is a desktop ;). My Network Manager seems to be working fine but obviously something is wrong here and this error message bugs the hell out of me. Thanx for the quick reply..

---

### Post by p_quarles on 2008-01-13
> **Semong said:**
>  but obviously something is wrong here 
I disagree that this is obvious. Based on what you've said, I'd say that this is either a false alarm or a minor bug. Error messages are meant to be helpful when something *isn't *working. They sometimes show up when everything's working fine -- but that doesn't mean that anything's wrong.

---

### Post by Semong on 2008-01-13
I see your point. I would just really like to get this fixed (if it is indeed a problem) or find some way to make those messages dissappear. It couldnt be a restricted module because my hardware doesn't require any. Any help or suggestions would make my day a happy one.

---

### Post by Semong on 2008-01-13
bump

---

### Post by Semong on 2008-01-13
Would installing another network manager make any difference?

---

### Post by Semong on 2008-01-17
*sigh*

---

### Post by Semong on 2008-01-18
Well no thanks to any advice from anyone here I came up with the conclusion that the network-manager that comes along with Xubuntu 7.10 has a bug in it somewhere. To anyone else thats having this problem here's my quickfix:

```
sudo apt-get install ubuntu-desktop
sudo apt-get remove xubuntu-desktop xubuntu-artwork-usplash
sudo apt-get autoremove

sudo apt-get remove abiword abiword-common abiword-plugins brasero dbus-x11 gnumeric-common gnumeric-gtk gqview gtk2-engines-murrine gtk2-engines-xfce libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-common libgoffice-gtk-0-4 libgsf-gnome-1-114 libgtkmathview0c2a libjpeg-progs liblink-grammar4 libmodplug0c2 libmpcdec3 libots0 libpulse0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxine1 libxvmc1 link-grammar-dictionaries-en mousepad mozilla-thunderbird orage python-exo tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman thunderbird totem-xine vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
```

If you perhaps you think that your machine doesn't have enough resources to properly run Ubuntu but haven't tested that theory, I would suggest testing it now. My machine is fairly low-end and it runs ubuntu just fine. If your machine really can't handle it though switch over to Damn Small Linux, Puppy Linux or Fluxbuntu.	;-)

---

### Post by p_quarles on 2008-01-18
You could have tested that theory by simply installing and running the Gnome network manager by itself.

---

### Post by Semong on 2008-01-19
> You could have tested that theory by simply installing and running the Gnome network manager by itself.

Well yeah I thought of that but I've ran into quite a few bugs on Xubuntu and the best option for anyone, in my humble opinion, is to make the switch to Ubuntu 7.10 Gutsy Ribbon. I would put a 99.9% gauruntee that they will be releived and completely satisfied with Ubuntu 7.10 and that includes speed.

---

### Post by p_quarles on 2008-01-19
> **Semong said:**
> Well yeah I thought of that but I've ran into quite a few bugs on Xubuntu and the best option for anyone, in my humble opinion, is to make the switch to Ubuntu 7.10 Gutsy Ribbon. I would put a 99.9% gauruntee that they will be releived and completely satisfied with Ubuntu 7.10 and that includes speed.
Just for the record, the only difference between Ubuntu 7.10 and Xubuntu 7.10 is the desktop environment. The former runs Gnome, while the latter runs the slightly more lightweight Xfce desktop. Beneath the GUI, there is absolutely no difference between the two. 

So, while the bugs that you encountered in Xfce may have been solved by switching to Gnome, it's very unlikely that the majority of users will notice a difference -- positive or negative -- in doing the same.

---

### Post by Semong on 2008-01-19
hmm maybe your right about that. I spoke a little too soon and without really thinking it through. I have re-installed my xfce desktop to try and see what I can do about the bugs because I prefer it, oddly enough. Ubuntu is a bit slower and my graphics card doesn't support any special effects. Also using Gnome I couldn't switch between workspaces with my pointer which really, really bothered me. There were alot of other things about gnome that also bothered me which I don't have time to explain.

> You could have tested that theory by simply installing and running the Gnome network manager by itself.

Xfce and Gnome both use the same network manager so it obviously isn't the manager itself but something wrong with xfce perhaps.

---

