---
title: "killing xscreensaver"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-07-03
Hi all,
       I noticed in Applications/System Tools/System Monitor that there are 31 processes running at present on my Breezy partition
I was wondering if I can get rid of some of these memory hungry programs, such as xscreensaver. 
The far right column in System Monitor called argument states that xscreensaver's argument is xscreensaver-nosplash. What does this mean?
Thanks for your comments in advance

:D 
_________________
BOOM SHANKA
May the seeds of your loins be fruitful in the belly of your woman
- Neil

---

### Post by woedend on 2006-07-03
xscreensaver has this nasty little splash screen when started..
a splash screen I assume you know what that is, when a program loads and you get a little window(for looks) like openoffice and gimp use.  
so the -nosplash option means don't show the splash screen(this is a good thing :p).
are you wanting to uninstall xscreensaver?  You need it running if you want screensavers to work.

---

### Post by carverj on 2006-07-03
That's right, I use xscreensaver as a good example because I don't use a screensaver, and this is one of the many processes I feel is clogging up memory
So I am wondering if all these processes are stored in the same location and am wondering if someone can tell me which other processes I can do without and how to disable permanantly(such as a script I can modify)
I hope this makes sense, Thanks.

---

### Post by woedend on 2006-07-03
search the forum for
sysv-rc-conf
its a package you install that you can enable/disable services with.
there were 21 services I did away with, you may have less.  What each thing does is outlined in the forums.  Just be careful with it!
As far as other things (like cups if you have no printer or xscreensaver), I just remove them from synaptic.

---

