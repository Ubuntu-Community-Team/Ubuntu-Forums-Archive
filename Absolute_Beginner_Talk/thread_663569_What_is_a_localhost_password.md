---
title: "What is a localhost password?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by xxmethie on 2008-01-10
When I try and install my printer, it asks for a 'localhost' password?

What is this, I've tried all my passwords but none of them work?

Help please?

---

### Post by dannyboy79 on 2008-01-10
well I don't know how your adding it but if you're using the cupsys web interface you need to do some modifications first. Ubuntu disables the admin password for cupsys as they view it as a security risk. see here: [http://ubuntuforums.org/showthread.php?t=473893](http://ubuntuforums.org/showthread.php?t=473893)

or if you're using the System->Admin->Add printer, it should just be asking for your password, which is the same one that works for sudo. That should be it.

Do you have multiple users on this machine, are you logged in as the main user or the first usert that was created when you set up the computer with ubuntu?

Are you trying to add a network printer or a local printer?

---

### Post by bryklie on 2008-01-20
Hi xxmethie, did you manage to fix this problem?

I'm having the same problem and can't find a fix anywhere.

Your help would be appreciated.

---

### Post by dannyboy79 on 2008-01-21
I see here: [http://ubuntuforums.org/showthread.php?t=542478](http://ubuntuforums.org/showthread.php?t=542478)
that what I already suggested about the cupsys password not being set up in ubuntu. Did you even bother to try this solution? it worked for the other user.

---

### Post by nickrout on 2008-02-28
instead of running System|Admin|Printing open a terminal (or Alt-F2) and run:

gksudo  system-config-printer

put your password into the dialog box and then configure the printer. Worked for me.

---

