---
title: "Printing to network printer connected to Mac"
date: 2011-08-08
forum: Apple Hardware Users
---

### Post by noahbanks on 2011-08-08
Hey everyone. I'm relatively new to Linux, but fairly experienced with OS X.

I've run into issue on my Linux machine (running 10.04) when I want to print. When I go to System>Administration> Printing, I cannot find the printer connected to the network through my dad's computer, running OS X 10.7.

I'm not sure what I should do and couldn't seem to find any help elsewhere.

I would appreciate any help.

---

### Post by linuxopjemac on 2011-08-08
open up
```
http://localhost:631
```
on your linux computer in a browser. Try to add the printer. If it's connected to a Mac, it should I think be visible with CUPS.

---

### Post by noahbanks on 2011-08-09
> **linuxopjemac said:**
> open up
```
http://localhost:631
```
on your linux computer in a browser. Try to add the printer. If it's connected to a Mac, it should I think be visible with CUPS.
I open up CUPS, click on printers, and no printers are present. Do I need a hardwire connection? Do I need to configure anything on the Apple computer side?

---

### Post by fdrake on 2011-08-09
2 thinks to notice. 
1.did you share your printer with the mac os to the rest of the network?
2. is your mac powered on? it needs to be on all the time if the printer is connected to the network through the mac

---

### Post by 1clue on 2011-08-09
Sometimes network shares take a few minutes to advertise.  Open your port and then refresh after a few minutes, see if anything came up.

Try putting in [http://mac.ip.address:631](http://mac.ip.address:631) on a lark.  It might not be public for other than localhost but it's worth a try.

Also try going to your mac control panel for the firewall and allow printer sharing, or just turn off the firewall for a few minutes to see what's going on.  Once you know what port you can open that port up on your mac and things should work.

---

