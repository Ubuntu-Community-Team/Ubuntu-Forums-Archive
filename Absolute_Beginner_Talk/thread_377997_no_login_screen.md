---
title: "no login screen"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by MrWashy on 2007-03-06
Hi all,

I'm having a slight problem.  After installing StartUp Manager (I posted there as well, but haven't heard back yet) I don't have a login screen.  I get the boot screen (is this the usplash?) withthe orange scrolling bar, but after that, nothing.  I can boot into the restore console but I'm not sure what to do from there.  

I'm guessing that somehow I deleted (or simply forgot to specify) which splash to use for the login screen.  (I'm not going to blame StartUp Manager, it's probably something I did!)

Can anyone tell me what to check to see if this is what I did?  And possibly how to repair/restore my login screen?

(Did that make sense?)

Thanks!
Rich W.

---

### Post by taurus on 2007-03-06
Do you get into a restore console by pressing <Ctrl><Alt>F2?  If not, what happens if you press those three keys?  Do you see a login screen where you have to enter your username and password.  And after you log in, what's the output of this command?

```
startx
-or-
ps -A
```

---

### Post by MrWashy on 2007-03-06
I can only get to the restore console by the grub menu item.  Pressing <Ctrl><Alt>F2 gives me a blank screen with a blinking cursor, no login.   <Ctrl><Alt>F1 will bring me back to the restore console.   

If I type startx from the restore console (via grub) I will get the blank screen that eventually goes into its own suspend mode because it's not receiving a signal.  (The monitor itself gives the message "no signal", not ubuntu)

The ps -A command gives me a list the brginning of which I can't see (it's off the top of the screen) .  Do you need the whole screen adn info, or am I looking for something in particular?

---

### Post by MrWashy on 2007-03-06
The output of the ps command is as follows:

   9	?	00:00:00	kblockd/0
  10	?	00:00:00	kacpid
  11	?	00:00:00	kacpi_notify
 128	?	00:00:00	kseriod
 161	?	00:00:00	pdflush
 162	?	00:00:00	pdflush
 163	?	00:00:00	kswapd0
 164	?	00:00:00	aio/0
1630	?	00:00:00	ata/0
1795	?	00:00:00	khubd
1889	?	00:00:00	kjournald
2161	?	00:00:00	udevd
2967	?	00:00:00	shpchpd
2997	?	00:00:00	kgameportd
3055	?	00:00:00	kpsmoused
3079	?	00:00:00	scsi_eh_0
3080	?	00:00:00	usb-storage
3411	?	00:00:00	dhclient3
3526	?	00:00:00	mount.ntfs-3g
3529	?	00:00:00	mount.ntfs-3g
3532	?	00:00:00	mount.ntfs-3g
3920 	ttyl	00:00:00	sh
3922	ttyl	00:00:00	bash
3935	ttyl	00:00:00	ps

I retyped that onto my laptop from my recovery console display.

---

### Post by MrWashy on 2007-03-06
Woohoo!  Got it!  I was able to get it back using

```
dpkg-reconfigure xserver-xorg
```

---

