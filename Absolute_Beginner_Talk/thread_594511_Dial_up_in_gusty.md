---
title: "Dial up in gusty"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by HybridTheory on 2007-10-28
Ok i upgraded to Gusty today and now my dial up isnt working right i use gnome-ppp i set it up and it dials in and stops on the dialing window... the only thing that works online is firefox nothing else does can any one help me? (Also i have fooled around in the network settings and the modem thing i click enable but it goes back to a box with like this [-] no matter what..) please help =(

---

### Post by anubhavrocks on 2007-10-28
Since Firefox can reach the net the dial up works fine.You can try 
```
ping ubuntu.com -c3
```
to confirm that.

---

### Post by mdebusk on 2007-10-28
> **HybridTheory said:**
> i use gnome-ppp i set it up and it dials in and stops on the dialing window...

Same thing happens to mine here. Its a known bug. I just move it to a different workspace.

> the only thing that works online is firefox nothing else does

If Firefox works, everything works. What do you think isn't working?

---

### Post by HybridTheory on 2007-10-28
> **mdebusk said:**
> Same thing happens to mine here. Its a known bug. I just move it to a different workspace.



If Firefox works, everything works. What do you think isn't working?

I was talking about like updating and installing things from the Add/remove window but i see what was wrong i fixed it thanks lol but is there any way to fix gnome ppp from doing that? its annoying =\

---

### Post by mdebusk on 2007-10-29
> **HybridTheory said:**
> is there any way to fix gnome ppp from doing that? its annoying =\

I agree that it's annoying. There are several things you could do.
[list]
[*] Follow the instructions outlined in [ the bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487") to patch and recompile the source;
[*] Download and use KPPP instead;
[*] use WVDial;
[*] Do it the old-fashioned way (pppconfig, pon, and poff);
[*] Give [PPPTray]("http://www.getdeb.net/app.php?name=PPP+Tray+Icon") a shot (but you'll still need to run pppconfig for it); or
[*] do what I'm doing: move it to another workspace and wait for the update.
[/list]

I just tried PPPTray and I sort of like it. Run pppconfig from the command line, answer the questions, and configure PPPTray. It runs very smoothly and seems to take very little in the way of resources.

---

