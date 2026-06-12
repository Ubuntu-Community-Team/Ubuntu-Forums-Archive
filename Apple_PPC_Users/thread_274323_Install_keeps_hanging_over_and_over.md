---
title: "Install keeps hanging over and over"
date: 2006-10-09
forum: Apple PPC Users
---

### Post by iric on 2006-10-09
Tried to install Ubuntu and Xubuntu on my Mac G3 350 B&W with 1GB memory and a 80gb harddisk (which had a linux install before, but on a x86 pc).

Tried the regular Ubuntu, the regular Xubuntu and both alternative cds and yes I downloaded the PowerPC versions ;) 

Burned the cd's at 8x speed on different brands, no luck at all. Boot is ok, but then the "famous" white screen appears and it gets stuck. 

On all cds the options boot video=ofonly or expert video=ofonly or even install powerpc or just install or expert won't work. Pressing CTRL + OPTION + F1 doesn't help either, nothing comes up after the white screen.

I'm kind of out of options now.

So the cd does boot, but after loading kernel and loading ram disk it hangs with a white screen and nothing seems to do anything. (Also tried ctrl+alt+f1 until f12 and ctrl+option+f1 until f12 and ctrl+alt+option+f1 until f12: nothing did anything).

Could somebody please help me out on this?

---

### Post by seatea on 2006-10-09
I don't have the solution that you need, but I wonder if there is a problem with your xorg.conf similar to what many in the imac threads have been encountering on installation. Here is the thread,[HTML]http://ubuntuforums.org/showthread.php?t=273711[/HTML].It will link you to others as well. One thing to keep in mind is that the monitor settings they are recommending are for the imac crt monitors. You will need to have the  specifications for your  monitor to use in  your  xorg.conf.

---

### Post by iric on 2006-10-10
> **seatea said:**
> I don't have the solution that you need, but I wonder if there is a problem with your xorg.conf similar to what many in the imac threads have been encountering on installation. Here is the thread,[HTML]http://ubuntuforums.org/showthread.php?t=273711[/HTML].It will link you to others as well. One thing to keep in mind is that the monitor settings they are recommending are for the imac crt monitors. You will need to have the  specifications for your  monitor to use in  your  xorg.conf.

But how to edit xorg.conf if ctrl + option + f1 doesn't bring up the terminal?

---

