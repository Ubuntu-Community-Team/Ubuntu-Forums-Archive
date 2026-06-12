---
title: "mtink gives Xlib errors"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by rev_b on 2006-12-06
I would like to use mtink to monitor my Epson printer ink levels, but I'm not even able to start it. I get

~$ sudo mtink
Password:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Any ideas?

Thanks.

---

### Post by rev_b on 2006-12-07
I really could use a ink monitoring utility... :( 

If mtink isn't an option, could someone tell me how to use ttink (in command line)?

---

### Post by dsowerby on 2007-02-12
Did you ever resolve this?  I have the same problem ...

David

---

### Post by MickS on 2007-02-16
I can't get it to work either.

Mick

---

### Post by dsowerby on 2007-03-03
Mike

This may help, though I'm not entirely sure what I did!

I found a later version (1.0.14) of mtink on [http://packages.debian.org/unstable/misc/mtink](http://packages.debian.org/unstable/misc/mtink)

Installed this with package manager, accepting its warning that the older version already installed may be better supported. After I installed, the package manager said it was the same as the previous version ... but I carried on anyway.

>  gksudo mtink 

now starts up mtink in a gui window

DX4800 isn't listed so I selected "other printer".

This is where I'm not sure exactly what happened

It took so long I thought it had hung up so tried to close it - it didn't respond, so I carried on doing something else for a while.  It must have closed at some point.  I printed a couple of lines just to make sure the printer was still ok - it was.

I then opened mtink again - and it came up with "DX4800" under the title bar and the ink levels showing - so it seems to be working.  I don't know whether it will do the cartridge change yet.  Maybe I was just too impatient the first time I opened it.

Sorry for the lack of precision, but hope this helps.

David

---

### Post by MickS on 2007-03-03
Thanks David, there is another thread on the same subject and I got help there, that bit about having to wait a long time was the all important bit of information, I have also got it working but I have to call from the terminal like you say, it's no good trying from the applications menu.
Any one following this when we say a long time we mean a long time, 5 minutes or so, I have no idea why but it is worth the wait because it only happens the first time.

Mick

---

