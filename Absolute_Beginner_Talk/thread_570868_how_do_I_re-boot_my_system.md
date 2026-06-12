---
title: "how do I re-boot my system?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by njmacrai on 2007-10-08
Sorry for being such a newbie, but how do I re-boot my LINUX operating system? What are the risks? My OOo is frozen and rebooting seems the only option left to me.

---

### Post by Dr Small on 2007-10-08
Umm, nothing ? O,o

How ?
```
sudo reboot
```

or System > Quit > Reboot

Dr Small

---

### Post by rsambuca on 2007-10-08
Whoa, that is your last resort.  Well, actually second last resort, prior to pulling the plug.

A couple things you can try.  Restart X (control-Alt-backspace), although you will lose any unsaved changes.

Drop to a terminal and kill the process.  Control-Alt-F1

---

### Post by mivo on 2007-10-08
If you use a default Ubuntu installation, use the red button in the right upper corner. If you shut down normally, there should be no problems. But you can also go into *System -> Administration-> System Monitor* and then end/kill the process that hangs.

---

### Post by Shazaam on 2007-10-08
Do you have ANY mouse keyboard control?
If not hold down the ALT+SysRq (Print Screen) keys and type in  REISUB
What this does is gracefully shuts down and reboots your pc. Write it down.
Check here... [http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

---

### Post by Dr Small on 2007-10-08
Or
```
ps aux | grep openoffice
```
Then:
```
kill *pid-number*
```

---

### Post by coffeecat on 2007-10-08
There's a panel app you can use to force-quit misbehaving apps, so you don't necessarily have to reboot.

So long as you're using Gnome, right-click on whichever panel you want the force-quit icon. Choose "Add to Panel" and then choose "Force Quit" and click on the "Add" button. If you have a frozen app, just click on the icon and follow the (simple) instruction.

I always add this to any fresh Linux install, whatever the distro.

---

### Post by psyke83 on 2007-10-08
> **njmacrai said:**
> Sorry for being such a newbie, but how do I re-boot my LINUX operating system? What are the risks? My OOo is frozen and rebooting seems the only option left to me.

Yes, but you may lose your recently edited document. OpenOffice.org has a document recovery feature, though, so you may be able to get it back when you open the program again.

It may be easier to close OpenOffice.org instead of rebooting. Just click on the close button and confirm closing the non-responsive program.

---

### Post by philinux on 2007-10-08
with your pinkies hold down alt and the "sys rq" key the print screen key.

While holding them down type r e i s u b 

This will stop all apps safely unmount your drives and then restart the pc.

nothing really happens until the b is pressed .

---

### Post by maharbA on 2007-10-08
If it's just OOo that's frozen, there are a few things you can do:

Go to System>Administration>System Monitor and select OOo from the list of processes, then click "end process" near the bottom-right (this is very much like Windows)

Hit Alt+F2, then type "xkill" (no quotes) and hit Run. Your cursor will turn into a skull & crossbones, click on the program you want to "kill" (NOTE: BE CAREFULL WHAT YOU CLICK ON! You can kill anything on your screen, including your desktop or panels!)

If all else fails (or if you computer is really locked up) hit Ctrl+Alt-Backspace (NOT delete). This will restart X and get you back to your login prompt.

Hope that helps

---

