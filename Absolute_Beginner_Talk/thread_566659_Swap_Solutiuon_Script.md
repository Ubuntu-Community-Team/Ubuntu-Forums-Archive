---
title: "Swap Solutiuon Script"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-10-03
I made this simple little script to go through your swap file and remove anything old that's still there, and anything that's still needed gets put back in RAM.  It comes with a little warning about not using it if you can't currently fit your entire swap contents in ram (just in case none of it's old), but in a serious situation, I believe it would simply deny you the ability to over fill your ram and crash :p

I haven't included a license because this is just two common commands basically :)  Do what you want with it!

---

### Post by llamakc on 2007-10-03
Maybe Absolute Beginner Talk is the wrong place for this? And where did you discover that running swapoff would flush stuff from swap to RAM?

---

### Post by ryanVickers on 2007-10-03
Why?  It's quite simple - just run it and it'll speed up your system a bit :)

Edit: Also, If I wanted a discussion about it, I'd put it in programming, but this is just a give-away to everyone, experienced or not! :)

---

### Post by llamakc on 2007-10-03
> **ryanVickers said:**
> Why?  It's quite simple - just run it and it'll speed up your system a bit :)

Edit: Also, If I wanted a discussion about it, I'd put it in programming, but this is just a give-away to everyone, experienced or not! :)

How does it speed up a system if nothing is currently in swap?

---

### Post by ryanVickers on 2007-10-03
Well, the nit wouldn't :p, but If you've just come out of running a VM and the rest of your "real" system's in swap, this will put it back where it should be :)

---

### Post by llamakc on 2007-10-03
> **ryanVickers said:**
> Well, the nit wouldn't :p, but If you've just come out of running a VM and the rest of your "real" system's in swap, this will put it back where it should be :)

I run Gutsy and Windows in a VM and my system's responsiveness seems to jump back to normal after a few seconds. Is this script for lower-RAM machines primarily? If so maybe the first post should specify that.

So what happens if somebody does NOT have enough RAM when swapoff is run in your script?

---

### Post by ryanVickers on 2007-10-06
Well, in theory, the commands it's running have a built in safety feature that will prevent this from happening, but if someone was to start up a ram hod app during the cleaning process, it *could* be bad.

As for the amount, if you've got 2Gb of ram or more, you should be fine, but anything less (like 1GB or under) will likely benefit from this sooner or later

---

