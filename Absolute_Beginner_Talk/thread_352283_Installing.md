---
title: "Installing ?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Infernal Byte on 2007-02-03
I'm trying to install Ubuntu frm a live CD but have no idea what I'm doing.  I have created a 15gb partition, but when I ask to create more partitions for the root and swap my pooter tells me I'm not allowed because I'm only allwoed 4 primary partitions.  The options to create other type partitions are ghosted.  I dont want to do an automatic as that will wipe windows, and that wont happen until I've found printer, nVidia Graphics card and WiFi drivers.  Can anyone walk me through?

...

---

### Post by xmastree on 2007-02-03
Don't create a partition. Remove some and create unpartitioned space. The installer will make its own partition in there.

---

### Post by Infernal Byte on 2007-02-03
Thanks for that, but having solved one problem another has occured.  My machine is an AMD64x2 I have 1024 ram and an Nvidia grphics card.  Under the live CD Ubuntu ran fine although the graphics were a bit blocky and the WiFi didn't work.  now that it is installed, it wont load.  After the splash screen and the little orange bar has filled up, the screen goes blank and then slowly turns a pinstripe grey.  Can anyone tell me what to do next? 

...

---

### Post by xmastree on 2007-02-03
ooh, sounds like a graphics issue.

I would disable whatever video driver it's using, and go with the basic vesa driver instead.

I'll assume you have no idea how to go about this, forgive me if that's not the case...


Firstly, you should be able to switch to another 'console' using Ctrl-Alt F2
this should present you with a login prompt.
Log in with the username you created during the install.

Then, type these commands:

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**
enter the password when prompted.
That's backed up the original file.

** sudo nano /etc/X11/xorg.conf**

That should open the file in an editor. Scroll down until you see a sectio  like this:
```
Section "Device"
	Identifier	"S3 Inc. 86C270-294 Savage/IX-MV"
	Driver		"[COLOR="Red"]savage[/COLOR]"
	BusID		"PCI:1:0:0"
```

See where mine says savage? change yours to [b]vesa[/v] *but don't change anything else*. Exit the editor (Ctrl-X), saving the file when prompted.

Then reboot.

If that works, try changing vesa to nv, which is for nvidia cards (unless that's what it used to say...).

---

### Post by Infernal Byte on 2007-02-03
Thanks and your right I know nothing of what I'm doing so I am grateful.  Where is this menu and how do I get to it?  Ubuntu crashes and I assume you dont mean windows!

...

---

### Post by srunni on 2007-02-03
Infernal Byte:
If you cannot use the Ctrl+Alt+F2 shortcut to access a terminal, then there is another way to access the terminal w/o loading the GUI. When you turn on your computer and you get to the point where you can pick whether you want to use Windows or Ubuntu, you should see 4 options:

"Ubuntu, kernel 2.6.17-10-generic" [it's OK if the version number isn't 2.6.17-10]
"Ubuntu, kernel 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Microsoft Windows XP Professional" [or Home or Media Center]

What you need to do is pick "recovery mode" and a terminal will show up. Follow xmastree's directions after that.

---

### Post by xmastree on 2007-02-03
> **Infernal Byte said:**
> Thanks and your right I know nothing of what I'm doing so I am grateful.  Where is this menu and how do I get to it?  Ubuntu crashes and I assume you dont mean windows!

...
There is no menu at this stage.

Ubuntu itself is probably running, but the desktop environment is crashing. Ctrl-Alt-F2 will get you to what looks like a DOS screen.

---

### Post by Infernal Byte on 2007-02-03
Me again, I've tried pushing Cnrl-Alt F2 during the pinstripe screen ant nothing happens, ( I think the problem is terminal by then), If I push just after the splash screen finishes, it forces Ubuntu to start and it runs like it did in Live CD mode, (blocky graphics).  After that there is also a terminal crash during shut down when the log off music sounds.  At exactly what point should I push Ctrl-Alt F2?

...

---

### Post by xmastree on 2007-02-03
It should work when you see the pinstripe effect. I'm assuming that's just an artefact of something wrong with the video settings.
Can you still boot from the live CD? It should be possible to access and modify that file from there.

---

### Post by Infernal Byte on 2007-02-04
Nap.  Is already terminal by the pinstripe, I to think its a graphics problem but I have given up now on that version now.  Thanks for your help.  I'm downloading the latest Ubuntu, (Herd) from distrowatch.com, I'll let you know if how I get on.

...

---

### Post by jvc26 on 2007-02-04
Remember that the Fiesty (Herd3 i think) disk is IN TESTING and therefore is not a 100% stable OS, and that if it works now, an update in the future may well break it, as it is currently in testing.
Il

---

### Post by Infernal Byte on 2007-02-04
Well its herd is meant for 64bit but it it wont even load at all, I might try again in April.  Am I damaging my laptop by having to switch of via the power key after crashing?

Thanks for the input.

...

---

