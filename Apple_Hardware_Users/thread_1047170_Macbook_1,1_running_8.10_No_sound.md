---
title: "Macbook 1,1 running 8.10 No sound"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by be249322 on 2009-01-22
As the title says no sound besides the initial chime... there is alot of posts about not having sound but they are usually for 8.04 and i seem to run into issues when trying to apply those fixes to 8.10. 

Sound is crackling but besides that i am clueless? Any suggestions?

---

### Post by cyberdork33 on 2009-01-22
run 'alsamixer' in a terminal and make sure that the channels are unmuted and turned up.

---

### Post by be249322 on 2009-01-22
> **cyberdork33 said:**
> run 'alsamixer' in a terminal and make sure that the channels are unmuted and turned up.

Both the master and capture are all the way up and not muted.

---

### Post by cyberdork33 on 2009-01-22
OK Right-Click on the Speaker Icon near the clock and "Open Volume Control"

There make sure that the Master and PCM channels are not muted and turned up.

---

### Post by be249322 on 2009-01-23
You are a life saver and i am an idiot... haha but now its alittle crackley... if that was a word... is it just the balance of the master PCM and front?

---

### Post by cyberdork33 on 2009-01-23
> **be249322 said:**
> You are a life saver and i am an idiot... haha but now its alittle crackley... if that was a word... is it just the balance of the master PCM and front?
we are really not sure why that happens, but we found that keeping your volume level a bit lower in the OSX side sometimes makes the crackling go away

---

