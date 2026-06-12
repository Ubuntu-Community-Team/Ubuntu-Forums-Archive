---
title: "Firefox crashes and won't restart"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by quercusrobur2002 on 2007-04-22
A problem I have with Firefox is that it frequently crashes for no apparent reason. When I try to restart Firefox, it shows in the task bar as loading, then disappears again. The only way I can get Firefox to reload is by rebooting the laptop from scratch, which is time consuming and irritating, and not really what I expect from a system renowned for it's stability?? Any ideas??

---

### Post by Bachstelze on 2007-04-22
What happens when you run Firefox from the terminal ?

---

### Post by quercusrobur2002 on 2007-04-22
Do you mean after it's crashed? I'll let you know next time it happens...

---

### Post by quercusrobur2002 on 2007-04-22
Right, its just happned again, I tried to start Firefox using the Terminal and got this message;

graham@graham-laptop:~$ firefox
Segmentation fault
graham@graham-laptop:~$

After that i had to once more restart Ubuntu in order to get Firefox to work again...

---

### Post by quercusrobur2002 on 2007-04-28
Still happening... any advise?? Whats a segmentation fault???

---

### Post by Najand on 2007-04-28
Try to kill it using:
```

$ kill-all firefox-bin

```
and try to start it again... If it didn't help try to reboot your computer.

---

### Post by Najand on 2007-04-28
According to WIKIPEDIA:
Segmentation Fault is a particular error condition that can occur during the operation of computer software. A segmentation fault occurs when a program attempts to access a memory location that it is not allowed to access, or attempts to access a memory location in a way that is not allowed (for example, attempting to write to a read-only location, or to overwrite part of the operating system)

---

### Post by DezSP on 2007-04-28
Perhaps we should be worrying about what crashes Firefox in the first place. It sounds like a memory leak to me, something FF is world-famous for nowadays, but it could be something else. Try running Firefox from the terminal to begin with, so we can see what error it crashes with. I'm assuming it tends to crash after a fair period of usage, if the memory leak hypothesis is true, this can probably be accelerated by just opening loads of different pages and using tabbed browsing a lot.

Oh, and if you could list the extensions/plugins/themes you're running, that would be useful.

---

### Post by tobler on 2008-04-16
I am using Hardy beta and Firefox-3 beta. And it crashes a lot.
Mostly I don't need to reboot whole computer, just log-off and login back.

If you are interested, you can run:
```
strace firefox 2>&1 | tee firefox-hangs.log
```
That will generate lot's of debug data and it can be used to solve what is causing problem.

On my case... propably problem is in opensc ("file does not exist") on my case. I use opensc card reader with Firefox but after crash it won't start without logoff/reboot.

---

