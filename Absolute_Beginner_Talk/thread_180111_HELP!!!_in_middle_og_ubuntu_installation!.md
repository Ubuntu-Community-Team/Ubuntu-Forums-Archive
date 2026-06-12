---
title: "HELP!!! in middle og ubuntu installation!"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by johanhartman on 2006-05-21
I'm in the middle of installing ubuntu on one of my other computers. I've done all the necesary parts and I'm now at the stage where GRUB should load for the first time but nothing is happening. The PC is still on but its idling and the monitor is blank.

Please help quickly, as I said I'm still in the middle of installation.:mad:

---

### Post by peterj on 2006-05-21
im no genious but if the boot disc is still in take it out and if the boot disc is out put it in!
nothing else you can do really

---

### Post by johanhartman on 2006-05-21
I only have the disc to which I have burned the iso image, i've gone past the installation section where the disc should be removed. Are you sure I should insert the disc again?

---

### Post by peterj on 2006-05-21
nope...ya got me there, hmm....i reckon your gonna have to start again..i'd be sympathetic but it took me 3 goes and i never changed anything the time it works...
maybe your computer doesn't like you..get a toshiba they're like lovable dogs. :confused:

---

### Post by johanhartman on 2006-05-21
Incedentally, I have chosen to dual boot and used "[http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm") All my OSes (windows xp home edition) were correctly detected.

---

### Post by johanhartman on 2006-05-21
Might Rebooting help. GRUB is already installed. Or would that be a big mistake?

---

### Post by confused57 on 2006-05-21
I don't know for sure, I'm don't know how far into installation you were; but, yes I'd reboot without the CD inserted.  If Grub is installed, there is an option of entering Grub during bootup by pressing "Esc"(you only have 3 seconds to do so), this will get you to the Grub menu, if it is installed.  Try selecting Windows to boot into first, if that is successful, you can try booting into Linux at your next reboot(forget this suggestion, you didn't indicate you were dualbooting).  Then you can troubleshoot further, once you've established that.

---

### Post by johanhartman on 2006-05-21
I've rebooted and GRUB started:D  Then I selected Ubuntu. 
The ubuntu logo appeared (where modules are loaded), then the screen went blank again and its idling again](*,)

---

### Post by confused57 on 2006-05-21
It looks like you have Ubuntu installed, but it appears you may to reconfigure your video settings.

When you get to the blank screen, try pressing Ctrl+Alt+F1; hopefully, this will get you to a command prompt.

At the prompt, enter:    sudo  dpkg-reconfigure  xserver-xorg      (I have 2 spaces between entries, should only be one space), press "enter"

You'll have to enter your user password to run as "sudo".   When you have the option to select a video driver:  try  "vesa"   or  "nv"  ,  if you have an ati card: try "ati"  or  "radeon"

Select your monitor resolutions, don't go higher than your monitor supported native resolution.

Then try typing "startx"(without quotes) at the prompt, hit enter(this is the command to start the GUI).

I don't know if any of this will work...

Try to see exactly where in "loading modules" that the screen goes blank, that may help determine the problem.

---

### Post by Galactus on 2006-05-21
I've been having the same problem since I tried to install Kubuntu on Fri night. See my post in the installation forum. I will be interested to see what the outcome to this problem is. I am not dual booting - installing on fresh 80 Gig Maxtor HD...I am soon to try another KDE distro...

---

### Post by johanhartman on 2006-05-21
[QUOTE=confused57]It looks like you have Ubuntu installed, but it appears you may to reconfigure your video settings.

When you get to the blank screen, try pressing Ctrl+Alt+F1; hopefully, this will get you to a command prompt.

At the prompt, enter:    sudo  dpkg-reconfigure  xserver-xorg      (I have 2 spaces between entries, should only be one space), press "enter"

You'll have to enter your user password to run as "sudo".   When you have the option to select a video driver:  try  "vesa"   or  "nv"  ,  if you have an ati card: try "ati"  or  "radeon"

Select your monitor resolutions, don't go higher than your monitor supported native resolution.

Then try typing "startx"(without quotes) at the prompt, hit enter(this is the command to start the GUI).

I don't know if any of this will work...

Try to see exactly where in "loading modules" that the screen goes blank, that may help determine the problem.[/QUOTE]

I tried the ctrl+alt+F1 thing and went through a loooong setup, the setup was done and when I typed "startx" a lot of error messages appeared, apparently a lot of the option i selected failed or something. This is the part where I get pretty stressed. Its late and I just want to bail out for now will it work to reboot and start again some other time?

PS: the screen goes blank after loading the modules.

---

### Post by richbarna on 2006-05-21
I would do the install again from scratch, but this time choose the "server" only install and then add the desktop-environment afterwards.
This seems to work with laptops and their finniky graphics cards.

---

### Post by johanhartman on 2006-05-21
This is the message I get: 

"
Fatal server error:
Server is already active for display 0
   If this server is no longer running, remove /tmp/.x0-lock
   and start again.

Please consult the The X.Org Foundation support
   at [http://wikki.X.Org](http://wikki.X.Org)
for help.

Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xint: unable to connect to Xserver
xint: No such process (errno 3): server error.
johan@ubuntu:~$_
"

Can I reboot into windows via GRUB from this point safely (force a reboot). Without losing my original "Xserver" settings.

---

### Post by macdo on 2006-05-21
On the offchance, press ctrl+alt+F7.
That's where the GUI should be.

---

### Post by johanhartman on 2006-05-21
Sorry i'm abit new what do you mean by offchance?

---

### Post by BobSongs on 2006-05-21
By now you may have already resolved your problem.

My experience with Ubuntu setup CDs is two-fold.

1. Any slight damage to the setup CD and things just go awry. I don't understand why. Perhaps it's the age of my optical drive. The older they get the more finicky. And files can be misread after a while.

2. I've installed Ubuntu a fair number of times. I tinker, I break, so slap me. But in my numerous installations I've noted that some things will work just fine in an install whereas they will not work quite so well on the next install... and then they'll be fine again on the next. 

Point #2 happened much more frequently with my Windows 98 installs than it ever did with Windows XP Pro. So in Ubuntu if something just won't run right I eventually get fed up and re-install. Then the feature works just fine.

Suggestion: The Ubuntu setup is very, very fast compared to, say, XP (considering XP just installs an O/S whereas Ubuntu adds an entire office suite in the process), so a reinstall should do fine. It **may** be possible, on the off chance, that some component doesn't like Ubuntu. But I would doubt it. Verify the underneath of the CD for scratches. If it isn't pristine, dump it and burn a new one in Windows.

---

### Post by richbarna on 2006-05-21
He means click the keys :- Ctrl , Alt and F7 together

---

### Post by Galactus on 2006-05-21
[QUOTE=macdo]On the offchance, press ctrl+alt+F7.
That's where the GUI should be.[/QUOTE]

I tried that (I am having the exact same problem) and it just locks everything up...the cursor disappears and the system stops. I have to do a hard reboot to start the machine again.

---

### Post by macdo on 2006-05-21
On the offchance = just in case

I'm guessing English is not your first language?

---

### Post by johanhartman on 2006-05-21
[QUOTE=richbarna]He means click the keys :- Ctrl , Alt and F7 together[/QUOTE]

Thanks I tried but ctrl + alt + F7 just brings me back to idle blank screen I am very prompted to restart... should I?

---

### Post by mlind on 2006-05-21
Ubuntu is probalby working fine and graphical user interface (GUI) is displayed 
on tty7, but there's a problem with gfx card's driver, like others have noted.

using terminal session, for example tty1 (Ctrl+Alt+F1),
you should backup your current /etc/X11/xorg.conf file and reconfigure X server.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
sudo dpkg-reconfigure xserver-xorg
(use default values for all questions you don't know for sure)
sudo /etc/init.d/gdm restart

```

don't start X-server manually, it's display managers job.
If you need to do so, you should start it on secondary screen
```

sudo startx -- :1

```

it's on tty8 now, Ctrl+Alt+F8

---

### Post by Mustard on 2006-05-21
When you do the above reconfiguration of xserver-xorg you should try the 'vesa' drivers too.

---

