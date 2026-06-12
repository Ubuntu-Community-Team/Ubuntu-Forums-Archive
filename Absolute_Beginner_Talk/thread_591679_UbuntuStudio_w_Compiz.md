---
title: "UbuntuStudio w/ Compiz?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by siege911 on 2007-10-25
I just recently installed UbuntuStudio as I was looking for something for my graphic/video/audio editing needs and I would rather not go spend several grand on a new computer and software.

Anyways, I got it installed and everything with only a few minor glitches so far.

The main thing I noticed was that the whole Compiz stuff was disabled or not installed or I couldn't access it for some reason. If it's not included in this, how can I install it? If it is included, why is it telling me: "Failed to execute child process "compiz" (No such file or directory)"

---

### Post by por100pre1 on 2007-10-25
Let's install it:

```
sudo aptitude install compiz compizconfig-settings-manager
```

Tell me if this works. :-k
[B]
Are you using Gutsy or Feisty?[/B]

---

### Post by siege911 on 2007-10-25
> **por100pre1 said:**
> Let's install it:

```
sudo aptitude install compiz compizconfig-settings-manager
```

Tell me if this works. :-k
[B]
Are you using Gutsy or Feisty?[/B]
Now I just get a simple "Desktop Effects Could not be enabled"

And I'm using Gutsy.

---

### Post by nynoah on 2007-10-25
To be honest with you...........if you are just getting it all running now........I would start over and load ubuntu (regular) 7.10 get that on your system and then add ubuntu studio from Synaptic.  You will get all that ubuntustudio has, plus all the things like compizfusion will be up and running correctly.  I think this will save you the most time.

Noah

---

### Post by Drunky on 2007-10-26
> **nynoah said:**
> To be honest with you...........if you are just getting it all running now........I would start over and load ubuntu (regular) 7.10 get that on your system and then add ubuntu studio from Synaptic.  You will get all that ubuntustudio has, plus all the things like compizfusion will be up and running correctly.  I think this will save you the most time.

Noah

That is what I did.  Not quite the exact order but it worked.

Installed Ubuntu 7.10 Gusty and updated.

Enabled restricted drivers for my ATI card.

Now I updated to Ubuntu Studio via this [Ubuntu Help Wiki]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy?highlight=%28studio%29").
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```
Ubuntu Studio is up and running at this point.

Then copied my xorg.conf file:
```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.backup
```

And edited it:
```
sudo gedit /etc/X11/xorg.conf
```

At the end of it look for Composite and put 1 instead of 0:

```
EndSection
Section "Extensions"
Option "Composite" "1"
EndSection
```

* SKIPPED STEP - see notes below

Then I loaded the compiz-setttings-manager:
```
sudo apt-get install compizconfig-settings-manager
```

Then goto *Preferences* -> * Appereance* and then click on the *Effects* tab.  Then choose one of the enabled settings for the effects.

Then goto *Preferences* -> *Compiz Manager* and turn on the cube, cube rotate...whatnot.

Also note that I only had two face to my "cube".  Move your cursor to the bottom right of the screen where the various desktops are shown and right click.  Choose preferences and change the number from '2' to the number of your choosing.  I tried six but the "cube" was huge and just silly...I ended up back at four.



* SKIPPED STEP caveat - I also did this step but Gnome acted funny afterwards and I ended up with some KDE icons apparently.  After another reboot I got a warning message that I didn't need to do what I did and that Gnome was reverting back to its settings on reboot.  Therefore I'm not recommending this step.
```
sudo apt-get install xserver-xgl
```

Hope this helps.

---

### Post by siege911 on 2007-10-29
Thanks. This is exactly what I wanted.

One last quick question. Do I need to install the ubuntustudio-desktop? Is it just gnome with a special theme or something else? Because if it's only a special theme, then I'd rather just customize the base setup.

---

