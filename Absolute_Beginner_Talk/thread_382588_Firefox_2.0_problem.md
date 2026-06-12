---
title: "Firefox 2.0 problem"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by jmtjet on 2007-03-12
I'm having a problem with one page. Firefox will alway crash on: [www.virtualdr.com](www.virtualdr.com)  no matter what I'm doing. I can't be on the page longer that 2-3 minutes before a crash occurs. I file a crash report after each crash.  All other pages seem ok- no crashes.  Could someone suggest a fix for this? Mozilla doesn't seem to be interested. I've tried Adblock Plus, didn't seem to make a difference. I think it's got something to do with the page re-sizing all the time. 

Note: I've tried dumping all history and cookies-didn't make a difference.

---

### Post by bollix47 on 2007-03-12
That site works fine for my system but it does use a lot of flash so if you want you could try installing the latest flash version using [_this guide_]("http://www.psychocats.net/ubuntu/flash").

---

### Post by Penguin Power on 2007-03-12
jmtjet, i've had exactly the same problem with many pages with Flash. I assume this is some sort of compatability bug with Flash 9.0 and Firefox 2.0, and it'll be fixed sooner or later. 

I'd recommend using NoScript to prevent Flash scripts from being executed in the first place, you can allow them if you need to use it.

---

### Post by jmtjet on 2007-03-12
I installed NoScrips and have had no crashes on VirtualDR website since. Time will tell if that does it. Thanks. :)

---

### Post by byka on 2007-03-12
Hi.
I'm new to ubuntu myself, and I was suffering from firefox crashing frequently, then I found this tip in the edgy guide and it seems to have done the trick for me. Maybe worth a try for you as well.


Note: if firefox crashes when visiting a website with flash content, do the following:

sudo gedit /usr/bin/firefox

and add the following line as last but one line of the file:

export XLIB_SKIP_ARGB_VISUALS=1

Now firefox shouldn't crash anymore. (Launchpad bug report: [1])

    * Restart Mozilla Firefox 

hth

---

