---
title: "[SOLVED] Firefox extension install failure"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by bren on 2007-08-09
I have Firefox 2.0.0.4 running on 32bit feisty

Tried to install an extension from the Firefox extension website page.


I got an error message saying extension install failed 

See attached screenshot

Any ideas?

Thanks

Bren

---

### Post by Pragmatist on 2007-08-10
Try it again, and when it says to "Review the error log for more details", go to **Tools-->Error Console**  and then post the content here.

---

### Post by bren on 2007-08-11
thanks pragmatist

here is the next screenshot (from error console)

one thing to note is that the only extension that i have installed is foxcloud but it is not installed properly.....it says it needs firefox restart.    I also cannot remove this extension.....if i try then it says it will be removeed at firefox restart but this does not happen

bren

EDIT : also have google extension installed

---

### Post by Pragmatist on 2007-08-11
which extension were you trying to install?

---

### Post by bren on 2007-08-11
adblock plus

bren

---

### Post by bren on 2007-08-11
but it doesn't matter

i get the same error for all extensions

bren

---

### Post by Pragmatist on 2007-08-11
I have some ideas for further troubleshooting, but if it were me, I would back-up my bookmarks and do a compete uninstall (to ensure ALL firefox files are removed) and then install fresh.

---

### Post by bren on 2007-08-11
hi pragmatist

thanks for that - i agree!
i have looked to try and find the location for bookmarks etc but failed....
any ideas....

also before i start i thought i remembered reading that firefox is strongly bound into the ubuntu install and shouldnt be removed....

but maybe i am wrong...

bren

---

### Post by bren on 2007-08-11
actually its ok i found this for the first question

locate firefox | grep bookmarks

---

### Post by Pragmatist on 2007-08-11
> **bren said:**
> 
....i have looked to try and find the location for bookmarks etc but failed....
any ideas....
It is in the .mozilla directory.  The path is something like this:
> /home/me/.mozilla/firefox/ugm614au.default/bookmarks.html
If you want to see exactly where, type this (replace "me" with your home directory):
```
find -P /home/me/.mozilla -name bookmarks.html
```

> **bren said:**
> ....i thought i remembered reading that firefox is strongly bound into the ubuntu install and shouldnt be removed....
I don't think so.  Whichever package manager you use will show you what you are removing.  Firefox is just one browser that comes with Ubuntu.  Ubuntu also comes with "Epiphany" browser , and there are many more browsers you can also install if you want.  Besides, your only removing it and then installing it again (Note: I didn't say "reinstall" since I want you to do a "complete uninstall" so that all firefox configuration files are removed.  You want to do this in case the problem is due to some configuration file.  If you just reinstall, you could reinstall the executable but keep all of your old config files--which won't help you if the problem IS the config file! :) )!

---

### Post by bren on 2007-08-11
it must have been a prob in the config somewhere.....

i moved .mozilla to .mozilla_backup and then copied back the bookmarks

all working now

thanks for your help

bren

---

