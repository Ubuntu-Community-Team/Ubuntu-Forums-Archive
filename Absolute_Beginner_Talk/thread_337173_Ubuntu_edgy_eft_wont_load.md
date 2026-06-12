---
title: "Ubuntu edgy eft wont load"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by brisingr_dagger on 2007-01-12
](*,) i recently installed ubuntu edgy eft onto my computer as a second os but now it wont load past the login screen it just keeps rebooting and i cant find away round it i can get onto my second user name fine but i have no admin privileges can anyone offer me any info on how to get around it or how to fix it because im stumped

---

### Post by fsando on 2007-01-12
I'm not sure about the character of your problem - are both your os'es linux or is one windows?
Does your second user name refer to your other os? Or do you have two user names for ubuntu?
If you can log in to ubuntu you generally gain super user access from the command console by putting the command **sudo** in front of other commands for instance if you want to edit setup of the x-server files you would issue the following:
sudo - gives super user status
gedit - opens gnome text editor
```
sudo gedit /etc/X11/xorg.conf
```

Another possible problem you may have is something to do with your graphics card and driver. 
What is your system (graphics card, screen etc)?

You could try to disable splash screen and let the boot process print out everything it does:
Do this:
When the grub boot menu appears press 'e' for editing
Then edit the standard boot: remove 'quiet' and 'splash'
And let the boot process run - see where exactly it stops

Another possibility is to boot in recovery mode - you end up at a root account in pure text mode from where you can do necessary changes - but lets first see what this brings up

---

