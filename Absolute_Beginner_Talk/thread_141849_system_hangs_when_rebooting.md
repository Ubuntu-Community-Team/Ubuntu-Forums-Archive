---
title: "system hangs when rebooting"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by mzilhao on 2006-03-09
hi,

just noticed the strangest thing. i cannot reboot my computer. 
it just says 'the system is restarting' and freezes!
i can shutdown fine, though. i don't think i had this problem before, and i can't remember making any major change to the system...
oh, and i'm using dapper...
anyway, can anyone help me?

thanks!
Miguel

---

### Post by mlind on 2006-03-09
does it freeze completely so you can't move your mouse cursor or
switch to other terminals (try Ctrl+Alt+F1) ?

if you can switch to virual terminal, you can view running processes
using *ps -A*

I noticed one of my gDesklets doesn't work well on Dapper, so sometimes
system seems to hang on logout sequence and I have to kill desklet process 
from other terminal.

If you do encounter total freeze, then you should view files on /var/log.
I dunno if Dapper contains Watchdog modules builtin which allow
you to verbosely troubleshoot kernel problems or other instability.

---

### Post by varunus on 2006-03-09
Try logging out and then restarting from the login screen.  Does that work?  If so, there's a bug with your session or in dapper..

---

### Post by mzilhao on 2006-03-09
when i log out and try to reboot from the login screen it's the same...
it freezes when it says "System is restarting, please wait" (and the ubuntu logo on top...)
i can switch to other terminals, but i can't login. nothing happens when i press the keys, actually... 
when i switch back (Ctr+Alt+F7), the GUI is gone, it shows the terminal saying "sending all processes the term signal" (or something...)

---

### Post by mlind on 2006-03-09
try to disable splash to get more verbose message about hanging.

you can do this by editing /boot/grub/menu.lst and adding
nosplash option. find section that looks like this

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=nosplash

```

---

### Post by mzilhao on 2006-03-09
thanks for your help.
i did that, here's what it says:
```
System is restarting, please wait...

* Switching to runlevel:6
* Sending all process the TERM signal

root@ubuntu:~#
```

and then it stays there, on the root terminal, waiting for me to do something...

---

### Post by mlind on 2006-03-10
well, it shouldn't hang there.

does command
```
sudo shutdown -r now
```
work?

---

### Post by mzilhao on 2006-03-10
no, it doesn't... the exact same thing happens...

---

### Post by mzilhao on 2006-03-10
just tried the live cd, and i was able to reboot... 
why doesn't it work with the installed version? i can't remember doing any tweaking to the system, but can i restore the 'default' configuration?

---

### Post by mlind on 2006-03-11
Is your */etc/rc6.d/* directory filled with symbolic links (not empty)?

I don't know how to restore to 'default configuration. Try to re-install initscripts
package and/or other packages that have something to do with booting sequence.

Maybe someone else can help you better.

---

### Post by chuckyp on 2006-03-11
Is it possible you updated.  You may want to check on irc freenode server in #ubuntu+1.  Keep in mind dapper is in no way a stable system yet.  Its possible you upgraded to a bad package.

---

### Post by mzilhao on 2006-03-11
my /etc/rc6.d/ has the symbolic links... i re-installed the initscripts, but it still hangs...

---

