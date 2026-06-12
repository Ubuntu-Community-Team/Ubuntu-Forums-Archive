---
title: "Open Office Updates are not authenticated"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by Vega on 2005-10-08
Well this is the first time I got a message that me this. Should I continue with the update?
Note: I'm just trying to be sure things are smooth.

---

### Post by TravisNewman on 2005-10-08
have you enabled extra repositories? If so, it could be getting them from a different repo that doesn't authenticate. You should definitely be getting the OO updates from the official repos. 
 
If you haven't enabled any extra repositories, then this could just be a fluke. Try updating the repository listings (apt-get update, or "reload" in synaptic), and then try installing these again.
 
If you still get the message after all this, let us know.
 
BTW, gotta love Reptile.

---

### Post by Vega on 2005-10-08
Yes I still get this message after "apt-get update" and reload in synaptic.
The update manager also told me about a exclusive lock that I have to exit apt-get but I already closed the terminal.

MKII is the best!

---

### Post by Mustard on 2005-10-08
Somtimes I have trouble getting updates on security keys with Synaptic.  I usually keep refreshing it until it decides to stop complaining about them.  I also try doing an apt-get update via command line too, which seems to work much better than via Synaptic itself.  Being on dialup, I never trust that my connection was certain enough that a second, third or fourth try isnt worth the effort.

---

### Post by Vega on 2005-10-08
[QUOTE=Mustard]Somtimes I have trouble getting updates on security keys with Synaptic.  I usually keep refreshing it until it decides to stop complaining about them.  I also try doing an apt-get update via command line too, which seems to work much better than via Synaptic itself.  Being on dialup, I never trust that my connection was certain enough that a second, third or fourth try isnt worth the effort.[/QUOTE]

you are right, now it stops complaining. thanks for your help guys!

---

