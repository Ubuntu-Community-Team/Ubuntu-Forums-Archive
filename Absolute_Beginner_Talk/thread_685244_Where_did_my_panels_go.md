---
title: "Where did my panels go?"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by pmooney78 on 2008-02-02
New Xubuntu user migrating from Windows 2000. I'm running a dual-boot Xubuntu 7.10/Win2K system on a 550MHz Pentium III with 384 MB of RAM. I'm running Xfce 4.4.1.

Last night, I had 80 bazillion programs open and the computer stopped responding. (By "stopped responding," I mean the computer didn't even update the mouse position more than two or three times per minute.) I heard wild disk access for several minutes and finally had to flip the main power switch on the back of the tower. (Yes, I know that's a bad idea.) I'm guessing that I ran out of virtual memory.

When the computer started back up, I logged in fine, and everything works as expected, except that the top and bottom panels on the desktop are gone. Right-clicking on the desktop and choosing settings/panel manager produces no effect at all. (Not even the sound of disk spinning.) Choosing settings/panel produces the same complete lack of result.

Yes, I can deal with not having panels, but I'd rather not have to. I've gotten use to having them. Does anyone have any suggestions?

On a related note, can anyone suggest a better response to a near-total lack of system responsivity? And, how can I configure (or at least examine) my virtual memory settings? (I am family with the DOS/Windows command line, but flounder somewhat under Linux, although I can follow detailed instructions.)

---

### Post by spiderbatdad on 2008-02-02
try alt-f2   xfce4-panel and save your session

---

### Post by pmooney78 on 2008-02-02
Thank you, that solved the problem. I've also added xcfe4-panel to the list of Autostarted applications ... is this overkill?

---

### Post by spiderbatdad on 2008-02-02
nope. sounds good. not sure if you have the option in xfce, but in gnome under preferences>>sessions>>sessions options, there is an option to "remember currently running apps.

---

