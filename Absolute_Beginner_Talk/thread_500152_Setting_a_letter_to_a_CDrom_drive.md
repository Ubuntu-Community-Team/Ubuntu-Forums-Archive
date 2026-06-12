---
title: "Setting a letter to a CDrom drive"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by beastrace91 on 2007-07-13
I am using the program WINE ([www.winehq.org](www.winehq.org)) to install my games on my kubuntu system and it is working rather well how ever I am running into one small error while trying to install my game Diablo 2. I have to know how to set a drive letter to my CDrom drive for wine to work with it properly.  Any one know how to do this on Kubuntu 7.04?

Thnx Much,
~J3ff

---

### Post by goodfella on 2007-07-13
I am not to sure about Kubuntu since I use Gnome but I think wine should handle it the same for both.  The easy way is to open a terminal (Applications->Accessories->Terminal) and type in the following command to open the wine configuration program:
```
$ winecfg
```

Then follow the steps below:
[LIST=1]
[*]Navigate to the 'Drives' tab
[*]Click 'Add'
[*]In the '_P_ath' text box specify the path to the cd drive mount point (most likely /media/cdrom0 or /media/cdrom1)
[/LIST]

After that you should be good to go.

If you don't have winecfg for some reason or you want to specify the drive letter you could do it the harder way:

[LIST=1]
[*]Navigate to ~/.wine/dosdevices
[*]Type the following in a terminal ```
$ sudo ln -s [path to cd drive] [drive label]
```
[/LIST]

[path to cd drive] is the mount point to the cdrom drive you want to label either /media/cdrom0 or /media/cdrom1 depending on your configuration.

[drive label] is the label you want to give the drive like D: or E:

Hope this helps.

---

### Post by beastrace91 on 2007-07-13
Thank you so much that helped alot!

~J3ff

---

### Post by beastrace91 on 2007-07-13
Also one more nooby question...

How do I cd to my CDrom drive(in terminal) once I have a letter set to it?

Thnx,
~J3ff

---

### Post by goodfella on 2007-07-13
You can cd into the drive either through the drive mount path or through .wine/dosdevices/[drive label]

---

### Post by goodfella on 2007-07-13
I would recommend looking into the ln command if you don't already know about it by typing "man ln" in a terminal.  You also want to make sure you understand mount points specifically what they are, how the are used, and how to create them.

---

