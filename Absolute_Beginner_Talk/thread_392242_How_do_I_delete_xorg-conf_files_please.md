---
title: "How do I delete xorg-conf files please?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-03-24
Hi

I have more than my fair share of xorg-conf files. I also have a xorg-conf-custom file that i would love to delete.

In Nautilus it tells me that I don't have permission to do this.

I have tried to cd etc/x11 in the terminal but I am told the folder doesn't exist.

How do i delete xorg-conf files please?

Regards
Bob

---

### Post by lamalex on 2007-03-24
/etc/x11 doesnt exist, but /etc/X11 does. linux is case-sensitive. cd into there and sudo rm the file. alternatively, gksudo nautilus will give you root permissions in the gui.

---

### Post by Kobalt on 2007-03-24
Try this in terminal : 
```
cd /etc/X11
sudo rm *name-of-the-file*
```
But if you delete your xorg.conf file, don't forget to generate a new one right after with ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bwallum on 2007-03-24
Hole in one! Thank you. I deleted all the surplus xorg.conf.numbers files and the custom file. I have a residual problem:

When I entered
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

after deleting the files I I got the following result:- 

> xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070324152219

Does this mean I still have a 'custom configuration' problem. If so how can i delete it and return to the default xorg.conf?

Rgds
Bob

---

### Post by bulldog on 2007-03-24
Running the command will make a copy of your existing xorg.conf which you have customized,that's all the warning means.
So every time you run this reconfigure command,it will make a new copy and you'll get a warning.

---

### Post by bwallum on 2007-03-24
Thanks Bulldog.

I still had the following error.

BEGINNING OF ERROR MESSAGE

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

END OF ERROR MESSAGE

So I thought, hmm if a bug you would have been on it by now therefore consider 'incompatible libxkbfile implementation'

I removed and then reinstalled libxkbfile 1 and rebooted. Lo, verily the problem was gone! So was the GUI which has finally removed any persistence and determination that I would get Ubuntu to work. I'll let Feisty settle in and come back and try again in a couple of months. If you have any clout in the organisation and if the organisations goals are to get widespread take up of Ubuntu then may I suggest you tell 'em that they need to produce an OS that doesn't require a degree in Linux to get up and running. it's like walking through a minefield. You may have seen how the newbies blow up and so can plot a safe course through it. The newbie has no chance other than luck. Ubuntu will just get the same name as the early Microsoft Windows and that will be a shame - we need some decent competition to friend Bill before his big brother software gets implanted between our ears.

I wish you luck and thanks for all your help.

Best regards
Bob

---

### Post by bulldog on 2007-03-24
Well,I'm sorry you think that ubuntu is hard to use.
I have had SuSe,Fedora, Ubuntu Dapper,Edgy and now running Feisty.

Can't say I had no trouble with them,but then again I have had my share of BSOD's in Windows as well.

You'll have to keep in mind you can't learn an whole new OS in one day.
If you're looking for an OS,but won't invest some time to learn and understand it,well,hate it to say,but you'll be better of with Windows.

Linux isn't for everyone,only when you're willing to learn ,you'll learn to appreciate it and most certainly will get it at work the way you want.

---

### Post by bwallum on 2007-10-08
Just to let you know i got over my little tantrum and I am now riding the Gutsy beta. You are right, this is the OS of the future, I just need to learn some more, that's all! Thank you again for your help.

Regards
Bob

---

