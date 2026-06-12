---
title: "Hit the ground walking"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by 5centcigar on 2006-08-15
Thanks to Ubuntu I have finally gotten my feet on the ground and am actually doing things in Linux. It did not take me long to break something, and it is my intention to clean up my messes as I go along.
When I launch 'Opera' from the command line I get this:
-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

....Opera lanches, but the terminal hangs there.I suspect this is connected to an attempt to install the Flash plugin.
Any suggestions for tidying up here?
thanks

---

### Post by jrjr on 2006-08-15
.

---

### Post by Tomosaur on 2006-08-15
The terminal isn't 'hanging', that's just how it works unless you tell Opera to fork from it. As far as I'm aware, those errors are just ordinary Opera debugging messages while it detects your system setup. Once you close Opera, control will be restored to the terminal, but you can quite easily just open another terminal and work in there.

---

### Post by jrjr on 2006-08-15
.

---

### Post by Ramses de Norre on 2006-08-15
```
nohup opera &
```
will give you opera undependent from your terminal,  when you got output you just press enter to get a prompt (the username@hostname:dir$ thingy).

The easier way is using a launcher ;)

---

### Post by kernelpanicked on 2006-08-15
> **jrjr said:**
> fork from it...hmmmm so thats what that means!!

I take it that if you tell opera to 'fork' from the terminal, once opera launches the terminal will close?

How is that done??

Well you can start it with nohup, as suggested, or after starting it hit "Ctl+z" to suspend the process. This will give you back the terminal but not yet fork the process, so if you close the terminal opera goes with it. To completely free the terminal, use "bg" to background the process.

---

### Post by Tomosaur on 2006-08-15
Actually, 'forking' is a completely different thing, I just used it to describe what I meant, which was - you can tell a program to use a new terminal to launch. By default, it will operate in a 'sub-shell', which means it gets control of the terminal window you're using. You could launch a new terminal and pass the program name as a command, and you'd keep your existing terminal while the program ran in the new one.

You can also use the '.' command, which will close the terminal when the program has finished.

Or, you can use ctrl+z or 'bg', as kernelpanicked has pointed out.

---

### Post by 5centcigar on 2006-08-15
Good to know I did not break anything.
Thanks everyone.

---

