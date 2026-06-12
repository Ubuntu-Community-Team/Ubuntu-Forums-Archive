---
title: "auto915Resolution"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2007-03-15
Hey everyone! I'm new to Ubuntu (and linux for that matter) and have a Dell Inspiron 1300 with an intel chipset.

I've used the auto915resolution script to fix my screen resolution. This is found here:
[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

After rebooting, Ubuntu shows me the splash screen but then goes into what looks like the Terminal program (except in full screen) and asks me to log in.

Essentially, I wanted to ask how I would go about undo'ing what i've done so that I can boot normally with the normal ubuntu login and access the GUI. Quite frankly, I have NO IDEA how to use linux in terminal so i'm really stuck :(

---

### Post by rexey on 2007-03-15
I'll take a stab at this.  
The program may have updated the ever lovely xorg.conf file.
Login at that terminal screen

type
cd /etc/X11
then
ls -l

you should get a detailed directory listing.  
The xorg.conf file should have 1 or more variations. for example, I have the following
xorg.conf 
xorg.conf~  
xorg.conf.fglrx-0, 
xorg.conf.original-0

my xorg.conf.original-0 has the timestamp 2mins before the current file.
If I wanted to go back to that one I'd do this.

sudo cp /etc/X11/xorg.conf xorg.conf.backup031507

(why you want to backup a broken xorg file is beyond me, it's probably just habit)

sudo mv /etc/X11/xorg.conf.original-0 xorg.conf

then reboot.

-Rexey

---

### Post by rexey on 2007-03-15
assuming that works, then load 915resolution using Synaptic Package Manager
pretty sure it's in there.  If not, make sure the universe repositories are enabled.

-Rexey

---

### Post by rexey on 2007-03-15
assuming that works, then load 915resolution using Synaptic Package Manager
pretty sure it's in there.  If not, make sure the universe repositories are enabled.

-Rexey

---

### Post by evolvedlight on 2007-03-15
> **tonycm1 said:**
> Hey everyone! I'm new to Ubuntu (and linux for that matter) and have a Dell Inspiron 1300 with an intel chipset.

I've used the auto915resolution script to fix my screen resolution. This is found here:
[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

After rebooting, Ubuntu shows me the splash screen but then goes into what looks like the Terminal program (except in full screen) and asks me to log in.

Essentially, I wanted to ask how I would go about undo'ing what i've done so that I can boot normally with the normal ubuntu login and access the GUI. Quite frankly, I have NO IDEA how to use linux in terminal so i'm really stuck :(

I have the same laptop. All you need to do is install 915resolution after enabling the extra repositories. No scripts needed. If you need any more info PM me

Steve

---

### Post by tonycm1 on 2007-03-15
Hey Rexey,
In my /etc/X11 folder, I only have 2 xorg files:
xorg.conf
xorg.conf.1

Both of them have the exact same timestamp except xorg.conf's size is 3991 whereas xorg.conf.1 is 4309.

Is there maybe an alternate way to remove this installation and get my Ubuntu back to normal so that I can see my GUI?

Tony

---

### Post by rexey on 2007-03-15
xorg.conf.1 is the original working one.  xorg.conf is the one the system is using (and broken)
conf.1 will be the one you rename to xorg.conf like so

sudo mv /etc/X11/xorg.conf.1 xorg.conf

---

### Post by tonycm1 on 2007-03-15
Worked like a charm! Thanks Rexey!

Now that i've reverted back to the original 915Resolution, how would I switch from 1280x800 to either 1280x1024 or something slightly larger (1600x1200 etc..)?

Thanks again!!
Tony

---

### Post by rexey on 2007-03-16
Evolvedlight,
Can you shed some er..light! on this?
I'm unfamilair with the Inspiron hardware (I'm using an HP Compaq)
Our widescreen nc6400's are native 1280x800 and don't go any higher.
The highest I can get with the the nc6220 and nc6000 is 1024x768 since they're the standard square box. 

-Rexey

---

