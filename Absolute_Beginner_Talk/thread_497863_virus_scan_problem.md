---
title: "virus scan problem"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by dwcrabtree on 2007-07-10
I'm a "absolute beginner". Having trouble with ClamTK Virus scanner.
When I bring it up I get the following window messsage:

"Unable to view ClamAV's information file.
This will affect
how ClamTk views the number of viruses and version information."

After closing THAT error message I get another one when I try and do a file scan as follows"


"You do not appear to have virus definitions!

Running "freshclam -v" as root may fix the problem."

Thanks in advance.

---

### Post by wormser on 2007-07-10
> **dwcrabtree said:**
> Running "freshclam -v" as root may fix the problem."

Have you tried that command?  Applications> Accessories> Terminal

```
sudo freshclam -v
```

Then enter in your password and try the scan again.  Sudo gives you root permissions.  Let us know how it goes.

---

### Post by dwcrabtree on 2007-07-10
Yeah I tried it. Below is the response from terminal:


"dave@dave-desktop:~$ 
dave@dave-desktop:~$ sudo freshclam -v
Password:
Current working dir is /var/lib/clamav/
Max retries == 5
ClamAV update process started at Tue Jul 10 20:06:45 2007
Querying current.cvd.clamav.net
TTL: 492
Software version from DNS: 0.90.3
WARNING: Your ClamAV installation is OUTDATED!"
WARNING: Local version: 0.90.2 Recommended version: 0.90.3
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 43
main.cvd is up to date (version: 43, sigs: 104500, f-level: 14, builder: sven)
daily.cvd version from DNS: 3633
daily.inc is up to date (version: 3633, sigs: 30874, f-level: 16, builder: ccordes)
dave@dave-desktop:~$ "

Thanks for your help here. We'll get it...

---

### Post by provolski on 2007-07-12
encountered same issue but typing sudo freshclam -v on the terminal did not help.i even log as the root. this is what came up.

root@christian-desktop:~# sudo freshclam -v
WARNING: Can't get information about user clamav.

pls help i am also new to this... thanks

---

### Post by kitterma on 2007-07-12
The clamtk shipped with Feisty is incompatible with the clamav shipped with Feisty.  A new one has been released and is in Gutsy.  I've asked for a backport, but in the meantime, even if you got clamtk running/updating (it can be done) it wouldn't be able to find a virus.  If you really want a clamav gui, use Klamav.

---

