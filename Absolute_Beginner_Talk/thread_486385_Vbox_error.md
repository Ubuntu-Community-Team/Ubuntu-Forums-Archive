---
title: "Vbox error"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Nigmah on 2007-06-27
[COLOR=DarkOrange][B]WHenever i try to boot up a virutal xp i get this error. 

Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either do 'chmod 0666 /dev/net/tun' or change the group of that node and get member of that group. Make sure that these changes are permanently in particular if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 [/B][/COLOR]
[COLOR=DarkOrange]**any help?**[/COLOR]

---

### Post by ajmorris on 2007-06-27
hi :)
go to menu >> system >> administration >> users and groups
then scroll down to vboxusers and select properties.
then tick the box with your name to add you to the group members. 
then start virtual box again.

EDIT: oops..... didn't read the post properly, bodhi.zazen, has the right idea.

---

### Post by bodhi.zazen on 2007-06-28
> **Nigmah said:**
> [COLOR=DarkOrange][B]WHenever i try to boot up a virutal xp i get this error. 

Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either do 'chmod 0666 /dev/net/tun' or change the group of that node and get member of that group. Make sure that these changes are permanently in particular if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 [/B][/COLOR]
[COLOR=DarkOrange]**any help?**[/COLOR]

Open a terminal.

```
sudo chown root.vboxusers /dev/net/tun
sudo chmod 660 /dev/net/tun
```

If you add those commands to _*/etc/rc.local_* permissions will be set at boot.

---

### Post by Nigmah on 2007-06-28
[COLOR=DarkOrange][B]anyways while im here and it is related to the subject i been struggling to  fix this error everytime i try to install xp in vb

[/B][/COLOR] TRAP_CAUSE_UNKNOWN 
 
If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps: 
 
Check to make sure any new hardware or software is properly installed. If this is a new installation ask your hardware or software manufacturer for any Windows updates you might need. 
 
If problems continue, disable o remove any newly installed hardware or software. Disable BIOS memory options such as caching or shadowing. If you need to use Safe Mode to remove or disable components, restart your computer, press F8 to select Advanced Startup Options, and then select Safe Mode. 
 
Technical information: 
 
*** STOP: 0x00000012 (0x00000001,0x00000000,0x00000000,0x00000000) 

[COLOR=DarkOrange][B]I believe it may be related to a bios error i get everytime i start up ubuntu 

[/B][/COLOR][B]MP-BIOS bug: 8254 timer not connected to IO-APIC
(though its missing a couple number at the beggining in [  ])
[/B]

---

### Post by Nigmah on 2007-06-28
[COLOR=DarkOrange]**bump**[/COLOR]

---

### Post by Nigmah on 2007-06-28
bump

---

### Post by leetcharmer on 2008-03-21
This is the error I get when running in Host Interface Mode after following this tutorial:
[http://spinczyk.net/blog/2008/03/05/setting-up-a-bridged-network-for-virtualbox-on-ubuntu-linux/](http://spinczyk.net/blog/2008/03/05/setting-up-a-bridged-network-for-virtualbox-on-ubuntu-linux/)
```
Unknown error creating VM (VERR_HOSTIF_INIT_FAILED).
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

Not sure how to fix.  Any ideas?

---

