---
title: "Firefox crash"
date: 2007-01-10
forum: Apple PPC Users
---

### Post by samden on 2007-01-10
I am running Xubuntu dapper on my iMac G3. Firefox crashes randomly on me (yes, randomly, not when I do anything intensive!). I had this problem on this machine once before with an earlier install of Xubuntu. On that install OpenOffice.org crashed a lot as well. It became much worse when I updated everything through Synaptic. I have not yet updated anything on this install and am hesitant to do so in case things start crashing on me again.

Any suggestions as to how to diagnose this, and what it would be safe / unsafe to update?

EDIT:
And there goes Mousepad crashing on me now! As yet this problem isn't too serious (I managed to post this through Firefox anyway), but I am nervous about installing any updates.

---

### Post by daszz on 2007-01-14
I runned firefox by a shell and this is what the error report says

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 146 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by brackishboy on 2007-01-14
I've been suffering through the same random FF crashes.

I've been mostly ignoring it and being thankful for FF2.0's excellent crash management system :p

---

### Post by mysticmarks on 2007-01-15
This is not just a firefox issue. The random crash is affecting alot of people. It shows up in all forum catagories.

---

### Post by samden on 2007-01-15
When hunting on the forums, heaps of people have similar issues with Firefox but few have definitive answers. I have a list of things to try specifically with Firefox now, so hopefully may find some answer there. However the problem is not isolated to Firefox for me.

In my last installation the problems got a whole lot worse when I installed all available updates, and upgraded to Firefox 2. So I am hesitant to run any updates, but really should (especially the security updates).

How should I proceed with updating? What would be a safe method to use with updating to try and avoid the possibility of further problems developing? What updates might be more questionable and shouldn't be installed?

Please note I have a standard Xubuntu installation from the live cd. Thankyou.

---

### Post by 3rdalbum on 2007-01-16
I used to get that crash on FF 1 on Ubuntu Breezy. It was being caused by gplflash. I simply removed gplflash (it doesn't work, anyway) and that stopped all the crashing.

No idea why (or how) Mousepad could be crashing though.

---

