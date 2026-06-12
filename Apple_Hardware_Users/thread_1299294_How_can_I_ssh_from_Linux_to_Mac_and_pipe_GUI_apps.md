---
title: "How can I ssh from Linux to Mac and pipe GUI apps?"
date: 2009-10-23
forum: Apple Hardware Users
---

### Post by Pogeymanz on 2009-10-23
The point here is that the Macs I work on have Matlab installed. I want to log in from my Linux box at home and run Matlab.

Help me Mac people!

---

### Post by Cybie257 on 2009-10-23
The only way(s) that will ever happen would be to remote into your MAC via VNC, or some other remote server software, and run it ON your MAC. The only other option would be if the app is network run-able. You can't run apps on one computer from another as there permission issues and also installed file throughout the system that are required to run them.

If you are referring to remote desktop-ing, then, yes, you can set up SSH and VNC to do so and I will find the links to help you there if you want, but to directly run from your Mac to your Linux, doubt you will find a way to make it happen, (UNLESS) this program is cross-platform compatible AND it only requires a single executable file to run.

-Cybie

---

### Post by Pogeymanz on 2009-10-24
Well, I didn't mean run it ON my machine. Rather, I meant pipe the GUI over ssh so that I could see and interact with Matlab, which would be running on the Mac at work.

I use ssh -Y username@machine to log into a Linux machine and run GUI programs on it from my machine and if I use the same command for the Mac, I can run X11 apps like xterm just fine.

---

### Post by buntuLo on 2009-10-24
uuhm? is it ssh on mac any different?
i ssh -X from ubuntu boxes to fedora workstations, and run matlab over there.
i get the matlab gui simply calling matlab at the remote prompt, while i launch background matlab jobs on those workstations with
```
nohup \matlab -nojvm -nodisplay < ~/batchjob.m > & ~/batchjob.log &
```

---

### Post by Pogeymanz on 2009-10-24
> **buntuLo said:**
> uuhm? is it ssh on mac any different?
i ssh -X from ubuntu boxes to fedora workstations, and run matlab over there.
i get the matlab gui simply calling matlab at the remote prompt, while i launch background matlab jobs on those workstations with
```
nohup \matlab -nojvm -nodisplay < ~/batchjob.m > & ~/batchjob.log &
```

Sure, but that doesn't work on the Mac I log into. That's my problem. I think it's because the Mac GUI is not X11, so ssh -X pipes X11, but matlab gui probably isn't using X11.

---

### Post by Eadz on 2009-10-24
If matlab on osx isn't a X11 application, you can't use ssh's X forwarding. Use VNC or similar.

---

### Post by crocowhile on 2009-10-24
Does your matlab use dynamic licenses (via a server?). If it does you can install matlab on ubuntu and use the dynamic license via VPN.

---

