---
title: "HELP - SoftMAC: invalid iw_mode !"
date: 2008-03-29
forum: Apple PPC Users
---

### Post by bifter on 2008-03-29
I changed the Screens & Graphics setting on my PowerBook G4 Ubuntu 7.10 to try to hook it up to a second display. When I made the change it said I had to log out for the change to take effect.

When it restarted it now displays the message - the numbers keep changing...

[  742.567567] SoftMAC: invalid iw_mode !
[  756.567567] SoftMAC: invalid iw_mode !
[  789.567567] SoftMAC: invalid iw_mode !
[  742.567567] SoftMAC: invalid iw_mode !
[  742.567567] SoftMAC: invalid iw_mode !
etc etc 

it just keeps adding lines with the number ever increasing.

is there a way that i can bypass this so i can get back in there and disable the setting i changed?

thanks for any advice.

---

### Post by stream303 on 2008-03-29
Although I can't help outright here, the first thing I do before fine-tuning a ppc install is to backup these files:

```
sudo cp /etc/X11/xorg.conf   /etc/X11/xorg.conf.original

sudo cp /etc/yaboot.conf  /etc/yaboot.conf.original
```

That way I can at least get back to square one if everything goes haywire by getting back in from a terminal, or rescue mode with

```
sudo cp /etc/X11/xorg.conf.original  /etc/X11/xorg.conf
```

etc.

I'll try digging up some info on those error messages and see if anything jumps out...

---

### Post by bifter on 2008-03-30
Thanks, that sounds a great tip for once I get things back to normal again.

One thing I forgot to say was that the errors appear after the Ubuntu loading status bar has completed. Seems to be just before I get to the login screen :(

i get

[INDENT]kinit : no resume image during normal boot . . .

pheonix login:[/INDENT]

then the screen is filled with the ever increasing 

[INDENT][ 742.567567] SoftMAC: invalid iw_mode !
[ 756.567567] SoftMAC: invalid iw_mode !
[ 789.567567] SoftMAC: invalid iw_mode !
[ 742.567567] SoftMAC: invalid iw_mode !
[ 742.567567] SoftMAC: invalid iw_mode ![/INDENT]

there seems no way to pause, interrupt or skip this - other than a hard reset.

---

### Post by bifter on 2008-03-30
It's ok, a fresh install seemed to do the trick ;) There was nothing of importance on the machine and it was probably way overdue anyhow. 

I found some info on setting up the DVI OUT on this page so hopefully I'll not screw it up next time - [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

