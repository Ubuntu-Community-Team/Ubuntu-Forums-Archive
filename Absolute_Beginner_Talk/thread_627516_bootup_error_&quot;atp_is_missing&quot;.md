---
title: "bootup error &quot;atp is missing&quot;"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Lderan on 2007-11-30
When I boot up my computer it goes into (what looks like command prompt) and says that "apt" is missing and to install it with  "apt-get install apt".

This doesn't seem to work. I have also tried putting sudo infront of it, but it comes up with an error saying "sudo" isn't a valid command.

Help please

---

### Post by eluzi on 2007-11-30
I don't know exactly what program is this but Gdesklets does the same thing and u can install it from Synaptic. ;)

---

### Post by philinux on 2007-11-30
> **Lderan said:**
> When I boot up my computer it goes into (what looks like command prompt) and says that "apt" is missing and to install it with  "apt-get install apt".

This doesn't seem to work. I have also tried putting sudo infront of it, but it comes up with an error saying "sudo" isn't a valid command.

Help please

What are the other error message before this. Anything to do with fsck by chance?

Is this a new install?

Can you boot into recovery mode via grub. ie press esc as soon a stage 1.5 comes up then select recovery mode option.

---

### Post by zabien1970 on 2007-11-30
Which version of ubunu are you using? fiesty, gutsy, kubuntu?

---

### Post by Lderan on 2007-11-30
Its fiesty fawn, will have to go see if there were any more errors, but i can't remember seeing any.
Its not a fresh install, its been on the computer for a couple of weeks now. 
Also yes i can boot into recovery mode.

---

### Post by Lderan on 2007-11-30
Is there nothing i can do? I need to save some files so I can finish off some work for my university assignments but some won't copy to my pendrive.

Help me please D=

---

### Post by FuturePilot on 2007-11-30
Your drive might need to be fscked. I've seen others report that usually fixes it.
You can do it from the live CD, just do
```
sudo fsck /dev/sdaX
```
from the live CD
Where X is the partition number. Just make sure it's **not** mounted or else it could really get messed up

---

