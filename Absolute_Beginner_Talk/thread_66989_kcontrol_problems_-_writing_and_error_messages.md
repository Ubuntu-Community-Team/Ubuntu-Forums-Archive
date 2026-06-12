---
title: "kcontrol problems - writing and error messages"
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by canuck45 on 2005-09-19
Very new to linux and ubunto.

Downloaded and installed ubuntu - went great
dowloaded KDE desktop and its up and running fine (don't like the looks of Gnome)
No KControl icon anywhere that I can find.

I can launch kcontrol from a terminal window though and went to make some changes in my mouse behaviour

i used kdesu kcontrol to launch the program and made the changes OK (I think)


however I tried to use kcontrol as a user and got an error message,
Will not save configuration.
Configuration file "/home/adrian/.kde/share/config/kcontrolrc" not writable. 
Please contact your system administrator.

 Clicked close/ok and it opened Kcontrol, made some changes and oops things went downhill from there.

Now each time I boot as it loads I get an error message pop up
/home/adrian/.kde/share/config/kaccessrc not writable

What have I messed up and any ideas on how to fix it, I am lost

2)and is there a way to get KControl into the K-Menu, ie not having to use terminal...


Not only am I gnu to linux but am also old so I learn slowly.

Thanks

Adrian
ps if necessary I can use the command line (why didn't I pay more attention in school)

---

### Post by canuck45 on 2005-09-19
well I got brave and renamed kaccessrc to kaccessbak, not having a clue what it does and now it no longer appears and everything still seems to be working.
Probably not the best solution as I have no idea what kaccessrc does or is.

Any explanations appreciated.
Still working on second problem kcontrol icon on menu :)

well I now have kcontrol added to my menu also...the logic of linux is beginning to make sense.

---

### Post by cwaldbieser on 2005-09-19
[QUOTE=canuck45]well I got brave and renamed kaccessrc to kaccessbak, not having a clue what it does and now it no longer appears and everything still seems to be working.
Probably not the best solution as I have no idea what kaccessrc does or is.

Any explanations appreciated.
Still working on second problem kcontrol icon on menu :)

well I now have kcontrol added to my menu also...the logic of linux is beginning to make sense.[/QUOTE]
Files that end in "rc" are often configuration files.  E.g. ".bashrc" is the configuration file for bash.

---

### Post by mlomker on 2005-09-19
> Configuration file "/home/adrian/.kde/share/config/kcontrolrc" not writable. 


This command in a terminal will make it writable:

```

sudo chmod 777 /home/adrian/.kde/share/config/kcontrolrc

```

---

### Post by canuck45 on 2005-09-19
Thank you for that info

---

### Post by Ptero-4 on 2005-09-19
[QUOTE=canuck45]Very new to linux and ubunto.

Downloaded and installed ubuntu - went great
dowloaded KDE desktop and its up and running fine (don't like the looks of Gnome)
No KControl icon anywhere that I can find.

I can launch kcontrol from a terminal window though and went to make some changes in my mouse behaviour

i used kdesu kcontrol to launch the program and made the changes OK (I think)


however I tried to use kcontrol as a user and got an error message,
Will not save configuration.
Configuration file "/home/adrian/.kde/share/config/kcontrolrc" not writable. 
Please contact your system administrator.

 Clicked close/ok and it opened Kcontrol, made some changes and oops things went downhill from there.

Now each time I boot as it loads I get an error message pop up
/home/adrian/.kde/share/config/kaccessrc not writable

What have I messed up and any ideas on how to fix it, I am lost

2)and is there a way to get KControl into the K-Menu, ie not having to use terminal...


Not only am I gnu to linux but am also old so I learn slowly.

Thanks

Adrian
ps if necessary I can use the command line (why didn't I pay more attention in school)[/QUOTE]
 What happened in your system is this. When you typed kdesu kcontrol you actually ran kcontrol as root, This caused the kcontrolrc file (the kcontrol config file) to become owner by root and thus to become read-only to your user account. To remedy this you just needed to delete it (kcontrol re-creates it). As for the menu item it's quite simple. Just create a new launcher and in the launcher properties look for the "command" field (or something like this. I'm far from the kde boxes at work) and put kcontrol in it (don't put "run as root" you don't need root privileges b/c kcontrol only acts on your personal settings which are stored in your home folder).

---

### Post by canuck45 on 2005-09-20
Thanks guys for putting it into plain english with clear instructions to follow.

Ptero-4  oops I had done similiar to what you said but sure enough I had put the command as kdesu kcontrol and had to enter passwords everytime.  Fixed it per your suggestion and everything is working fine.

Now for more serious stuff, finding plugins and installing, setting file associations....well I was tired of going to bed at a reasonable hour anyway, now I can stay up till 2 am again.

---

