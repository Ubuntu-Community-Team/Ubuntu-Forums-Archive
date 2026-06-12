---
title: "kgamma in Ubuntu 6.06"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by George_S on 2006-08-27
Can kgamma run in Ubuntu 6.06. If not, is there any other software for monitor calibration that would run in Ubuntu?

George

---

### Post by Kobalt on 2006-08-27
Hi,
Have you tryed searching it with Synaptic ? If it's in the repos then it works under Ubuntu 6.06. And if you don't find it, you can still search for a monitor calibration software in synaptic. 

Cheerios :

---

### Post by George_S on 2006-08-27
Yes, in fact I installed it already. It was deposited into usr/share/applications/kde folder. However, when I double-click on it, the application launches, but there is just an empty windows with a Cancel button in the lower right corner.

Perhaps kgamma really works, but maybe I am accessing it the wrong way ....

---

### Post by zami on 2007-02-15
This is an old thread, but I'm having the EXACT same problem as the original poster, and thought just adding to this thread might save someone else a little headache later - that is if an answer crops up!

I launch KGamma with
```
kcmshell kgamma
```
But I get the errors
```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```
and though the program still launches, it's just a blank box with nothing but the cancel button.

I am using the gnome desktop, but I installed KGamma via Synaptic so I'm assuming all the dependencies are accounted for.  And I haven't had troubles running "K" programs in the Gnome land before.

Any assistance or suggestions would be much appreciated!  Or mabye  a pointer to another program.  (I'm also trying to get the monitor calibration tool Monica to run ... but that's a problem for another post.)

-zami

---

### Post by George_S on 2007-02-17
Zami,

I never got KGamma to work reliably, so I switched to gFTP, which works fine. 

Hope this helps.

---

