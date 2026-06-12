---
title: "[SOLVED] Firestarter Error"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by whitethorn on 2007-12-04
When I start Firestarter from the gnome terminal with  ::  

sudo firestarter & 

then after awhile I get this message.  It's the first time I get it, and the firewall is working in the background I just wonder what this error means.  


***MEMORY-ERROR***: firestarter[11608]: GSlice: assertion failed: sinfo->n_allocated > 0

[2]+  Aborted                 (core dumped) sudo firestarter




Oh and is it possible to set up Firestarter to allow connections from vpnc, I need it to be able to connect to my universities server.

---

### Post by Paqman on 2007-12-04
Er, I have a question: why are you running Firestarter in the background anyway?

Firestarter isn't a firewall. It's a configuration GUI for the built-in firewall. You use Firestarter to configure the firewall, then you shut it down.

---

### Post by whitethorn on 2007-12-04
I was trying to configure the firewall, and firestarter kept shutting down..  I was just wondering if it might a bigger problem ..  

Ne1 know how to configure firestarter so that I can use vpnc ?

---

### Post by jimmj43 on 2007-12-04
Well,,,,,,,, OK. 

May I step in with a related (Firestarter) question or 2?

I only recently learned it was in the repository, and thought, "Why not?", so I marked it to be loaded - which it obediently did. Even gave me a nifty little icon up top next to the "updates" icon. Out of curiosity I clicked on it and was faced with a tidy status console. But when I closed the console, the icon went away......... never to return! I tried uninstalling and reinstalling to no avail using Applications > add/remove.

What do I have to do to (a) get the icon back, and (b) keep it there? :confused:

---

### Post by some_random_noob on 2007-12-04
> **jimmj43 said:**
> 
What do I have to do to (a) get the icon back, and (b) keep it there? :confused:

(A) Try finding Firestarter in applications>internet>firestarter or system>admin>firestarter. You should be able to open the FS config window from one of those locations.

(B) I think what you do is simply click the small icon at the top-right of the screen - this will make the window disappear, but the icon should remain at the top-right. This is an alternative to closing it.

Bear in mind that Firestarter can be a pain in the *** at times. I installed it a while back, but I can't be bothered with it anymore. If I look at the alt+ctrl+F8 console during bootup, it says in red that Firestarter failed to run... it seems to have lots of permission problems for me :(

---

