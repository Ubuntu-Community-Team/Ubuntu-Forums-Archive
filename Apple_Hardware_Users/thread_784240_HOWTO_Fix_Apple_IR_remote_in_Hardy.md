---
title: "HOWTO: Fix Apple IR remote in Hardy"
date: 2008-05-06
forum: Apple Hardware Users
---

### Post by benanzo on 2008-05-06
Unfortunately the Apple IR remote doesn't work out-of-the-box in Hardy on my MacBook 1,1 so I went about trying to figure out why.  I came across [[COLOR="SeaGreen"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=607797") thread which addresses the problem but requires some steps unnecessary for the Hardy kernel, which can lead to some complications down the road.  I actually found a really simple solution in the bug report on launchpad for this problem [[COLOR="Green"][COLOR="SeaGreen"]here[/COLOR][/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/157919").  Just to simplify things, I'll give the quick fix here.

Basically the problem is just that the **appleir** module is loaded too late in the initial modprobe process.  It needs to be loaded *before* **applesmc** and **usbhid**.  In order to get it to load before those other two we have to change the order a bit.

Open a terminal (Applications -> Accessories -> Terminal) and do:
```

$ sudo nano /etc/modprobe.d/blacklist

```
Scroll to the bottom of that file and add the following:
```

# To fix the IR receiver we have to load appleir _before_ these two (see /etc/modules)
blacklist applesmc
blacklist usbhid

```
Press **ctrl-o** (to save) then **ctrl-x** to exit nano.

The only important part is the two **blacklist** lines.  The other is just there to remind you why you did this in a few months when you're wondering why usbhid is blacklisted.

Now we're going to change the order in which these modules load.  With your terminal still open do this:
```

$ sudo nano /etc/modules

```
Add the following lines to the bottom of this file:
```

# Apple modules need to be loaded in this order for the IR receiver to work
appleir
usbhid
applesmc

```
Press **ctrl-o** then **ctrl-x** again to save and exit nano.

Reboot.

You can try unloading then reloading these modules in the correct order by hand but you might have a hard time  controlling your machine once **usbhid** is unloaded!  I certainly did.  I couldn't get it to reload (no keyboard, duh) so I had to reboot anyway.

NOTE: This process *may* cause the numlock to stay on after resuming from suspend forcing you to reboot in order to restore normal operation.  I can't find a workaround for this (putting the load order in /etc/rc.local instead of doing the blacklist/modules thing doesn't seem to fix it.)  If you have problems please report it on the launchpad bug mentioned above.

Good Luck!

---

### Post by mkgkg on 2008-05-06
does it works also for the newest macbook, like mine 3,1 santarosa and the last one?

---

### Post by cyberdork33 on 2008-05-06
> **mkgkg said:**
> does it works also for the newest macbook, like mine 3,1 santarosa and the last one?
try it.

---

### Post by MTZeon on 2008-05-08
Nice guide. Works on Black Macbook 2008 gen.

---

### Post by yousufinternet on 2008-05-08
when i do

sudo gedit /etc/modules 

i get an error when i try to save the file 
[B]> 
You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.[/B]

although i have used sudo

update : ok it worked now!!
i am going to reboot and see

thanks very much

---

### Post by yousufinternet on 2008-05-08
wow the remote is working perfectly with totem and with volume manager 

is their any way to allow the remote to control Elisa Media Center??? 

thanks in advance

---

### Post by deltaiscain on 2009-02-25
so, does this work well? I'm not to fond of making my keyboard unusable. Will it work again after reboot? And does it automatically find my apple remote then? Thanks

---

### Post by letorbi on 2009-03-27
Be careful with disabling your keyboard when you're using an encrypted logical volume. I wasn't able to enter my password after I had blacklisted the modules and it took me almost the whole afternoon to find a way back to my data...

---

### Post by moviemaniac on 2010-01-19
Is there a new method for getting the remote to work? I can't seem to find the "appleir" module in lucid, modprobe tells me it's not available. Any hints?

//edit: got it to work by letting lirc autodetect the hardware. However, pressing buttons on the remote don't seem to trigger anything - even though the lirc remote control properties application registers I'm pressing the buttons. Weird.

---

