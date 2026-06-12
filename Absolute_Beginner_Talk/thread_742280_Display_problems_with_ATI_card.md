---
title: "Display problems with ATI card"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Nagisaki on 2008-04-01
Okay, I'm a Linux newcomer.  Got some terrible virus or something on my box, to the point where it didn't even boot all the way.  So, i used an Ubuntu CD to get access to my files, and wiped the thing clean.  Very easy to do.  Decided not to reinstall winblows, so i stuck with Ubuntu, i think it's 7.10, "Gutsy"

I have an ATI Radeon 9250, and according to my screens and graphics preferences, I'm using the fglrx driver.  but my display is not using the whole screen.  theres at least a half-inch border of black around the top and sides.  resolution is 1280 x 768, when i try to change it, i tell it to keep the new settings, but nothing happens.  when i reopen the control panel, it's back to 1280 x 768.  My monitor is a Nokia 447w CRT.

I'm completely unfamiliar with console, so any fixes that require it, please spell it out step by step.  I would prefer a GUI solution, but i can accept that thats not always possible.  Thanks in advance for the help.

---

### Post by scragar on 2008-04-01
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

envy is a good and easy way to install your drivers(just run the .deb installer, then open it from
Applications > System Tools > envy
and choose install ATI graphics card

when it's done log out, press ctrl+alt+backspace to quickly restart graphics, then log back in.

---

### Post by Oldsoldier2003 on 2008-04-01
> **scragar said:**
> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

envy is a good and easy way to install your drivers(just run the .deb installer, then open it from
Applications > System Tools > envy
and choose install ATI graphics card

when it's done log out, press ctrl+alt+backspace to quickly restart graphics, then log back in.

Just an important reminder. If you use envy on Gutsy or below you MUST remove the drivers  before upgrading to hardy or you will mess things up. The new version of envy will not require you to uninstall drivers before upgrades, however its not available for versions lower then Hardy last time I checked.

---

### Post by scragar on 2008-04-01
nope, you need EnvyNG to avoid uninstalling to upgrade, best on gutsy is still the legacy.

site does say that in some rather large red text that explains this:
> [color=red]**[SIZE="4"]WARNING: you will have to remove the driver you installed with Envy before upgrading Debian or Ubuntu to a newer release (e.g. upgrading Ubuntu Edgy to Ubuntu Feisty or Debian Etch to Debian Lenny).[/SIZE]** [/color]

You will have to type the following command:

sudo envy --uninstall-all 
[NOTE: This is no longer necessary with EnvyNG]

---

### Post by forrestcupp on 2008-04-01
You don't need the command line, or to change the resolution or anything.  You just need to adjust the screen size on your monitor.  Does your monitor have buttons on it for the settings?  You should be able to stretch the horizontal and vertical size to fit your screen by actually using those buttons on your monitor.  Especially if it is a CRT.


And about the Envy thing.  I wouldn't suggest this, but I had Envy installed drivers in my Gutsy, and I just upgraded to Hardy leaving those drivers on just to see what would happen.  It worked.  I didn't have any trouble with it.  That seems to go against what is supposed to happen.

---

### Post by Nagisaki on 2008-04-01
Envy was not able to upgrade me to the drivers i needed.  The most current ATI drivers do not support Ubuntu... only Suse and Red hat.  At least, thats what the programmers e-mail told me.

And as for resizing my monitor? Thats not the problem.  I was able to size it properly before, but now, as i said, even when i change the resolution, it doesn't change.

---

### Post by forrestcupp on 2008-04-01
> **Nagisaki said:**
> 
And as for resizing my monitor? Thats not the problem.  I was able to size it properly before, but now, as i said, even when i change the resolution, it doesn't change.

Did you try it?  For a while, I was having a problem that every time I switched between Ubuntu and Vista, I had to mess with my monitor settings because they both used the monitor differently.  Changing the resolution wouldn't necessarily change that.

But if you actually tried using the buttons on the monitor and it didn't work, try changing your refresh rates.

---

### Post by Nagisaki on 2008-04-11
It apparently has "fixed" itself, it's now sized properly (though it seems too small to me)

and i can adjust the screen size by pushing the buttons...  that was never a problem.

---

