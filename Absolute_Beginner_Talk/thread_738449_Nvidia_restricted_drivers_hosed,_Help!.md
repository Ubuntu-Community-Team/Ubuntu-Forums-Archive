---
title: "Nvidia restricted drivers hosed, Help!"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by apokkalyps on 2008-03-28
I'm making a new thread for this, because my goals have changed.  I'm using Gutsy 64 and after installing ubuntustudio-audio, my linux-restricted-modules got jacked up and my nvidia card isn't working right.
(WARNING: ubuntustudio has practicaly ruined my computer, as far as i'm concerned it's a virus, and it's sitting right there in synaptic waiting to ruin yours.  be careful, steer clear of it especially if your on 64)

So anyway, now it will only let me do 640x480 or many smaller screen choices.  I tried uninstalling and reinstalling the drivers but it had no affect.  Does anyone know a special way to blow away those drivers and reinstall it like its a fresh install?  

"Fresh install" leads me to what will probably end up happening, which is frankly a common thing with linux in my experience, having to format and reinstall to fix mysterious problems.  What I wanted to know is, does the ubuntu install cd have a way to reinstall without a format that might fix this problem?  Like how windows will just redo your system files?

If not, and I end up having to format, how hard is it to transfer my user settings to a new ubuntu PC?  In theory it shouldnt be so hard right?  Thats the whole point of the FHS file heirarchy isnt it?  Can I just copy my home directory onto an install with the same packages installed, and the same user name, since most of the user settings are in /home/user/.* ?

Thanks for any information you have on any of these points.  I'm totally stuck right now, and don't know much about linux.
Thanks

---

### Post by kwacka on 2008-03-28
1. is nVidia restricted drivers installed (look under system --> administration --> restricted drivers.

2. if it is installed run ```
dpkg-reconfigure xserver-xorg
``` and let us know if it works.

3. If you make home a separate partition you keep everything.

---

### Post by Inxsible on 2008-03-28
just to add to kwacka's reply, you will need to set additional preferences again after you use the command he gave. for eg, if you have set dual monitors etc.

---

### Post by apokkalyps on 2008-03-28
Ok, the driver was enabled, and I went into a terminal and ran 
> sudo dpkg-reconfigure xserver-xorg
Then I selected yes i want to reconfigure.

It gives me an error which says 

> No X server known for your video hardware

There is either no video hardware installed on this machine (e.g. serial conole only), or the "discover" program was unable to determine which X server is appropriate for the video hardware.  This could be due to incomplete information in discover's hardware database, or because your video hardware is not supported by the available X servers.

Very strange, I promise it was working like compiz awsome for the last month.



Edit: I kept moving through it anyway and it completed (i picked vesa, remembered hearing that somehwere) its rebooting now

---

### Post by apokkalyps on 2008-03-28
Woohoo!  This fixed it!  Mostly anyway.
My compiz settings dont seem to be working however.  They are all still set in ccsm i see, but my wobly windows for example aren't working.  And I only have two virtual desktops even though my "horizantal virtual size" is set to 4.  Do I have to do something to "activate" compiz with its current settings?

Also I'm interested, you were saying if you make your home folder a seperate partition, it makes it easy to keep everything after a system wipe... I hate to ask you to write me an essay about this, so is there a guide anywhere for setting up this kind of portability?  I understand partitioning and stuff, but have a few questions, like do I have to install all the packages exactly the same (or is an installed package listing somewhere in /home)? and how would I go about importing it all back in if?  What issues would it create?  The actual process...

---

### Post by Inxsible on 2008-03-28
since you picked vesa, you need to re-enable the restricted drivers i think.

system>>Adminstration>>Restricted Driver Manager. Enable your drivers and restart X.

Changing to 4 desktops is in CCSM under General Options>> Desktop Size

Horizontal Virtual Size needs to be 4

---

### Post by jimv on 2008-03-28
you could try running 

[INDENT]sudo apt-get install --reinstall nvidia-glx-new[/INDENT]

and then

[INDENT]sudo nvidia-xconfig[/INDENT]

---

### Post by apokkalyps on 2008-03-28
Sure enough, i figured they had to be enabled since my resolution was over 640x480.

Was I wrong to pick vesa?  

I enabled the driver and rebooted, but still no compiz activity.  All my settings are in ccsm, but they are just not active somehow.  I tried changing the desktop size down to 3 and back to 4, but I still only have 2.  What does this mean?

---

### Post by Inxsible on 2008-03-28
have you enabled compiz yet ??

Under System>>Preferences>>Apperance
On the Visual Effects tab, select Extra and then reboot. Make sure that you have already enabled the restricted drivers before you perform this step.

---

### Post by apokkalyps on 2008-03-28
That got it.  Thanks!

---

### Post by Inxsible on 2008-03-28
Sweet !!

Enjoy Compiz :)

---

