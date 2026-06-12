---
title: "[SOLVED] Need Urgent Help"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by gverrilla on 2008-04-12
I have installed some updates,and now my mouse pointer is still in the middle of the screen and I can't move it
I can still CLICK it,but not move it
need some URGENT help please

---

### Post by Diabolis on 2008-04-12
Restart xserver? ctrl + alt + backspace That will close all your apps and log you out, so you can log in again with a new xsession.

---

### Post by gverrilla on 2008-04-12
no,it is still not working :/

---

### Post by gverrilla on 2008-04-12
I had already restarted..
It seems the update ****** up with my mouse driver
what to do :/ :???

---

### Post by Diabolis on 2008-04-12
mmm go synaptic->edit->fix broken packages, if you can.

or

 Reconfigure xserver, that will also reconfigure your mouse.
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by gverrilla on 2008-04-12
I tried both of those,and it still not working
already restarted to try :/
that dpkg thing is for the keyboard,isn't it ?

---

### Post by Diabolis on 2008-04-12
Yeah, type the command in a terminal.

---

### Post by gverrilla on 2008-04-12
it didn't work :/

---

### Post by Diabolis on 2008-04-12
What was the update? maybe you can remove it and check if that gives you your mouse back. What I would try next, is to check synaptic for mouse drivers.

---

### Post by gverrilla on 2008-04-12
it was the normal system update :/
and I can't do it on synaptic : I don't know how :(

---

### Post by gverrilla on 2008-04-12
how can I remove updates?
thank you

---

### Post by Diabolis on 2008-04-12
Just open synaptic, you can navigate through its controls with tab and direction arrows. Do a search for mouse drivers or something like that, if you find a package that seems like the right one, select it with the arrows and press the space bar to mark it for installation.

The only way I know to downgrade an application is to remove it and install a older version.

---

### Post by gverrilla on 2008-04-12
I can't find any package that seems the right one :/
is there any hardcore solution?like some restoring or something?
cheers

---

### Post by Diabolis on 2008-04-12
I searched synaptic with "mouse driver", what I have installed is:

xserver-xorg-input-evdev
xserver-xorg-input-mouse
xserver-xorg-input-synaptics

The ones that are not installed and I would go for if I had your problem are:

xserver-xorg-input-magellan
xserver-xorg-input-vmmouse
libsdl1.2debian-all

I hope that helps.

---

### Post by kerry_s on 2008-04-12
open synaptic, click> file> history to see what was updated.

---

### Post by Diabolis on 2008-04-12
I didn't know about that feature in synaptic, I usually use the terminal. Its really cool, I just discovered that I've been running this ubuntu installation since november 2007 which is the longest I've had one. I usually wreck them.

---

### Post by gverrilla on 2008-04-12
well..now nothing is working on my mouse..
not even the scroll or the buttons :/
I tried to reinstall all of those packages :/

---

### Post by Diabolis on 2008-04-12
also downgraded/removed the ones that were updated before your mouse stopped working?

---

### Post by gverrilla on 2008-04-12
I'm a real ubuntu/linux rookie
and it seems I have made some real bad stuff for my machine
can anyone give me some more specific lines to fix this please?

I don't know exactly how to downgrade
should I remove (remove completely?) them all?

:((((((

---

### Post by gverrilla on 2008-04-12
well..I can't use the history (synaptics) without the mouse or without specific search keywords
and I don't know what caused the problem
:(*(

---

### Post by Diabolis on 2008-04-12
If wrecking the system is not a issue, just experiment. You'll learn a lot.

As said above, go to synaptic->file->history

see the last update, it will tell you which packages where updated.

So remove those packages.
```
sudo apt-get remove *name of the package*
```

---

### Post by Diabolis on 2008-04-12
The info displayed here: **synaptic->file->history** is stored in a text file inside ubuntu. You can read any file from the terminal.

type:
```
 cat /var/log/dpkg.log 
```

Updates are ordered by date and time, so check the lines that match with your last update.

---

### Post by kerry_s on 2008-04-12
okay, i better tell you how to control your mouse with the keyboard to help you along. :)

press and hold shift+ctrl+numlock you should hear a beep, that means keyboard mouse control is on.(you may not hear a beep, it doesn't beep on my laptop)

use the #'s 7,8,9,4,6,1,2,3 to move the mouse direction on the number pad.
/,*,- are your three mouse buttons, pick the mouse click you want, 5 clicks it

that should be enough to get you moving around, so i'll skip the other controls.

you don't have a extra mouse you can try?

---

### Post by gverrilla on 2008-04-13
wow,that keyboard-mouse-controlling made things much easier,thank you!
for the mouse problem itself,I checked the dpkg log,and these are the lines I have found :
I tried to check the packages listed above,but none of them could I relate to mouse driver nor hardware.
maybe you guys can help?

very thankful ;)

```
2008-04-12 15:31:32 startup archives unpack
2008-04-12 15:31:43 upgrade initramfs-tools 0.85eubuntu34 0.85eubuntu36
2008-04-12 15:31:43 status half-configured initramfs-tools 0.85eubuntu34
2008-04-12 15:31:43 status unpacked initramfs-tools 0.85eubuntu34
2008-04-12 15:31:43 status half-installed initramfs-tools 0.85eubuntu34
2008-04-12 15:31:43 status half-installed initramfs-tools 0.85eubuntu34
2008-04-12 15:31:43 status unpacked initramfs-tools 0.85eubuntu36
2008-04-12 15:31:43 status unpacked initramfs-tools 0.85eubuntu36
2008-04-12 15:31:44 upgrade libvolume-id0 117-4ubuntu2 117-8
2008-04-12 15:31:44 status half-configured libvolume-id0 117-4ubuntu2
2008-04-12 15:31:44 status unpacked libvolume-id0 117-4ubuntu2
2008-04-12 15:31:44 status half-installed libvolume-id0 117-4ubuntu2
2008-04-12 15:31:44 status half-installed libvolume-id0 117-4ubuntu2
2008-04-12 15:31:44 status unpacked libvolume-id0 117-8
2008-04-12 15:31:44 status unpacked libvolume-id0 117-8
2008-04-12 15:31:44 upgrade grub 0.97-29ubuntu20 0.97-29ubuntu21
2008-04-12 15:31:44 status half-configured grub 0.97-29ubuntu20
2008-04-12 15:31:44 status unpacked grub 0.97-29ubuntu20
2008-04-12 15:31:44 status half-installed grub 0.97-29ubuntu20
2008-04-12 15:31:44 status half-installed grub 0.97-29ubuntu20
2008-04-12 15:31:44 status unpacked grub 0.97-29ubuntu21
2008-04-12 15:31:44 status unpacked grub 0.97-29ubuntu21
2008-04-12 15:31:45 startup packages remove
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 remove volumeid 117-4ubuntu2 117-4ubuntu2
2008-04-12 15:31:45 status half-configured volumeid 117-4ubuntu2
2008-04-12 15:31:45 status half-installed volumeid 117-4ubuntu2
2008-04-12 15:31:45 status config-files volumeid 117-4ubuntu2
2008-04-12 15:31:45 status config-files volumeid 117-4ubuntu2
2008-04-12 15:31:45 status config-files volumeid 117-4ubuntu2
2008-04-12 15:31:45 status not-installed volumeid <none>
2008-04-12 15:31:46 startup archives unpack
2008-04-12 15:31:46 upgrade udev 117-4ubuntu2 117-8
2008-04-12 15:31:46 status half-configured udev 117-4ubuntu2
2008-04-12 15:31:46 status unpacked udev 117-4ubuntu2
2008-04-12 15:31:46 status half-installed udev 117-4ubuntu2
2008-04-12 15:31:47 status half-installed udev 117-4ubuntu2
2008-04-12 15:31:47 status unpacked udev 117-8
2008-04-12 15:31:47 status unpacked udev 117-8
2008-04-12 15:31:47 upgrade upstart-compat-sysv 0.3.9-1 0.3.9-2
2008-04-12 15:31:47 status half-configured upstart-compat-sysv 0.3.9-1
2008-04-12 15:31:47 status unpacked upstart-compat-sysv 0.3.9-1
2008-04-12 15:31:47 status half-installed upstart-compat-sysv 0.3.9-1
2008-04-12 15:31:47 status half-installed upstart-compat-sysv 0.3.9-1
2008-04-12 15:31:47 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:31:47 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:31:47 upgrade upstart-logd 0.3.9-1 0.3.9-2
2008-04-12 15:31:47 status half-configured upstart-logd 0.3.9-1
2008-04-12 15:31:47 status unpacked upstart-logd 0.3.9-1
2008-04-12 15:31:47 status half-installed upstart-logd 0.3.9-1
2008-04-12 15:31:47 status half-installed upstart-logd 0.3.9-1
2008-04-12 15:31:47 status unpacked upstart-logd 0.3.9-2
2008-04-12 15:31:47 status unpacked upstart-logd 0.3.9-2
2008-04-12 15:31:47 upgrade upstart 0.3.9-1 0.3.9-2
2008-04-12 15:31:47 status half-configured upstart 0.3.9-1
2008-04-12 15:31:47 status unpacked upstart 0.3.9-1
2008-04-12 15:31:47 status half-installed upstart 0.3.9-1
2008-04-12 15:31:48 status half-installed upstart 0.3.9-1
2008-04-12 15:31:48 status unpacked upstart 0.3.9-2
2008-04-12 15:31:48 status unpacked upstart 0.3.9-2
2008-04-12 15:31:48 install linux-image-2.6.24-16-generic <none> 2.6.24-16.30
2008-04-12 15:31:48 status half-installed linux-image-2.6.24-16-generic 2.6.24-16.30
2008-04-12 15:31:59 status unpacked linux-image-2.6.24-16-generic 2.6.24-16.30
2008-04-12 15:31:59 status unpacked linux-image-2.6.24-16-generic 2.6.24-16.30
2008-04-12 15:31:59 install linux-ubuntu-modules-2.6.24-16-generic <none> 2.6.24-16.22
2008-04-12 15:31:59 status half-installed linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.22
2008-04-12 15:32:02 status unpacked linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.22
2008-04-12 15:32:02 status unpacked linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.22
2008-04-12 15:32:02 upgrade startup-tasks 0.3.9-1 0.3.9-2
2008-04-12 15:32:02 status half-configured startup-tasks 0.3.9-1
2008-04-12 15:32:02 status unpacked startup-tasks 0.3.9-1
2008-04-12 15:32:02 status half-installed startup-tasks 0.3.9-1
2008-04-12 15:32:02 status half-installed startup-tasks 0.3.9-1
2008-04-12 15:32:02 status unpacked startup-tasks 0.3.9-2
2008-04-12 15:32:02 status unpacked startup-tasks 0.3.9-2
2008-04-12 15:32:02 upgrade system-services 0.3.9-1 0.3.9-2
2008-04-12 15:32:02 status half-configured system-services 0.3.9-1
2008-04-12 15:32:02 status unpacked system-services 0.3.9-1
2008-04-12 15:32:02 status half-installed system-services 0.3.9-1
2008-04-12 15:32:02 status half-installed system-services 0.3.9-1
2008-04-12 15:32:02 status unpacked system-services 0.3.9-2
2008-04-12 15:32:02 status unpacked system-services 0.3.9-2
2008-04-12 15:32:02 upgrade command-not-found-data 0.2.16ubuntu1 0.2.17ubuntu1
2008-04-12 15:32:02 status half-configured command-not-found-data 0.2.16ubuntu1
2008-04-12 15:32:02 status unpacked command-not-found-data 0.2.16ubuntu1
2008-04-12 15:32:02 status half-installed command-not-found-data 0.2.16ubuntu1
2008-04-12 15:32:03 status half-installed command-not-found-data 0.2.16ubuntu1
2008-04-12 15:32:03 status unpacked command-not-found-data 0.2.17ubuntu1
2008-04-12 15:32:03 status unpacked command-not-found-data 0.2.17ubuntu1
2008-04-12 15:32:03 upgrade command-not-found 0.2.16ubuntu1 0.2.17ubuntu1
2008-04-12 15:32:03 status half-configured command-not-found 0.2.16ubuntu1
2008-04-12 15:32:03 status unpacked command-not-found 0.2.16ubuntu1
2008-04-12 15:32:03 status half-installed command-not-found 0.2.16ubuntu1
2008-04-12 15:32:03 status half-installed command-not-found 0.2.16ubuntu1
2008-04-12 15:32:03 status unpacked command-not-found 0.2.17ubuntu1
2008-04-12 15:32:03 status unpacked command-not-found 0.2.17ubuntu1
2008-04-12 15:32:03 upgrade friendly-recovery 0.0+bzr20070723 0.1
2008-04-12 15:32:03 status half-configured friendly-recovery 0.0+bzr20070723
2008-04-12 15:32:03 status unpacked friendly-recovery 0.0+bzr20070723
2008-04-12 15:32:03 status half-installed friendly-recovery 0.0+bzr20070723
2008-04-12 15:32:03 status half-installed friendly-recovery 0.0+bzr20070723
2008-04-12 15:32:03 status unpacked friendly-recovery 0.1
2008-04-12 15:32:03 status unpacked friendly-recovery 0.1
2008-04-12 15:32:03 upgrade rsync 2.6.9-6ubuntu1 2.6.9-6ubuntu2
2008-04-12 15:32:03 status half-configured rsync 2.6.9-6ubuntu1
2008-04-12 15:32:03 status unpacked rsync 2.6.9-6ubuntu1
2008-04-12 15:32:03 status half-installed rsync 2.6.9-6ubuntu1
2008-04-12 15:32:04 status half-installed rsync 2.6.9-6ubuntu1
2008-04-12 15:32:04 status unpacked rsync 2.6.9-6ubuntu2
2008-04-12 15:32:04 status unpacked rsync 2.6.9-6ubuntu2
2008-04-12 15:32:04 upgrade libcairo2 1.5.20-0ubuntu1 1.6.0-0ubuntu1
2008-04-12 15:32:04 status half-configured libcairo2 1.5.20-0ubuntu1
2008-04-12 15:32:04 status unpacked libcairo2 1.5.20-0ubuntu1
2008-04-12 15:32:04 status half-installed libcairo2 1.5.20-0ubuntu1
2008-04-12 15:32:04 status half-installed libcairo2 1.5.20-0ubuntu1
2008-04-12 15:32:04 status unpacked libcairo2 1.6.0-0ubuntu1
2008-04-12 15:32:04 status unpacked libcairo2 1.6.0-0ubuntu1
2008-04-12 15:32:04 upgrade synaptic 0.61ubuntu8 0.61ubuntu9
2008-04-12 15:32:04 status half-configured synaptic 0.61ubuntu8
2008-04-12 15:32:04 status unpacked synaptic 0.61ubuntu8
2008-04-12 15:32:04 status half-installed synaptic 0.61ubuntu8
2008-04-12 15:32:04 status half-installed synaptic 0.61ubuntu8
2008-04-12 15:32:10 status unpacked synaptic 0.61ubuntu9
2008-04-12 15:32:10 status unpacked synaptic 0.61ubuntu9
2008-04-12 15:32:10 upgrade update-manager 1:0.87.16 1:0.87.17
2008-04-12 15:32:10 status half-configured update-manager 1:0.87.16
2008-04-12 15:32:20 status unpacked update-manager 1:0.87.16
2008-04-12 15:32:21 status half-installed update-manager 1:0.87.16
2008-04-12 15:32:21 status half-installed update-manager 1:0.87.16
2008-04-12 15:32:22 status unpacked update-manager 1:0.87.17
2008-04-12 15:32:22 status unpacked update-manager 1:0.87.17
2008-04-12 15:32:22 upgrade update-manager-core 1:0.87.16 1:0.87.17
2008-04-12 15:32:22 status half-configured update-manager-core 1:0.87.16
2008-04-12 15:32:22 status unpacked update-manager-core 1:0.87.16
2008-04-12 15:32:22 status half-installed update-manager-core 1:0.87.16
2008-04-12 15:32:22 status half-installed update-manager-core 1:0.87.16
2008-04-12 15:32:22 status unpacked update-manager-core 1:0.87.17
2008-04-12 15:32:22 status unpacked update-manager-core 1:0.87.17
2008-04-12 15:32:22 upgrade libktnef1 4:3.5.9-0ubuntu2 4:3.5.9-0ubuntu3
2008-04-12 15:32:22 status half-configured libktnef1 4:3.5.9-0ubuntu2
2008-04-12 15:32:22 status unpacked libktnef1 4:3.5.9-0ubuntu2
2008-04-12 15:32:22 status half-installed libktnef1 4:3.5.9-0ubuntu2
2008-04-12 15:32:22 status half-installed libktnef1 4:3.5.9-0ubuntu2
2008-04-12 15:32:22 status unpacked libktnef1 4:3.5.9-0ubuntu3
2008-04-12 15:32:22 status unpacked libktnef1 4:3.5.9-0ubuntu3
2008-04-12 15:32:22 upgrade libkdepim1a 4:3.5.9-0ubuntu2 4:3.5.9-0ubuntu3
2008-04-12 15:32:22 status half-configured libkdepim1a 4:3.5.9-0ubuntu2
2008-04-12 15:32:22 status unpacked libkdepim1a 4:3.5.9-0ubuntu2
2008-04-12 15:32:22 status half-installed libkdepim1a 4:3.5.9-0ubuntu2
2008-04-12 15:32:22 status half-installed libkdepim1a 4:3.5.9-0ubuntu2
2008-04-12 15:32:23 status unpacked libkdepim1a 4:3.5.9-0ubuntu3
2008-04-12 15:32:23 status unpacked libkdepim1a 4:3.5.9-0ubuntu3
2008-04-12 15:32:23 upgrade libkcal2b 4:3.5.9-0ubuntu2 4:3.5.9-0ubuntu3
2008-04-12 15:32:23 status half-configured libkcal2b 4:3.5.9-0ubuntu2
2008-04-12 15:32:23 status unpacked libkcal2b 4:3.5.9-0ubuntu2
2008-04-12 15:32:23 status half-installed libkcal2b 4:3.5.9-0ubuntu2
2008-04-12 15:32:23 status half-installed libkcal2b 4:3.5.9-0ubuntu2
2008-04-12 15:32:23 status unpacked libkcal2b 4:3.5.9-0ubuntu3
2008-04-12 15:32:23 status unpacked libkcal2b 4:3.5.9-0ubuntu3
2008-04-12 15:32:23 upgrade akregator 4:3.5.9-0ubuntu2 4:3.5.9-0ubuntu3
2008-04-12 15:32:23 status half-configured akregator 4:3.5.9-0ubuntu2
2008-04-12 15:32:23 status unpacked akregator 4:3.5.9-0ubuntu2
2008-04-12 15:32:23 status half-installed akregator 4:3.5.9-0ubuntu2
2008-04-12 15:32:23 status half-installed akregator 4:3.5.9-0ubuntu2
2008-04-12 15:32:24 status unpacked akregator 4:3.5.9-0ubuntu3
2008-04-12 15:32:24 status unpacked akregator 4:3.5.9-0ubuntu3
2008-04-12 15:32:24 upgrade amarok-xine 2:1.4.9-0ubuntu1 2:1.4.9.1-0ubuntu1
2008-04-12 15:32:24 status half-configured amarok-xine 2:1.4.9-0ubuntu1
2008-04-12 15:32:24 status unpacked amarok-xine 2:1.4.9-0ubuntu1
2008-04-12 15:32:24 status half-installed amarok-xine 2:1.4.9-0ubuntu1
2008-04-12 15:32:24 status half-installed amarok-xine 2:1.4.9-0ubuntu1
2008-04-12 15:32:24 status unpacked amarok-xine 2:1.4.9.1-0ubuntu1
2008-04-12 15:32:24 status unpacked amarok-xine 2:1.4.9.1-0ubuntu1
2008-04-12 15:32:24 upgrade libmtp7 0.2.6.1-1 0.2.6.1-2ubuntu1
2008-04-12 15:32:24 status half-configured libmtp7 0.2.6.1-1
2008-04-12 15:32:24 status unpacked libmtp7 0.2.6.1-1
2008-04-12 15:32:24 status half-installed libmtp7 0.2.6.1-1
2008-04-12 15:32:25 status half-installed libmtp7 0.2.6.1-1
2008-04-12 15:32:26 status unpacked libmtp7 0.2.6.1-2ubuntu1
2008-04-12 15:32:26 status unpacked libmtp7 0.2.6.1-2ubuntu1
2008-04-12 15:32:27 upgrade amarok 2:1.4.9-0ubuntu1 2:1.4.9.1-0ubuntu1
2008-04-12 15:32:27 status half-configured amarok 2:1.4.9-0ubuntu1
2008-04-12 15:32:27 status unpacked amarok 2:1.4.9-0ubuntu1
2008-04-12 15:32:27 status half-installed amarok 2:1.4.9-0ubuntu1
2008-04-12 15:32:28 status half-installed amarok 2:1.4.9-0ubuntu1
2008-04-12 15:32:29 status unpacked amarok 2:1.4.9.1-0ubuntu1
2008-04-12 15:32:29 status unpacked amarok 2:1.4.9.1-0ubuntu1
2008-04-12 15:32:29 upgrade gnome-app-install 0.5.2.6-0ubuntu1 0.5.2.7-0ubuntu1
2008-04-12 15:32:29 status half-configured gnome-app-install 0.5.2.6-0ubuntu1
2008-04-12 15:32:37 status unpacked gnome-app-install 0.5.2.6-0ubuntu1
2008-04-12 15:32:38 status half-installed gnome-app-install 0.5.2.6-0ubuntu1
2008-04-12 15:32:39 status half-installed gnome-app-install 0.5.2.6-0ubuntu1
2008-04-12 15:32:39 status unpacked gnome-app-install 0.5.2.7-0ubuntu1
2008-04-12 15:32:39 status unpacked gnome-app-install 0.5.2.7-0ubuntu1
2008-04-12 15:32:39 upgrade apturl 0.2.0ubuntu1 0.2.1ubuntu1
2008-04-12 15:32:39 status half-configured apturl 0.2.0ubuntu1
2008-04-12 15:32:47 status unpacked apturl 0.2.0ubuntu1
2008-04-12 15:32:48 status half-installed apturl 0.2.0ubuntu1
2008-04-12 15:32:48 status half-installed apturl 0.2.0ubuntu1
2008-04-12 15:32:48 status unpacked apturl 0.2.1ubuntu1
2008-04-12 15:32:48 status unpacked apturl 0.2.1ubuntu1
2008-04-12 15:32:48 upgrade compiz-gnome 1:0.7.2-0ubuntu2 1:0.7.4-0ubuntu4
2008-04-12 15:32:48 status half-configured compiz-gnome 1:0.7.2-0ubuntu2
2008-04-12 15:32:58 status unpacked compiz-gnome 1:0.7.2-0ubuntu2
2008-04-12 15:32:59 status half-installed compiz-gnome 1:0.7.2-0ubuntu2
2008-04-12 15:32:59 status half-installed compiz-gnome 1:0.7.2-0ubuntu2
2008-04-12 15:32:59 status unpacked compiz-gnome 1:0.7.4-0ubuntu4
2008-04-12 15:32:59 status unpacked compiz-gnome 1:0.7.4-0ubuntu4
2008-04-12 15:33:00 upgrade compiz-plugins 1:0.7.2-0ubuntu2 1:0.7.4-0ubuntu4
2008-04-12 15:33:00 status half-configured compiz-plugins 1:0.7.2-0ubuntu2
2008-04-12 15:33:00 status unpacked compiz-plugins 1:0.7.2-0ubuntu2
2008-04-12 15:33:00 status half-installed compiz-plugins 1:0.7.2-0ubuntu2
2008-04-12 15:33:00 status half-installed compiz-plugins 1:0.7.2-0ubuntu2
2008-04-12 15:33:00 status unpacked compiz-plugins 1:0.7.4-0ubuntu4
2008-04-12 15:33:00 status unpacked compiz-plugins 1:0.7.4-0ubuntu4
2008-04-12 15:33:00 upgrade libcompizconfig0 0.7.2-0ubuntu1 0.7.4-0ubuntu1
2008-04-12 15:33:00 status half-configured libcompizconfig0 0.7.2-0ubuntu1
2008-04-12 15:33:00 status unpacked libcompizconfig0 0.7.2-0ubuntu1
2008-04-12 15:33:00 status half-installed libcompizconfig0 0.7.2-0ubuntu1
2008-04-12 15:33:00 status half-installed libcompizconfig0 0.7.2-0ubuntu1
2008-04-12 15:33:00 status unpacked libcompizconfig0 0.7.4-0ubuntu1
2008-04-12 15:33:00 status unpacked libcompizconfig0 0.7.4-0ubuntu1
2008-04-12 15:33:00 upgrade compiz-core 1:0.7.2-0ubuntu2 1:0.7.4-0ubuntu4
2008-04-12 15:33:00 status half-configured compiz-core 1:0.7.2-0ubuntu2
2008-04-12 15:33:00 status unpacked compiz-core 1:0.7.2-0ubuntu2
2008-04-12 15:33:00 status half-installed compiz-core 1:0.7.2-0ubuntu2
2008-04-12 15:33:00 status half-installed compiz-core 1:0.7.2-0ubuntu2
2008-04-12 15:33:00 status unpacked compiz-core 1:0.7.4-0ubuntu4
2008-04-12 15:33:00 status unpacked compiz-core 1:0.7.4-0ubuntu4
2008-04-12 15:33:00 upgrade libdecoration0 1:0.7.2-0ubuntu2 1:0.7.4-0ubuntu4
2008-04-12 15:33:00 status half-configured libdecoration0 1:0.7.2-0ubuntu2
2008-04-12 15:33:00 status unpacked libdecoration0 1:0.7.2-0ubuntu2
2008-04-12 15:33:00 status half-installed libdecoration0 1:0.7.2-0ubuntu2
2008-04-12 15:33:00 status half-installed libdecoration0 1:0.7.2-0ubuntu2
2008-04-12 15:33:00 status unpacked libdecoration0 1:0.7.4-0ubuntu4
2008-04-12 15:33:00 status unpacked libdecoration0 1:0.7.4-0ubuntu4
2008-04-12 15:33:00 upgrade compizconfig-backend-gconf 0.7.2-0ubuntu1 0.7.4-0ubuntu1
2008-04-12 15:33:00 status half-configured compizconfig-backend-gconf 0.7.2-0ubuntu1
2008-04-12 15:33:00 status unpacked compizconfig-backend-gconf 0.7.2-0ubuntu1
2008-04-12 15:33:00 status half-installed compizconfig-backend-gconf 0.7.2-0ubuntu1
2008-04-12 15:33:00 status half-installed compizconfig-backend-gconf 0.7.2-0ubuntu1
2008-04-12 15:33:00 status unpacked compizconfig-backend-gconf 0.7.4-0ubuntu1
2008-04-12 15:33:00 status unpacked compizconfig-backend-gconf 0.7.4-0ubuntu1
2008-04-12 15:33:00 upgrade compiz-fusion-plugins-extra 0.7.2-0ubuntu1 0.7.4-0ubuntu1
2008-04-12 15:33:00 status half-configured compiz-fusion-plugins-extra 0.7.2-0ubuntu1
2008-04-12 15:33:08 status unpacked compiz-fusion-plugins-extra 0.7.2-0ubuntu1
2008-04-12 15:33:09 status half-installed compiz-fusion-plugins-extra 0.7.2-0ubuntu1
2008-04-12 15:33:10 status half-installed compiz-fusion-plugins-extra 0.7.2-0ubuntu1
2008-04-12 15:33:10 status unpacked compiz-fusion-plugins-extra 0.7.4-0ubuntu1
2008-04-12 15:33:10 status unpacked compiz-fusion-plugins-extra 0.7.4-0ubuntu1
2008-04-12 15:33:10 upgrade compiz-fusion-plugins-main 0.7.2-0ubuntu2 0.7.4-0ubuntu3
2008-04-12 15:33:10 status half-configured compiz-fusion-plugins-main 0.7.2-0ubuntu2
2008-04-12 15:33:18 status unpacked compiz-fusion-plugins-main 0.7.2-0ubuntu2
2008-04-12 15:33:20 status half-installed compiz-fusion-plugins-main 0.7.2-0ubuntu2
2008-04-12 15:33:20 status half-installed compiz-fusion-plugins-main 0.7.2-0ubuntu2
2008-04-12 15:33:20 status unpacked compiz-fusion-plugins-main 0.7.4-0ubuntu3
2008-04-12 15:33:20 status unpacked compiz-fusion-plugins-main 0.7.4-0ubuntu3
2008-04-12 15:33:20 upgrade compiz 1:0.7.2-0ubuntu2 1:0.7.4-0ubuntu4
2008-04-12 15:33:20 status half-configured compiz 1:0.7.2-0ubuntu2
2008-04-12 15:33:20 status unpacked compiz 1:0.7.2-0ubuntu2
2008-04-12 15:33:20 status half-installed compiz 1:0.7.2-0ubuntu2
2008-04-12 15:33:20 status half-installed compiz 1:0.7.2-0ubuntu2
2008-04-12 15:33:20 status unpacked compiz 1:0.7.4-0ubuntu4
2008-04-12 15:33:20 status unpacked compiz 1:0.7.4-0ubuntu4
2008-04-12 15:33:20 upgrade cryptsetup 2:1.0.5-2ubuntu11 2:1.0.5-2ubuntu12
2008-04-12 15:33:20 status half-configured cryptsetup 2:1.0.5-2ubuntu11
2008-04-12 15:33:20 status unpacked cryptsetup 2:1.0.5-2ubuntu11
2008-04-12 15:33:20 status half-installed cryptsetup 2:1.0.5-2ubuntu11
2008-04-12 15:33:20 status half-installed cryptsetup 2:1.0.5-2ubuntu11
2008-04-12 15:33:20 status unpacked cryptsetup 2:1.0.5-2ubuntu12
2008-04-12 15:33:20 status unpacked cryptsetup 2:1.0.5-2ubuntu12
2008-04-12 15:33:20 upgrade example-content 30 31
2008-04-12 15:33:20 status half-configured example-content 30
2008-04-12 15:33:20 status unpacked example-content 30
2008-04-12 15:33:20 status half-installed example-content 30
2008-04-12 15:33:21 status half-installed example-content 30
2008-04-12 15:33:21 status unpacked example-content 31
2008-04-12 15:33:21 status unpacked example-content 31
2008-04-12 15:33:21 upgrade gdebi 0.3.6 0.3.7
2008-04-12 15:33:21 status half-configured gdebi 0.3.6
2008-04-12 15:33:21 status unpacked gdebi 0.3.6
2008-04-12 15:33:21 status half-installed gdebi 0.3.6
2008-04-12 15:33:21 status half-installed gdebi 0.3.6
2008-04-12 15:33:21 status unpacked gdebi 0.3.7
2008-04-12 15:33:22 status unpacked gdebi 0.3.7
2008-04-12 15:33:22 upgrade gdebi-core 0.3.6 0.3.7
2008-04-12 15:33:22 status half-configured gdebi-core 0.3.6
2008-04-12 15:33:22 status unpacked gdebi-core 0.3.6
2008-04-12 15:33:22 status half-installed gdebi-core 0.3.6
2008-04-12 15:33:22 status half-installed gdebi-core 0.3.6
2008-04-12 15:33:22 status unpacked gdebi-core 0.3.7
2008-04-12 15:33:22 status unpacked gdebi-core 0.3.7
2008-04-12 15:33:22 upgrade gnome-panel-data 1:2.22.1.1-0ubuntu1 1:2.22.1.2-0ubuntu3
2008-04-12 15:33:22 status half-configured gnome-panel-data 1:2.22.1.1-0ubuntu1
2008-04-12 15:33:29 status unpacked gnome-panel-data 1:2.22.1.1-0ubuntu1
2008-04-12 15:33:31 status half-installed gnome-panel-data 1:2.22.1.1-0ubuntu1
2008-04-12 15:33:32 status half-installed gnome-panel-data 1:2.22.1.1-0ubuntu1
2008-04-12 15:33:33 status unpacked gnome-panel-data 1:2.22.1.2-0ubuntu3
2008-04-12 15:33:33 status unpacked gnome-panel-data 1:2.22.1.2-0ubuntu3
2008-04-12 15:33:33 upgrade libpanel-applet2-0 1:2.22.1.1-0ubuntu1 1:2.22.1.2-0ubuntu3
2008-04-12 15:33:33 status half-configured libpanel-applet2-0 1:2.22.1.1-0ubuntu1
2008-04-12 15:33:33 status unpacked libpanel-applet2-0 1:2.22.1.1-0ubuntu1
2008-04-12 15:33:33 status half-installed libpanel-applet2-0 1:2.22.1.1-0ubuntu1
2008-04-12 15:33:33 status half-installed libpanel-applet2-0 1:2.22.1.1-0ubuntu1
2008-04-12 15:33:33 status unpacked libpanel-applet2-0 1:2.22.1.2-0ubuntu3
2008-04-12 15:33:33 status unpacked libpanel-applet2-0 1:2.22.1.2-0ubuntu3
2008-04-12 15:33:33 upgrade gnome-panel 1:2.22.1.1-0ubuntu1 1:2.22.1.2-0ubuntu3
2008-04-12 15:33:33 status half-configured gnome-panel 1:2.22.1.1-0ubuntu1
2008-04-12 15:33:33 status unpacked gnome-panel 1:2.22.1.1-0ubuntu1
2008-04-12 15:33:33 status half-installed gnome-panel 1:2.22.1.1-0ubuntu1
2008-04-12 15:33:33 status half-installed gnome-panel 1:2.22.1.1-0ubuntu1
2008-04-12 15:33:34 status unpacked gnome-panel 1:2.22.1.2-0ubuntu3
2008-04-12 15:33:34 status unpacked gnome-panel 1:2.22.1.2-0ubuntu3
2008-04-12 15:33:34 upgrade gnome-power-manager 2.22.1-1ubuntu3 2.22.1-1ubuntu4
2008-04-12 15:33:34 status half-configured gnome-power-manager 2.22.1-1ubuntu3
2008-04-12 15:33:40 status unpacked gnome-power-manager 2.22.1-1ubuntu3
2008-04-12 15:33:41 status half-installed gnome-power-manager 2.22.1-1ubuntu3
2008-04-12 15:33:42 status half-installed gnome-power-manager 2.22.1-1ubuntu3
2008-04-12 15:33:43 status unpacked gnome-power-manager 2.22.1-1ubuntu4
2008-04-12 15:33:43 status unpacked gnome-power-manager 2.22.1-1ubuntu4
2008-04-12 15:33:43 upgrade gnome-session 2.22.1-0ubuntu3 2.22.1.1-0ubuntu2
2008-04-12 15:33:43 status half-configured gnome-session 2.22.1-0ubuntu3
2008-04-12 15:33:48 status unpacked gnome-session 2.22.1-0ubuntu3
2008-04-12 15:33:50 status half-installed gnome-session 2.22.1-0ubuntu3
2008-04-12 15:33:51 status half-installed gnome-session 2.22.1-0ubuntu3
2008-04-12 15:33:51 status unpacked gnome-session 2.22.1.1-0ubuntu2
2008-04-12 15:33:51 status unpacked gnome-session 2.22.1.1-0ubuntu2
2008-04-12 15:33:51 upgrade hotkey-setup 0.1-17ubuntu20 0.1-17ubuntu21
2008-04-12 15:33:51 status half-configured hotkey-setup 0.1-17ubuntu20
2008-04-12 15:33:52 status unpacked hotkey-setup 0.1-17ubuntu20
2008-04-12 15:33:52 status half-installed hotkey-setup 0.1-17ubuntu20
2008-04-12 15:33:52 status half-installed hotkey-setup 0.1-17ubuntu20
2008-04-12 15:33:52 status unpacked hotkey-setup 0.1-17ubuntu21
2008-04-12 15:33:52 status unpacked hotkey-setup 0.1-17ubuntu21
2008-04-12 15:33:52 upgrade libkleopatra1 4:3.5.9-0ubuntu2 4:3.5.9-0ubuntu3
2008-04-12 15:33:52 status half-configured libkleopatra1 4:3.5.9-0ubuntu2
2008-04-12 15:33:52 status unpacked libkleopatra1 4:3.5.9-0ubuntu2
2008-04-12 15:33:52 status half-installed libkleopatra1 4:3.5.9-0ubuntu2
2008-04-12 15:33:52 status half-installed libkleopatra1 4:3.5.9-0ubuntu2
2008-04-12 15:33:52 status unpacked libkleopatra1 4:3.5.9-0ubuntu3
2008-04-12 15:33:52 status unpacked libkleopatra1 4:3.5.9-0ubuntu3
2008-04-12 15:33:52 upgrade libkmime2 4:3.5.9-0ubuntu2 4:3.5.9-0ubuntu3
2008-04-12 15:33:52 status half-configured libkmime2 4:3.5.9-0ubuntu2
2008-04-12 15:33:52 status unpacked libkmime2 4:3.5.9-0ubuntu2
2008-04-12 15:33:52 status half-installed libkmime2 4:3.5.9-0ubuntu2
2008-04-12 15:33:52 status half-installed libkmime2 4:3.5.9-0ubuntu2
2008-04-12 15:33:52 status unpacked libkmime2 4:3.5.9-0ubuntu3
2008-04-12 15:33:52 status unpacked libkmime2 4:3.5.9-0ubuntu3
2008-04-12 15:33:52 upgrade libkpimidentities1 4:3.5.9-0ubuntu2 4:3.5.9-0ubuntu3
2008-04-12 15:33:52 status half-configured libkpimidentities1 4:3.5.9-0ubuntu2
2008-04-12 15:33:52 status unpacked libkpimidentities1 4:3.5.9-0ubuntu2
2008-04-12 15:33:52 status half-installed libkpimidentities1 4:3.5.9-0ubuntu2
2008-04-12 15:33:52 status half-installed libkpimidentities1 4:3.5.9-0ubuntu2
2008-04-12 15:33:52 status unpacked libkpimidentities1 4:3.5.9-0ubuntu3
2008-04-12 15:33:52 status unpacked libkpimidentities1 4:3.5.9-0ubuntu3
2008-04-12 15:33:53 upgrade kalarm 4:3.5.9-0ubuntu2 4:3.5.9-0ubuntu3
2008-04-12 15:33:53 status half-configured kalarm 4:3.5.9-0ubuntu2
2008-04-12 15:33:53 status unpacked kalarm 4:3.5.9-0ubuntu2
2008-04-12 15:33:53 status half-installed kalarm 4:3.5.9-0ubuntu2
2008-04-12 15:33:53 status half-installed kalarm 4:3.5.9-0ubuntu2
2008-04-12 15:33:54 status unpacked kalarm 4:3.5.9-0ubuntu3
2008-04-12 15:33:54 status unpacked kalarm 4:3.5.9-0ubuntu3
2008-04-12 15:33:54 upgrade karm 4:3.5.9-0ubuntu2 4:3.5.9-0ubuntu3
2008-04-12 15:33:54 status half-configured karm 4:3.5.9-0ubuntu2
2008-04-12 15:33:54 status unpacked karm 4:3.5.9-0ubuntu2
2008-04-12 15:33:54 status half-installed karm 4:3.5.9-0ubuntu2
2008-04-12 15:33:54 status half-installed karm 4:3.5.9-0ubuntu2
2008-04-12 15:33:54 status unpacked karm 4:3.5.9-0ubuntu3
2008-04-12 15:33:55 status unpacked karm 4:3.5.9-0ubuntu3
2008-04-12 15:33:55 upgrade knotes 4:3.5.9-0ubuntu2 4:3.5.9-0ubuntu3
2008-04-12 15:33:55 status half-configured knotes 4:3.5.9-0ubuntu2
2008-04-12 15:33:55 status unpacked knotes 4:3.5.9-0ubuntu2
2008-04-12 15:33:55 status half-installed knotes 4:3.5.9-0ubuntu2
2008-04-12 15:33:55 status half-installed knotes 4:3.5.9-0ubuntu2
2008-04-12 15:33:56 status unpacked knotes 4:3.5.9-0ubuntu3
2008-04-12 15:33:56 status unpacked knotes 4:3.5.9-0ubuntu3
2008-04-12 15:33:56 upgrade libkpimexchange1 4:3.5.9-0ubuntu2 4:3.5.9-0ubuntu3
2008-04-12 15:33:56 status half-configured libkpimexchange1 4:3.5.9-0ubuntu2
2008-04-12 15:33:56 status unpacked libkpimexchange1 4:3.5.9-0ubuntu2
2008-04-12 15:33:56 status half-installed libkpimexchange1 4:3.5.9-0ubuntu2
2008-04-12 15:33:56 status half-installed libkpimexchange1 4:3.5.9-0ubuntu2
2008-04-12 15:33:56 status unpacked libkpimexchange1 4:3.5.9-0ubuntu3
2008-04-12 15:33:56 status unpacked libkpimexchange1 4:3.5.9-0ubuntu3
2008-04-12 15:33:56 upgrade korganizer 4:3.5.9-0ubuntu2 4:3.5.9-0ubuntu3
2008-04-12 15:33:56 status half-configured korganizer 4:3.5.9-0ubuntu2
2008-04-12 15:33:56 status unpacked korganizer 4:3.5.9-0ubuntu2
2008-04-12 15:33:56 status half-installed korganizer 4:3.5.9-0ubuntu2
2008-04-12 15:33:56 status half-installed korganizer 4:3.5.9-0ubuntu2
2008-04-12 15:33:57 status unpacked korganizer 4:3.5.9-0ubuntu3
2008-04-12 15:33:57 status unpacked korganizer 4:3.5.9-0ubuntu3
2008-04-12 15:33:57 upgrade language-support-writing-en 1:8.04+20080409 1:8.04+20080410
2008-04-12 15:33:57 status half-configured language-support-writing-en 1:8.04+20080409
2008-04-12 15:33:57 status unpacked language-support-writing-en 1:8.04+20080409
2008-04-12 15:33:57 status half-installed language-support-writing-en 1:8.04+20080409
2008-04-12 15:33:57 status half-installed language-support-writing-en 1:8.04+20080409
2008-04-12 15:33:57 status unpacked language-support-writing-en 1:8.04+20080410
2008-04-12 15:33:57 status unpacked language-support-writing-en 1:8.04+20080410
2008-04-12 15:33:57 upgrade linux-generic 2.6.24.15.17 2.6.24.16.18
2008-04-12 15:33:57 status half-configured linux-generic 2.6.24.15.17
2008-04-12 15:33:57 status unpacked linux-generic 2.6.24.15.17
2008-04-12 15:33:57 status half-installed linux-generic 2.6.24.15.17
2008-04-12 15:33:57 status half-installed linux-generic 2.6.24.15.17
2008-04-12 15:33:57 status unpacked linux-generic 2.6.24.16.18
2008-04-12 15:33:57 status unpacked linux-generic 2.6.24.16.18
2008-04-12 15:33:57 upgrade linux-image-generic 2.6.24.15.17 2.6.24.16.18
2008-04-12 15:33:57 status half-configured linux-image-generic 2.6.24.15.17
2008-04-12 15:33:57 status unpacked linux-image-generic 2.6.24.15.17
2008-04-12 15:33:57 status half-installed linux-image-generic 2.6.24.15.17
2008-04-12 15:33:57 status half-installed linux-image-generic 2.6.24.15.17
2008-04-12 15:33:57 status unpacked linux-image-generic 2.6.24.16.18
2008-04-12 15:33:57 status unpacked linux-image-generic 2.6.24.16.18
2008-04-12 15:33:57 upgrade linux-restricted-modules-common 2.6.24.12-15.33 2.6.24.12-16.34
2008-04-12 15:33:57 status half-configured linux-restricted-modules-common 2.6.24.12-15.33
2008-04-12 15:33:57 status unpacked linux-restricted-modules-common 2.6.24.12-15.33
2008-04-12 15:33:57 status half-installed linux-restricted-modules-common 2.6.24.12-15.33
2008-04-12 15:33:57 status half-installed linux-restricted-modules-common 2.6.24.12-15.33
2008-04-12 15:33:57 status unpacked linux-restricted-modules-common 2.6.24.12-16.34
2008-04-12 15:33:57 status unpacked linux-restricted-modules-common 2.6.24.12-16.34
2008-04-12 15:33:58 install linux-restricted-modules-2.6.24-16-generic <none> 2.6.24.12-16.34
2008-04-12 15:33:58 status half-installed linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34
2008-04-12 15:33:59 status unpacked linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34
2008-04-12 15:33:59 status unpacked linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34
2008-04-12 15:33:59 upgrade linux-restricted-modules-generic 2.6.24.15.17 2.6.24.16.18
2008-04-12 15:33:59 status half-configured linux-restricted-modules-generic 2.6.24.15.17
2008-04-12 15:33:59 status unpacked linux-restricted-modules-generic 2.6.24.15.17
2008-04-12 15:33:59 status half-installed linux-restricted-modules-generic 2.6.24.15.17
2008-04-12 15:33:59 status half-installed linux-restricted-modules-generic 2.6.24.15.17
2008-04-12 15:33:59 status unpacked linux-restricted-modules-generic 2.6.24.16.18
2008-04-12 15:33:59 status unpacked linux-restricted-modules-generic 2.6.24.16.18
2008-04-12 15:33:59 install linux-headers-2.6.24-16 <none> 2.6.24-16.30
2008-04-12 15:33:59 status half-installed linux-headers-2.6.24-16 2.6.24-16.30
2008-04-12 15:34:03 status unpacked linux-headers-2.6.24-16 2.6.24-16.30
2008-04-12 15:34:03 status unpacked linux-headers-2.6.24-16 2.6.24-16.30
2008-04-12 15:34:03 install linux-headers-2.6.24-16-generic <none> 2.6.24-16.30
2008-04-12 15:34:03 status half-installed linux-headers-2.6.24-16-generic 2.6.24-16.30
2008-04-12 15:34:04 status unpacked linux-headers-2.6.24-16-generic 2.6.24-16.30
2008-04-12 15:34:04 status unpacked linux-headers-2.6.24-16-generic 2.6.24-16.30
2008-04-12 15:34:04 upgrade linux-headers-generic 2.6.24.15.17 2.6.24.16.18
2008-04-12 15:34:04 status half-configured linux-headers-generic 2.6.24.15.17
2008-04-12 15:34:04 status unpacked linux-headers-generic 2.6.24.15.17
2008-04-12 15:34:04 status half-installed linux-headers-generic 2.6.24.15.17
2008-04-12 15:34:04 status half-installed linux-headers-generic 2.6.24.15.17
2008-04-12 15:34:04 status unpacked linux-headers-generic 2.6.24.16.18
2008-04-12 15:34:04 status unpacked linux-headers-generic 2.6.24.16.18
2008-04-12 15:34:04 upgrade nvidia-glx-new 169.12+2.6.24.12-15.33 169.12+2.6.24.12-16.34
2008-04-12 15:34:04 status half-configured nvidia-glx-new 169.12+2.6.24.12-15.33
2008-04-12 15:34:04 status unpacked nvidia-glx-new 169.12+2.6.24.12-15.33
2008-04-12 15:34:04 status half-installed nvidia-glx-new 169.12+2.6.24.12-15.33
2008-04-12 15:34:05 status half-installed nvidia-glx-new 169.12+2.6.24.12-15.33
2008-04-12 15:34:06 status unpacked nvidia-glx-new 169.12+2.6.24.12-16.34
2008-04-12 15:34:06 status unpacked nvidia-glx-new 169.12+2.6.24.12-16.34
2008-04-12 15:34:06 upgrade pm-utils 0.99.2-3ubuntu8 0.99.2-3ubuntu9
2008-04-12 15:34:06 status half-configured pm-utils 0.99.2-3ubuntu8
2008-04-12 15:34:06 status unpacked pm-utils 0.99.2-3ubuntu8
2008-04-12 15:34:06 status half-installed pm-utils 0.99.2-3ubuntu8
2008-04-12 15:34:06 status half-installed pm-utils 0.99.2-3ubuntu8
2008-04-12 15:34:06 status unpacked pm-utils 0.99.2-3ubuntu9
2008-04-12 15:34:06 status unpacked pm-utils 0.99.2-3ubuntu9
2008-04-12 15:34:06 upgrade readahead 1:0.20050517.0220-0ubuntu12 1:0.20050517.0220-0ubuntu13
2008-04-12 15:34:06 status half-configured readahead 1:0.20050517.0220-0ubuntu12
2008-04-12 15:34:06 status unpacked readahead 1:0.20050517.0220-0ubuntu12
2008-04-12 15:34:06 status half-installed readahead 1:0.20050517.0220-0ubuntu12
2008-04-12 15:34:06 status half-installed readahead 1:0.20050517.0220-0ubuntu12
2008-04-12 15:34:06 status unpacked readahead 1:0.20050517.0220-0ubuntu13
2008-04-12 15:34:06 status unpacked readahead 1:0.20050517.0220-0ubuntu13
2008-04-12 15:34:06 upgrade rhythmbox 0.11.5-0ubuntu2 0.11.5-0ubuntu3
2008-04-12 15:34:06 status half-configured rhythmbox 0.11.5-0ubuntu2
2008-04-12 15:34:12 status unpacked rhythmbox 0.11.5-0ubuntu2
2008-04-12 15:34:13 status half-installed rhythmbox 0.11.5-0ubuntu2
2008-04-12 15:34:14 status half-installed rhythmbox 0.11.5-0ubuntu2
2008-04-12 15:34:17 status unpacked rhythmbox 0.11.5-0ubuntu3
2008-04-12 15:34:18 status unpacked rhythmbox 0.11.5-0ubuntu3
2008-04-12 15:34:19 upgrade totem-plugins 2.22.1-0ubuntu1 2.22.1-0ubuntu2
2008-04-12 15:34:19 status half-configured totem-plugins 2.22.1-0ubuntu1
2008-04-12 15:34:19 status unpacked totem-plugins 2.22.1-0ubuntu1
2008-04-12 15:34:19 status half-installed totem-plugins 2.22.1-0ubuntu1
2008-04-12 15:34:19 status half-installed totem-plugins 2.22.1-0ubuntu1
2008-04-12 15:34:19 status unpacked totem-plugins 2.22.1-0ubuntu2
2008-04-12 15:34:19 status unpacked totem-plugins 2.22.1-0ubuntu2
2008-04-12 15:34:19 upgrade totem-common 2.22.1-0ubuntu1 2.22.1-0ubuntu2
2008-04-12 15:34:19 status half-configured totem-common 2.22.1-0ubuntu1
2008-04-12 15:34:24 status unpacked totem-common 2.22.1-0ubuntu1
2008-04-12 15:34:26 status half-installed totem-common 2.22.1-0ubuntu1
2008-04-12 15:34:26 status half-installed totem-common 2.22.1-0ubuntu1
2008-04-12 15:34:26 status unpacked totem-common 2.22.1-0ubuntu2
2008-04-12 15:34:26 status unpacked totem-common 2.22.1-0ubuntu2
2008-04-12 15:34:26 upgrade totem-gstreamer 2.22.1-0ubuntu1 2.22.1-0ubuntu2
2008-04-12 15:34:26 status half-configured totem-gstreamer 2.22.1-0ubuntu1
2008-04-12 15:34:26 status unpacked totem-gstreamer 2.22.1-0ubuntu1
2008-04-12 15:34:26 status half-installed totem-gstreamer 2.22.1-0ubuntu1
2008-04-12 15:34:26 status half-installed totem-gstreamer 2.22.1-0ubuntu1
2008-04-12 15:34:27 status unpacked totem-gstreamer 2.22.1-0ubuntu2
2008-04-12 15:34:27 status unpacked totem-gstreamer 2.22.1-0ubuntu2
2008-04-12 15:34:27 upgrade totem 2.22.1-0ubuntu1 2.22.1-0ubuntu2
2008-04-12 15:34:27 status half-configured totem 2.22.1-0ubuntu1
2008-04-12 15:34:27 status unpacked totem 2.22.1-0ubuntu1
2008-04-12 15:34:27 status half-installed totem 2.22.1-0ubuntu1
2008-04-12 15:34:27 status half-installed totem 2.22.1-0ubuntu1
2008-04-12 15:34:27 status unpacked totem 2.22.1-0ubuntu2
2008-04-12 15:34:27 status unpacked totem 2.22.1-0ubuntu2
2008-04-12 15:34:27 upgrade totem-mozilla 2.22.1-0ubuntu1 2.22.1-0ubuntu2
2008-04-12 15:34:27 status half-configured totem-mozilla 2.22.1-0ubuntu1
2008-04-12 15:34:27 status unpacked totem-mozilla 2.22.1-0ubuntu1
2008-04-12 15:34:27 status half-installed totem-mozilla 2.22.1-0ubuntu1
2008-04-12 15:34:27 status half-installed totem-mozilla 2.22.1-0ubuntu1
2008-04-12 15:34:27 status unpacked totem-mozilla 2.22.1-0ubuntu2
2008-04-12 15:34:27 status unpacked totem-mozilla 2.22.1-0ubuntu2
2008-04-12 15:34:27 upgrade xscreensaver-data 5.04-2ubuntu2 5.04-4ubuntu1
2008-04-12 15:34:27 status half-configured xscreensaver-data 5.04-2ubuntu2
2008-04-12 15:34:27 status unpacked xscreensaver-data 5.04-2ubuntu2
2008-04-12 15:34:27 status half-installed xscreensaver-data 5.04-2ubuntu2
2008-04-12 15:34:27 status half-installed xscreensaver-data 5.04-2ubuntu2
2008-04-12 15:34:27 status unpacked xscreensaver-data 5.04-4ubuntu1
2008-04-12 15:34:27 status unpacked xscreensaver-data 5.04-4ubuntu1
2008-04-12 15:34:27 upgrade xscreensaver-gl 5.04-2ubuntu2 5.04-4ubuntu1
2008-04-12 15:34:27 status half-configured xscreensaver-gl 5.04-2ubuntu2
2008-04-12 15:34:27 status unpacked xscreensaver-gl 5.04-2ubuntu2
2008-04-12 15:34:27 status half-installed xscreensaver-gl 5.04-2ubuntu2
2008-04-12 15:34:28 status half-installed xscreensaver-gl 5.04-2ubuntu2
2008-04-12 15:34:28 status unpacked xscreensaver-gl 5.04-4ubuntu1
2008-04-12 15:34:28 status unpacked xscreensaver-gl 5.04-4ubuntu1
2008-04-12 15:34:29 startup packages configure
2008-04-12 15:34:29 configure libvolume-id0 117-8 117-8
2008-04-12 15:34:29 status unpacked libvolume-id0 117-8
2008-04-12 15:34:29 status half-configured libvolume-id0 117-8
2008-04-12 15:34:29 status installed libvolume-id0 117-8
2008-04-12 15:34:29 configure upstart 0.3.9-2 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart 0.3.9-2
2008-04-12 15:34:29 status half-configured upstart 0.3.9-2
2008-04-12 15:34:29 status installed upstart 0.3.9-2
2008-04-12 15:34:29 configure upstart-compat-sysv 0.3.9-2 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 status half-configured upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 status installed upstart-compat-sysv 0.3.9-2
2008-04-12 15:34:29 configure upstart-logd 0.3.9-2 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-logd 0.3.9-2
2008-04-12 15:34:29 status unpacked upstart-logd 0.3.9-2
2008-04-12 15:34:29 status half-configured upstart-logd 0.3.9-2
2008-04-12 15:34:29 status installed upstart-logd 0.3.9-2
2008-04-12 15:34:29 configure startup-tasks 0.3.9-2 0.3.9-2
2008-04-12 15:34:29 status unpacked startup-tasks 0.3.9-2
2008-04-12 15:34:29 status half-configured startup-tasks 0.3.9-2
2008-04-12 15:34:29 status installed startup-tasks 0.3.9-2
2008-04-12 15:34:29 configure system-services 0.3.9-2 0.3.9-2
2008-04-12 15:34:29 status unpacked system-services 0.3.9-2
2008-04-12 15:34:29 status unpacked system-services 0.3.9-2
2008-04-12 15:34:29 status unpacked system-services 0.3.9-2
2008-04-12 15:34:29 status unpacked system-services 0.3.9-2
2008-04-12 15:34:29 status unpacked system-services 0.3.9-2
2008-04-12 15:34:29 status unpacked system-services 0.3.9-2
2008-04-12 15:34:29 status unpacked system-services 0.3.9-2
2008-04-12 15:34:29 status half-configured system-services 0.3.9-2
2008-04-12 15:34:29 status installed system-services 0.3.9-2
2008-04-12 15:34:29 configure command-not-found-data 0.2.17ubuntu1 0.2.17ubuntu1
2008-04-12 15:34:29 status unpacked command-not-found-data 0.2.17ubuntu1
2008-04-12 15:34:29 status half-configured command-not-found-data 0.2.17ubuntu1
2008-04-12 15:34:29 status installed command-not-found-data 0.2.17ubuntu1
2008-04-12 15:34:29 configure command-not-found 0.2.17ubuntu1 0.2.17ubuntu1
2008-04-12 15:34:29 status unpacked command-not-found 0.2.17ubuntu1
2008-04-12 15:34:29 status unpacked command-not-found 0.2.17ubuntu1
2008-04-12 15:34:29 status half-configured command-not-found 0.2.17ubuntu1
2008-04-12 15:34:29 status installed command-not-found 0.2.17ubuntu1
2008-04-12 15:34:29 configure friendly-recovery 0.1 0.1
2008-04-12 15:34:29 status unpacked friendly-recovery 0.1
2008-04-12 15:34:29 status half-configured friendly-recovery 0.1
2008-04-12 15:34:29 status installed friendly-recovery 0.1
2008-04-12 15:34:29 configure rsync 2.6.9-6ubuntu2 2.6.9-6ubuntu2
2008-04-12 15:34:29 status unpacked rsync 2.6.9-6ubuntu2
2008-04-12 15:34:29 status unpacked rsync 2.6.9-6ubuntu2
2008-04-12 15:34:29 status unpacked rsync 2.6.9-6ubuntu2
2008-04-12 15:34:29 status half-configured rsync 2.6.9-6ubuntu2
2008-04-12 15:34:29 status installed rsync 2.6.9-6ubuntu2
2008-04-12 15:34:29 configure libcairo2 1.6.0-0ubuntu1 1.6.0-0ubuntu1
2008-04-12 15:34:29 status unpacked libcairo2 1.6.0-0ubuntu1
2008-04-12 15:34:29 status half-configured libcairo2 1.6.0-0ubuntu1
2008-04-12 15:34:29 status installed libcairo2 1.6.0-0ubuntu1
2008-04-12 15:34:29 status triggers-pending libc6 2.7-10ubuntu3
2008-04-12 15:34:29 configure synaptic 0.61ubuntu9 0.61ubuntu9
2008-04-12 15:34:29 status unpacked synaptic 0.61ubuntu9
2008-04-12 15:34:29 status half-configured synaptic 0.61ubuntu9
2008-04-12 15:34:48 status installed synaptic 0.61ubuntu9
2008-04-12 15:34:48 configure update-manager-core 1:0.87.17 1:0.87.17
2008-04-12 15:34:48 status unpacked update-manager-core 1:0.87.17
2008-04-12 15:34:48 status unpacked update-manager-core 1:0.87.17
2008-04-12 15:34:48 status half-configured update-manager-core 1:0.87.17
2008-04-12 15:34:49 status installed update-manager-core 1:0.87.17
2008-04-12 15:34:49 configure update-manager 1:0.87.17 1:0.87.17
2008-04-12 15:34:49 status unpacked update-manager 1:0.87.17
2008-04-12 15:34:49 status half-configured update-manager 1:0.87.17
2008-04-12 15:34:53 status installed update-manager 1:0.87.17
2008-04-12 15:34:54 configure libktnef1 4:3.5.9-0ubuntu3 4:3.5.9-0ubuntu3
2008-04-12 15:34:54 status unpacked libktnef1 4:3.5.9-0ubuntu3
2008-04-12 15:34:54 status half-configured libktnef1 4:3.5.9-0ubuntu3
2008-04-12 15:34:54 status installed libktnef1 4:3.5.9-0ubuntu3
2008-04-12 15:34:54 configure libmtp7 0.2.6.1-2ubuntu1 0.2.6.1-2ubuntu1
2008-04-12 15:34:54 status unpacked libmtp7 0.2.6.1-2ubuntu1
2008-04-12 15:34:54 status unpacked libmtp7 0.2.6.1-2ubuntu1
2008-04-12 15:34:54 status half-configured libmtp7 0.2.6.1-2ubuntu1
2008-04-12 15:34:54 status installed libmtp7 0.2.6.1-2ubuntu1
2008-04-12 15:34:54 configure gnome-app-install 0.5.2.7-0ubuntu1 0.5.2.7-0ubuntu1
2008-04-12 15:34:54 status unpacked gnome-app-install 0.5.2.7-0ubuntu1
2008-04-12 15:34:54 status half-configured gnome-app-install 0.5.2.7-0ubuntu1
2008-04-12 15:35:25 status installed gnome-app-install 0.5.2.7-0ubuntu1
2008-04-12 15:35:25 configure apturl 0.2.1ubuntu1 0.2.1ubuntu1
2008-04-12 15:35:25 status unpacked apturl 0.2.1ubuntu1
2008-04-12 15:35:25 status unpacked apturl 0.2.1ubuntu1
2008-04-12 15:35:25 status half-configured apturl 0.2.1ubuntu1
2008-04-12 15:35:25 status installed apturl 0.2.1ubuntu1
2008-04-12 15:35:25 configure compiz-core 1:0.7.4-0ubuntu4 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 status unpacked compiz-core 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 status unpacked compiz-core 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 status half-configured compiz-core 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 status installed compiz-core 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 configure libdecoration0 1:0.7.4-0ubuntu4 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 status unpacked libdecoration0 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 status half-configured libdecoration0 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 status installed libdecoration0 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 configure compiz-plugins 1:0.7.4-0ubuntu4 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 status unpacked compiz-plugins 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 status half-configured compiz-plugins 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 status installed compiz-plugins 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 configure libcompizconfig0 0.7.4-0ubuntu1 0.7.4-0ubuntu1
2008-04-12 15:35:25 status unpacked libcompizconfig0 0.7.4-0ubuntu1
2008-04-12 15:35:25 status unpacked libcompizconfig0 0.7.4-0ubuntu1
2008-04-12 15:35:25 status half-configured libcompizconfig0 0.7.4-0ubuntu1
2008-04-12 15:35:25 status installed libcompizconfig0 0.7.4-0ubuntu1
2008-04-12 15:35:25 configure compizconfig-backend-gconf 0.7.4-0ubuntu1 0.7.4-0ubuntu1
2008-04-12 15:35:25 status unpacked compizconfig-backend-gconf 0.7.4-0ubuntu1
2008-04-12 15:35:25 status half-configured compizconfig-backend-gconf 0.7.4-0ubuntu1
2008-04-12 15:35:25 status installed compizconfig-backend-gconf 0.7.4-0ubuntu1
2008-04-12 15:35:25 configure compiz-gnome 1:0.7.4-0ubuntu4 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 status unpacked compiz-gnome 1:0.7.4-0ubuntu4
2008-04-12 15:35:25 status half-configured compiz-gnome 1:0.7.4-0ubuntu4
2008-04-12 15:35:28 status installed compiz-gnome 1:0.7.4-0ubuntu4
2008-04-12 15:35:29 configure compiz-fusion-plugins-extra 0.7.4-0ubuntu1 0.7.4-0ubuntu1
2008-04-12 15:35:29 status unpacked compiz-fusion-plugins-extra 0.7.4-0ubuntu1
2008-04-12 15:35:29 status half-configured compiz-fusion-plugins-extra 0.7.4-0ubuntu1
2008-04-12 15:35:31 status installed compiz-fusion-plugins-extra 0.7.4-0ubuntu1
2008-04-12 15:35:32 configure compiz-fusion-plugins-main 0.7.4-0ubuntu3 0.7.4-0ubuntu3
2008-04-12 15:35:32 status unpacked compiz-fusion-plugins-main 0.7.4-0ubuntu3
2008-04-12 15:35:32 status half-configured compiz-fusion-plugins-main 0.7.4-0ubuntu3
2008-04-12 15:35:35 status installed compiz-fusion-plugins-main 0.7.4-0ubuntu3
2008-04-12 15:35:36 configure compiz 1:0.7.4-0ubuntu4 1:0.7.4-0ubuntu4
2008-04-12 15:35:36 status unpacked compiz 1:0.7.4-0ubuntu4
2008-04-12 15:35:36 status half-configured compiz 1:0.7.4-0ubuntu4
2008-04-12 15:35:36 status installed compiz 1:0.7.4-0ubuntu4
2008-04-12 15:35:36 configure cryptsetup 2:1.0.5-2ubuntu12 2:1.0.5-2ubuntu12
2008-04-12 15:35:36 status unpacked cryptsetup 2:1.0.5-2ubuntu12
2008-04-12 15:35:36 status unpacked cryptsetup 2:1.0.5-2ubuntu12
2008-04-12 15:35:36 status unpacked cryptsetup 2:1.0.5-2ubuntu12
2008-04-12 15:35:36 status unpacked cryptsetup 2:1.0.5-2ubuntu12
2008-04-12 15:35:36 status half-configured cryptsetup 2:1.0.5-2ubuntu12
2008-04-12 15:35:36 status installed cryptsetup 2:1.0.5-2ubuntu12
2008-04-12 15:35:36 configure example-content 31 31
2008-04-12 15:35:36 status unpacked example-content 31
2008-04-12 15:35:36 status half-configured example-content 31
2008-04-12 15:35:36 status installed example-content 31
2008-04-12 15:35:36 configure gdebi-core 0.3.7 0.3.7
2008-04-12 15:35:36 status unpacked gdebi-core 0.3.7
2008-04-12 15:35:36 status half-configured gdebi-core 0.3.7
2008-04-12 15:35:36 status installed gdebi-core 0.3.7
2008-04-12 15:35:36 configure gdebi 0.3.7 0.3.7
2008-04-12 15:35:36 status unpacked gdebi 0.3.7
2008-04-12 15:35:36 status half-configured gdebi 0.3.7
2008-04-12 15:35:36 status installed gdebi 0.3.7
2008-04-12 15:35:36 configure gnome-panel-data 1:2.22.1.2-0ubuntu3 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:36 status unpacked gnome-panel-data 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:36 status unpacked gnome-panel-data 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:36 status unpacked gnome-panel-data 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:36 status unpacked gnome-panel-data 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:36 status unpacked gnome-panel-data 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:36 status unpacked gnome-panel-data 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:36 status half-configured gnome-panel-data 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:43 status installed gnome-panel-data 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:44 configure libpanel-applet2-0 1:2.22.1.2-0ubuntu3 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:44 status unpacked libpanel-applet2-0 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:44 status half-configured libpanel-applet2-0 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:44 status installed libpanel-applet2-0 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:44 configure gnome-panel 1:2.22.1.2-0ubuntu3 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:44 status unpacked gnome-panel 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:44 status half-configured gnome-panel 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:44 status installed gnome-panel 1:2.22.1.2-0ubuntu3
2008-04-12 15:35:44 configure gnome-power-manager 2.22.1-1ubuntu4 2.22.1-1ubuntu4
2008-04-12 15:35:44 status unpacked gnome-power-manager 2.22.1-1ubuntu4
2008-04-12 15:35:44 status unpacked gnome-power-manager 2.22.1-1ubuntu4
2008-04-12 15:35:44 status half-configured gnome-power-manager 2.22.1-1ubuntu4
2008-04-12 15:35:50 status installed gnome-power-manager 2.22.1-1ubuntu4
2008-04-12 15:35:51 configure gnome-session 2.22.1.1-0ubuntu2 2.22.1.1-0ubuntu2
2008-04-12 15:35:51 status unpacked gnome-session 2.22.1.1-0ubuntu2
2008-04-12 15:35:51 status unpacked gnome-session 2.22.1.1-0ubuntu2
2008-04-12 15:35:51 status half-configured gnome-session 2.22.1.1-0ubuntu2
2008-04-12 15:35:59 status installed gnome-session 2.22.1.1-0ubuntu2
2008-04-12 15:35:59 configure hotkey-setup 0.1-17ubuntu21 0.1-17ubuntu21
2008-04-12 15:35:59 status unpacked hotkey-setup 0.1-17ubuntu21
2008-04-12 15:35:59 status unpacked hotkey-setup 0.1-17ubuntu21
2008-04-12 15:35:59 status half-configured hotkey-setup 0.1-17ubuntu21
2008-04-12 15:35:59 status installed hotkey-setup 0.1-17ubuntu21
2008-04-12 15:35:59 configure libkleopatra1 4:3.5.9-0ubuntu3 4:3.5.9-0ubuntu3
2008-04-12 15:35:59 status unpacked libkleopatra1 4:3.5.9-0ubuntu3
2008-04-12 15:35:59 status unpacked libkleopatra1 4:3.5.9-0ubuntu3
2008-04-12 15:35:59 status half-configured libkleopatra1 4:3.5.9-0ubuntu3
2008-04-12 15:35:59 status installed libkleopatra1 4:3.5.9-0ubuntu3
2008-04-12 15:35:59 configure libkmime2 4:3.5.9-0ubuntu3 4:3.5.9-0ubuntu3
2008-04-12 15:35:59 status unpacked libkmime2 4:3.5.9-0ubuntu3
2008-04-12 15:35:59 status half-configured libkmime2 4:3.5.9-0ubuntu3
2008-04-12 15:35:59 status installed libkmime2 4:3.5.9-0ubuntu3
2008-04-12 15:35:59 configure language-support-writing-en 1:8.04+20080410 1:8.04+20080410
2008-04-12 15:35:59 status unpacked language-support-writing-en 1:8.04+20080410
2008-04-12 15:35:59 status half-configured language-support-writing-en 1:8.04+20080410
2008-04-12 15:36:01 status installed language-support-writing-en 1:8.04+20080410
2008-04-12 15:36:01 configure linux-restricted-modules-common 2.6.24.12-16.34 2.6.24.12-16.34
2008-04-12 15:36:01 status unpacked linux-restricted-modules-common 2.6.24.12-16.34
2008-04-12 15:36:01 status unpacked linux-restricted-modules-common 2.6.24.12-16.34
2008-04-12 15:36:01 status unpacked linux-restricted-modules-common 2.6.24.12-16.34
2008-04-12 15:36:01 status unpacked linux-restricted-modules-common 2.6.24.12-16.34
2008-04-12 15:36:01 status half-configured linux-restricted-modules-common 2.6.24.12-16.34
2008-04-12 15:36:01 status installed linux-restricted-modules-common 2.6.24.12-16.34
2008-04-12 15:36:01 configure linux-headers-2.6.24-16 2.6.24-16.30 2.6.24-16.30
2008-04-12 15:36:01 status unpacked linux-headers-2.6.24-16 2.6.24-16.30
2008-04-12 15:36:01 status half-configured linux-headers-2.6.24-16 2.6.24-16.30
2008-04-12 15:36:01 status installed linux-headers-2.6.24-16 2.6.24-16.30
2008-04-12 15:36:01 configure linux-headers-2.6.24-16-generic 2.6.24-16.30 2.6.24-16.30
2008-04-12 15:36:01 status unpacked linux-headers-2.6.24-16-generic 2.6.24-16.30
2008-04-12 15:36:01 status half-configured linux-headers-2.6.24-16-generic 2.6.24-16.30
2008-04-12 15:36:01 status installed linux-headers-2.6.24-16-generic 2.6.24-16.30
2008-04-12 15:36:01 configure linux-headers-generic 2.6.24.16.18 2.6.24.16.18
2008-04-12 15:36:01 status unpacked linux-headers-generic 2.6.24.16.18
2008-04-12 15:36:01 status half-configured linux-headers-generic 2.6.24.16.18
2008-04-12 15:36:01 status installed linux-headers-generic 2.6.24.16.18
2008-04-12 15:36:01 configure nvidia-glx-new 169.12+2.6.24.12-16.34 169.12+2.6.24.12-16.34
2008-04-12 15:36:01 status unpacked nvidia-glx-new 169.12+2.6.24.12-16.34
2008-04-12 15:36:01 status half-configured nvidia-glx-new 169.12+2.6.24.12-16.34
2008-04-12 15:36:01 status installed nvidia-glx-new 169.12+2.6.24.12-16.34
2008-04-12 15:36:01 configure pm-utils 0.99.2-3ubuntu9 0.99.2-3ubuntu9
2008-04-12 15:36:01 status unpacked pm-utils 0.99.2-3ubuntu9
2008-04-12 15:36:01 status half-configured pm-utils 0.99.2-3ubuntu9
2008-04-12 15:36:01 status installed pm-utils 0.99.2-3ubuntu9
2008-04-12 15:36:01 configure readahead 1:0.20050517.0220-0ubuntu13 1:0.20050517.0220-0ubuntu13
2008-04-12 15:36:01 status unpacked readahead 1:0.20050517.0220-0ubuntu13
2008-04-12 15:36:01 status unpacked readahead 1:0.20050517.0220-0ubuntu13
2008-04-12 15:36:01 status unpacked readahead 1:0.20050517.0220-0ubuntu13
2008-04-12 15:36:01 status unpacked readahead 1:0.20050517.0220-0ubuntu13
2008-04-12 15:36:01 status unpacked readahead 1:0.20050517.0220-0ubuntu13
2008-04-12 15:36:01 status unpacked readahead 1:0.20050517.0220-0ubuntu13
2008-04-12 15:36:01 status half-configured readahead 1:0.20050517.0220-0ubuntu13
2008-04-12 15:36:01 status installed readahead 1:0.20050517.0220-0ubuntu13
2008-04-12 15:36:01 configure rhythmbox 0.11.5-0ubuntu3 0.11.5-0ubuntu3
2008-04-12 15:36:01 status unpacked rhythmbox 0.11.5-0ubuntu3
2008-04-12 15:36:02 status half-configured rhythmbox 0.11.5-0ubuntu3
2008-04-12 15:36:04 status installed rhythmbox 0.11.5-0ubuntu3
2008-04-12 15:36:04 configure totem-common 2.22.1-0ubuntu2 2.22.1-0ubuntu2
2008-04-12 15:36:04 status unpacked totem-common 2.22.1-0ubuntu2
2008-04-12 15:36:04 status half-configured totem-common 2.22.1-0ubuntu2
2008-04-12 15:36:10 status installed totem-common 2.22.1-0ubuntu2
2008-04-12 15:36:11 configure totem-gstreamer 2.22.1-0ubuntu2 2.22.1-0ubuntu2
2008-04-12 15:36:11 status unpacked totem-gstreamer 2.22.1-0ubuntu2
2008-04-12 15:36:12 status half-configured totem-gstreamer 2.22.1-0ubuntu2
2008-04-12 15:36:12 status installed totem-gstreamer 2.22.1-0ubuntu2
2008-04-12 15:36:12 configure totem-plugins 2.22.1-0ubuntu2 2.22.1-0ubuntu2
2008-04-12 15:36:12 status unpacked totem-plugins 2.22.1-0ubuntu2
2008-04-12 15:36:12 status half-configured totem-plugins 2.22.1-0ubuntu2
2008-04-12 15:36:12 status installed totem-plugins 2.22.1-0ubuntu2
2008-04-12 15:36:12 configure totem 2.22.1-0ubuntu2 2.22.1-0ubuntu2
2008-04-12 15:36:12 status unpacked totem 2.22.1-0ubuntu2
2008-04-12 15:36:12 status half-configured totem 2.22.1-0ubuntu2
2008-04-12 15:36:12 status installed totem 2.22.1-0ubuntu2
2008-04-12 15:36:12 configure totem-mozilla 2.22.1-0ubuntu2 2.22.1-0ubuntu2
2008-04-12 15:36:12 status unpacked totem-mozilla 2.22.1-0ubuntu2
2008-04-12 15:36:12 status half-configured totem-mozilla 2.22.1-0ubuntu2
2008-04-12 15:36:12 status installed totem-mozilla 2.22.1-0ubuntu2
2008-04-12 15:36:12 configure xscreensaver-data 5.04-4ubuntu1 5.04-4ubuntu1
2008-04-12 15:36:12 status unpacked xscreensaver-data 5.04-4ubuntu1
2008-04-12 15:36:12 status unpacked xscreensaver-data 5.04-4ubuntu1
2008-04-12 15:36:12 status half-configured xscreensaver-data 5.04-4ubuntu1
2008-04-12 15:36:12 status installed xscreensaver-data 5.04-4ubuntu1
2008-04-12 15:36:12 configure xscreensaver-gl 5.04-4ubuntu1 5.04-4ubuntu1
2008-04-12 15:36:12 status unpacked xscreensaver-gl 5.04-4ubuntu1
2008-04-12 15:36:12 status unpacked xscreensaver-gl 5.04-4ubuntu1
2008-04-12 15:36:12 status half-configured xscreensaver-gl 5.04-4ubuntu1
2008-04-12 15:36:12 status installed xscreensaver-gl 5.04-4ubuntu1
2008-04-12 15:36:12 configure libkdepim1a 4:3.5.9-0ubuntu3 4:3.5.9-0ubuntu3
2008-04-12 15:36:12 status unpacked libkdepim1a 4:3.5.9-0ubuntu3
2008-04-12 15:36:12 status half-configured libkdepim1a 4:3.5.9-0ubuntu3
2008-04-12 15:36:12 status installed libkdepim1a 4:3.5.9-0ubuntu3
2008-04-12 15:36:12 configure amarok-xine 2:1.4.9.1-0ubuntu1 2:1.4.9.1-0ubuntu1
2008-04-12 15:36:12 status unpacked amarok-xine 2:1.4.9.1-0ubuntu1
2008-04-12 15:36:12 status half-configured amarok-xine 2:1.4.9.1-0ubuntu1
2008-04-12 15:36:12 status installed amarok-xine 2:1.4.9.1-0ubuntu1
2008-04-12 15:36:12 configure udev 117-8 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status unpacked udev 117-8
2008-04-12 15:36:12 status half-configured udev 117-8
2008-04-12 15:36:13 status installed udev 117-8
2008-04-12 15:36:13 configure initramfs-tools 0.85eubuntu36 0.85eubuntu36
2008-04-12 15:36:13 status unpacked initramfs-tools 0.85eubuntu36
2008-04-12 15:36:13 status unpacked initramfs-tools 0.85eubuntu36
2008-04-12 15:36:13 status unpacked initramfs-tools 0.85eubuntu36
2008-04-12 15:36:13 status half-configured initramfs-tools 0.85eubuntu36
2008-04-12 15:36:13 status installed initramfs-tools 0.85eubuntu36
2008-04-12 15:36:13 status triggers-pending initramfs-tools 0.85eubuntu36
2008-04-12 15:36:13 configure grub 0.97-29ubuntu21 0.97-29ubuntu21
2008-04-12 15:36:13 status unpacked grub 0.97-29ubuntu21
2008-04-12 15:36:13 status half-configured grub 0.97-29ubuntu21
2008-04-12 15:36:13 status installed grub 0.97-29ubuntu21
2008-04-12 15:36:13 configure linux-image-2.6.24-16-generic 2.6.24-16.30 2.6.24-16.30
2008-04-12 15:36:13 status unpacked linux-image-2.6.24-16-generic 2.6.24-16.30
2008-04-12 15:36:13 status half-configured linux-image-2.6.24-16-generic 2.6.24-16.30
2008-04-12 15:36:32 status installed linux-image-2.6.24-16-generic 2.6.24-16.30
2008-04-12 15:36:32 configure linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.22 2.6.24-16.22
2008-04-12 15:36:32 status unpacked linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.22
2008-04-12 15:36:32 status half-configured linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.22
2008-04-12 15:36:47 status installed linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.22
2008-04-12 15:36:47 configure libkcal2b 4:3.5.9-0ubuntu3 4:3.5.9-0ubuntu3
2008-04-12 15:36:47 status unpacked libkcal2b 4:3.5.9-0ubuntu3
2008-04-12 15:36:47 status half-configured libkcal2b 4:3.5.9-0ubuntu3
2008-04-12 15:36:47 status installed libkcal2b 4:3.5.9-0ubuntu3
2008-04-12 15:36:47 configure akregator 4:3.5.9-0ubuntu3 4:3.5.9-0ubuntu3
2008-04-12 15:36:47 status unpacked akregator 4:3.5.9-0ubuntu3
2008-04-12 15:36:47 status half-configured akregator 4:3.5.9-0ubuntu3
2008-04-12 15:36:48 status installed akregator 4:3.5.9-0ubuntu3
2008-04-12 15:36:48 configure amarok 2:1.4.9.1-0ubuntu1 2:1.4.9.1-0ubuntu1
2008-04-12 15:36:48 status unpacked amarok 2:1.4.9.1-0ubuntu1
2008-04-12 15:36:48 status unpacked amarok 2:1.4.9.1-0ubuntu1
2008-04-12 15:36:48 status half-configured amarok 2:1.4.9.1-0ubuntu1
2008-04-12 15:36:48 status installed amarok 2:1.4.9.1-0ubuntu1
2008-04-12 15:36:48 configure libkpimidentities1 4:3.5.9-0ubuntu3 4:3.5.9-0ubuntu3
2008-04-12 15:36:48 status unpacked libkpimidentities1 4:3.5.9-0ubuntu3
2008-04-12 15:36:48 status half-configured libkpimidentities1 4:3.5.9-0ubuntu3
2008-04-12 15:36:48 status installed libkpimidentities1 4:3.5.9-0ubuntu3
2008-04-12 15:36:48 configure kalarm 4:3.5.9-0ubuntu3 4:3.5.9-0ubuntu3
2008-04-12 15:36:48 status unpacked kalarm 4:3.5.9-0ubuntu3
2008-04-12 15:36:48 status half-configured kalarm 4:3.5.9-0ubuntu3
2008-04-12 15:36:49 status installed kalarm 4:3.5.9-0ubuntu3
2008-04-12 15:36:49 configure karm 4:3.5.9-0ubuntu3 4:3.5.9-0ubuntu3
2008-04-12 15:36:49 status unpacked karm 4:3.5.9-0ubuntu3
2008-04-12 15:36:49 status half-configured karm 4:3.5.9-0ubuntu3
2008-04-12 15:36:49 status installed karm 4:3.5.9-0ubuntu3
2008-04-12 15:36:49 configure knotes 4:3.5.9-0ubuntu3 4:3.5.9-0ubuntu3
2008-04-12 15:36:49 status unpacked knotes 4:3.5.9-0ubuntu3
2008-04-12 15:36:49 status half-configured knotes 4:3.5.9-0ubuntu3
2008-04-12 15:36:49 status installed knotes 4:3.5.9-0ubuntu3
2008-04-12 15:36:50 configure libkpimexchange1 4:3.5.9-0ubuntu3 4:3.5.9-0ubuntu3
2008-04-12 15:36:50 status unpacked libkpimexchange1 4:3.5.9-0ubuntu3
2008-04-12 15:36:50 status half-configured libkpimexchange1 4:3.5.9-0ubuntu3
2008-04-12 15:36:50 status installed libkpimexchange1 4:3.5.9-0ubuntu3
2008-04-12 15:36:50 configure korganizer 4:3.5.9-0ubuntu3 4:3.5.9-0ubuntu3
2008-04-12 15:36:50 status unpacked korganizer 4:3.5.9-0ubuntu3
2008-04-12 15:36:50 status half-configured korganizer 4:3.5.9-0ubuntu3
2008-04-12 15:36:50 status installed korganizer 4:3.5.9-0ubuntu3
2008-04-12 15:36:50 configure linux-image-generic 2.6.24.16.18 2.6.24.16.18
2008-04-12 15:36:50 status unpacked linux-image-generic 2.6.24.16.18
2008-04-12 15:36:50 status half-configured linux-image-generic 2.6.24.16.18
2008-04-12 15:36:50 status installed linux-image-generic 2.6.24.16.18
2008-04-12 15:36:50 configure linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34 2.6.24.12-16.34
2008-04-12 15:36:50 status unpacked linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34
2008-04-12 15:36:50 status half-configured linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34
2008-04-12 15:36:51 status installed linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34
2008-04-12 15:36:51 configure linux-restricted-modules-generic 2.6.24.16.18 2.6.24.16.18
2008-04-12 15:36:51 status unpacked linux-restricted-modules-generic 2.6.24.16.18
2008-04-12 15:36:51 status half-configured linux-restricted-modules-generic 2.6.24.16.18
2008-04-12 15:36:51 status installed linux-restricted-modules-generic 2.6.24.16.18
2008-04-12 15:36:51 configure linux-generic 2.6.24.16.18 2.6.24.16.18
2008-04-12 15:36:51 status unpacked linux-generic 2.6.24.16.18
2008-04-12 15:36:51 status half-configured linux-generic 2.6.24.16.18
2008-04-12 15:36:51 status installed linux-generic 2.6.24.16.18
2008-04-12 15:36:51 trigproc libc6 2.7-10ubuntu3 2.7-10ubuntu3
2008-04-12 15:36:51 status half-configured libc6 2.7-10ubuntu3
2008-04-12 15:36:52 status installed libc6 2.7-10ubuntu3
2008-04-12 15:36:52 trigproc initramfs-tools 0.85eubuntu36 0.85eubuntu36
2008-04-12 15:36:52 status half-configured initramfs-tools 0.85eubuntu36
2008-04-12 15:37:05 status installed initramfs-tools 0.85eubuntu36
2008-04-12 15:37:42 startup packages remove
2008-04-12 15:37:42 status installed linux-headers-2.6.24-12-generic 2.6.24-12.22
2008-04-12 15:37:43 remove linux-headers-2.6.24-12-generic 2.6.24-12.22 2.6.24-12.22
2008-04-12 15:37:43 status half-configured linux-headers-2.6.24-12-generic 2.6.24-12.22
2008-04-12 15:37:43 status half-installed linux-headers-2.6.24-12-generic 2.6.24-12.22
2008-04-12 15:37:46 status config-files linux-headers-2.6.24-12-generic 2.6.24-12.22
2008-04-12 15:37:46 status config-files linux-headers-2.6.24-12-generic 2.6.24-12.22
2008-04-12 15:37:46 status config-files linux-headers-2.6.24-12-generic 2.6.24-12.22
2008-04-12 15:37:46 status not-installed linux-headers-2.6.24-12-generic <none>
2008-04-12 15:37:46 status installed linux-headers-2.6.24-12 2.6.24-12.22
2008-04-12 15:37:46 remove linux-headers-2.6.24-12 2.6.24-12.22 2.6.24-12.22
2008-04-12 15:37:46 status half-configured linux-headers-2.6.24-12 2.6.24-12.22
2008-04-12 15:37:46 status half-installed linux-headers-2.6.24-12 2.6.24-12.22
2008-04-12 15:37:49 status config-files linux-headers-2.6.24-12 2.6.24-12.22
2008-04-12 15:37:49 status config-files linux-headers-2.6.24-12 2.6.24-12.22
2008-04-12 15:37:49 status config-files linux-headers-2.6.24-12 2.6.24-12.22
2008-04-12 15:37:49 status not-installed linux-headers-2.6.24-12 <none>
2008-04-12 15:37:49 status installed linux-headers-2.6.24-14-generic 2.6.24-14.25
2008-04-12 15:37:49 remove linux-headers-2.6.24-14-generic 2.6.24-14.25 2.6.24-14.25
2008-04-12 15:37:49 status half-configured linux-headers-2.6.24-14-generic 2.6.24-14.25
2008-04-12 15:37:49 status half-installed linux-headers-2.6.24-14-generic 2.6.24-14.25
2008-04-12 15:37:50 status config-files linux-headers-2.6.24-14-generic 2.6.24-14.25
2008-04-12 15:37:50 status config-files linux-headers-2.6.24-14-generic 2.6.24-14.25
2008-04-12 15:37:50 status config-files linux-headers-2.6.24-14-generic 2.6.24-14.25
2008-04-12 15:37:50 status not-installed linux-headers-2.6.24-14-generic <none>
2008-04-12 15:37:50 status installed linux-headers-2.6.24-14 2.6.24-14.25
2008-04-12 15:37:50 remove linux-headers-2.6.24-14 2.6.24-14.25 2.6.24-14.25
2008-04-12 15:37:50 status half-configured linux-headers-2.6.24-14 2.6.24-14.25
2008-04-12 15:37:50 status half-installed linux-headers-2.6.24-14 2.6.24-14.25
2008-04-12 15:37:53 status config-files linux-headers-2.6.24-14 2.6.24-14.25
2008-04-12 15:37:53 status config-files linux-headers-2.6.24-14 2.6.24-14.25
2008-04-12 15:37:53 status config-files linux-headers-2.6.24-14 2.6.24-14.25
2008-04-12 15:37:53 status not-installed linux-headers-2.6.24-14 <none>
2008-04-12 15:37:53 status installed openoffice.org-hyphenation-en-us 2.3.1-2ubuntu1
2008-04-12 15:37:53 remove openoffice.org-hyphenation-en-us 2.3.1-2ubuntu1 2.3.1-2ubuntu1
2008-04-12 15:37:53 status half-configured openoffice.org-hyphenation-en-us 2.3.1-2ubuntu1
2008-04-12 15:37:53 status half-installed openoffice.org-hyphenation-en-us 2.3.1-2ubuntu1
2008-04-12 15:37:53 status config-files openoffice.org-hyphenation-en-us 2.3.1-2ubuntu1
2008-04-12 15:37:53 status config-files openoffice.org-hyphenation-en-us 2.3.1-2ubuntu1
```

---

### Post by gverrilla on 2008-04-13
2 extra things : my mouse is a razerlachesis with builtin-chip,I don't think it's a normal mouse
the click buttons are working once again
and a question :

what happens if I just go and remove a very important package?




cheers ;)

---

### Post by gverrilla on 2008-04-13
I have just thought that it could be a power management problem,since it's a very sophisticated mouse hardware
what do you guys think?

bye

---

### Post by gverrilla on 2008-04-13
fixed!

```
2008-04-13 05:29:41 startup archives unpack
2008-04-13 05:29:41 upgrade guidance-backends 0.8.0svn20080103-0ubuntu14 0.8.0svn20080103-0ubuntu14
2008-04-13 05:29:41 status half-configured guidance-backends 0.8.0svn20080103-0ubuntu14
2008-04-13 05:29:42 status unpacked guidance-backends 0.8.0svn20080103-0ubuntu14
2008-04-13 05:29:42 status half-installed guidance-backends 0.8.0svn20080103-0ubuntu14
2008-04-13 05:29:42 status half-installed guidance-backends 0.8.0svn20080103-0ubuntu14
2008-04-13 05:29:42 status unpacked guidance-backends 0.8.0svn20080103-0ubuntu14
2008-04-13 05:29:42 status unpacked guidance-backends 0.8.0svn20080103-0ubuntu14
2008-04-13 05:29:43 startup packages configure
2008-04-13 05:29:43 configure guidance-backends 0.8.0svn20080103-0ubuntu14 0.8.0svn20080103-0ubuntu14
2008-04-13 05:29:43 status unpacked guidance-backends 0.8.0svn20080103-0ubuntu14
2008-04-13 05:29:43 status half-configured guidance-backends 0.8.0svn20080103-0ubuntu14
2008-04-13 05:29:43 status installed guidance-backends 0.8.0svn20080103-0ubuntu14
```

thank you for you help diabolis and kerry : very grateful am I
;)

---

### Post by Diabolis on 2008-04-13
Cool you got it working. So the problem was in the packages from your last post? did you removed/reinstalled them?

---

### Post by kerry_s on 2008-04-13
fantastic!
and now you know how to use your keyboard for the mouse, just in case it happens again.

---

