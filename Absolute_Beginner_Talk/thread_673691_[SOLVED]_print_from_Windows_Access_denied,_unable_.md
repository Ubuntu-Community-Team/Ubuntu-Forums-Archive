---
title: "[SOLVED] print from Windows Access denied, unable to connect"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by christopher.newell on 2008-01-20
I've been trying unsuccessfully to print from my wife's Win XP laptop.  I've searched the Internet on how to setup CUPS etc, and from what I've found, I should be there.  Whatever print job I send gives me the first 1/2 inch (after the top margin), then stops.  When I look at the printer from the laptop, the printer status window has [PRINTER]" on "[PC NAME]" Access denied, unable to connect".  I've got a connection, otherwise I wouldn't get the 1/2 inch, but I'm at a loss for the remaining data.  Any ideas?

---

### Post by torgrot on 2008-01-20
Try creating an account on the Ubuntu PC with the exact same user name and password as is on the WinXP laptop.  I have had only marginal success printing from windows to a printer connected to ubuntu.  Each time it has worked, I was using an account with the same username and password.  I wish you luck.

torgrot

---

### Post by christopher.newell on 2008-01-22
Thanks Togrot.  When you've tried without the username on Ubuntu, do you get anything printing?  I think my problem might be in my overall network setup.  Oddly, I'm able to access files on my Ubuntu PC from the Windows laptop, and I can see the laptop connected to the network from Ubuntu, but I can't actually access any files on the laptop.  Maybe there's a connection (pardon the pun).

---

### Post by mikeyphi on 2008-01-22
Only one thought!!
 Have you setup System/Administration/ Printing  in Ubuntu for sharing?

---

### Post by christopher.newell on 2008-01-22
Well, I did have sharing enabled, but when I looked to verify it, somehow the "enabled" checkbox wasn't selected!  As soon as I checked it, out popped the Win XP printer test page.  Looks like the problem's solved.  After all the details I checked and rechecked, to be such a simple thing...

---

