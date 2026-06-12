---
title: "Checkgmail for multiple users"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Strangerdave on 2008-02-24
I have a account on this computer and use checkgmail quite a bit.  My wife who also has a account on this computer would like to use checkgmail also, but I can't seem to get it to work at startup.

I have created a session at start up called Gmail and as a command put:

usr/bin/checkgmail

but it won't start up.  This is what I have for my profile, but is there something I am missing? Should it be 

sudo usr/bin/checkgmail instead?

Any help would be appreciated.

-SD-

---

### Post by northern lights on 2008-02-25
That does not seem like a command that needs root rights.

Other than that I am not familiar with "checkgmail".

Alternatively, why don't youuse some email client (evolution, thunderbird), configure it for both accounts, autostart it and configure it to notify you when new messages arrive? If you use IMAP, it leaves the messages on the server also...

---

