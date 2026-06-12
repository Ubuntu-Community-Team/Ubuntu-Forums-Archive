---
title: "Colour Problem"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by risk on 2007-08-14
Despite reading "DON'T HAVE ROOT ACCESS" everywhere, I went and got root access... I was messing with my graphics card settings but I messed it up so much the GUI didn't display after restarting, only a command line.

I reinstalled from my cd and have since used [envy]("http://albertomilone.com/nvidia_scripts1.html") to install correct nvidia drivers  however there is still an orange ---> purple ---> green gradient running along my screen :confused:


Just restarted again and I'm getting an old fashioned looking screen saying Xserver failed, this happened last time O_o

The error report says "Failed to load NVIDIA Kernel module!"

Screens found, but none have a usable configuration..... 

I now have only a command line again lol XP for me I think ;D

---

### Post by ThinkBuntu on 2007-08-14
> **risk said:**
> Despite reading "DON'T HAVE ROOT ACCESS" everywhere, I went and got root access... I was messing with my graphics card settings but I messed it up so much the GUI didn't display after restarting, only a command line.

I reinstalled from my cd and have since used [envy]("http://albertomilone.com/nvidia_scripts1.html") to install correct nvidia drivers  however there is still an orange ---> purple ---> green gradient running along my screen :confused:


Just restarted again and I'm getting an old fashioned looking screen saying Xserver failed, this happened last time O_o

The error report says "Failed to load NVIDIA Kernel module!"

Screens found, but none have a usable configuration..... 

I now have only a command line again lol XP for me I think ;D
Damn! Sounds like things got pretty messed up. Maybe you should remove and reinstall Xorg? I'd ask some more experienced people in this forum, but a reinstall of all of your graphical utilities should be the obvious fix.

---

### Post by Hospadar on 2007-08-14
Edit: you might also try reinstalling xorg with something like ```
apt-get --reinstall install xserver-xorg
```In addition, you may want to rename (not delete, just rename it so you don't loose it if things don't work) your /etc/X11/xorg.conf file before you reinstall so that the installation creates and configures a fresh one for you
/edit


Well probably you horribly mangled your x configuration, hopefully there is a backup copy somewhere, try looking in:
/etc/X11/   (this is where the actual xorg.conf is stored, and often backups are saved here under names like xorg.conf.backupXX or whatever)  try poking around this folder for an old backup

Also have a look in 
/var/backups
/var/backups/xorg

If and when you find one you'll want to do:
```

sudo cp <whatever the name of the backup is> /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart

```
The second line there restarts gnome (which you will need to do for your changes to take effect

Also, you may want to run "sudo dpkg-reconfigure xserver-xorg" and let it pick all the defaults, use the "nv" video driver, don't monkey with monitor settings, and see if that gets you back to normal, at which point you can use envy to properly install your video drivers.

Also, for future reference, you never want to give yourself root priviledges, but rather you should prepend "sudo" (command line) or "gksu" (for gui apps) to commands so that those individual commands gain root priliedges.  For example if you want to edit a system file you would do "sudo gedit <file>"

At this point it sounds as if it might be best to reinstall fresh, and then use envy right off the bat.  I bet your stuff would work just fine.

If you arn't familiar with the linux command line, check out [this]("http://lug.mtu.edu/slides-fall05/basic-commands.html") site for a little basic info, it should be able to let you do the kind of stuff you will need to copy backups and whatnot.

You could also use a livecd to go into your hard drive graphically and change these files (just make sure you are changing the ones on the hard drive, not the temporary ones the livecd is using (things you want to edit will be somewhere like /media/hda0/whatever if you do things this way)

---

