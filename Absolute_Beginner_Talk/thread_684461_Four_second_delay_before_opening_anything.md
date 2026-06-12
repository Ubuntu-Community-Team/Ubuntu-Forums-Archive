---
title: "Four second delay before opening anything"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Keilious on 2008-02-01
I've just upgraded my computer. I had tried Ubuntu on my previous rig and had lots of trouble with the ATI card, but everything loaded lightning fast.

Now, with the same HDDs (but now suspended instead of mounted, but I can't imagine that would cause a problem), but a Q6600 instead of a P4EE, and a 8800GT, opening ANYTHING halts for 4 seconds before popping open. Even gedit, or calculator or anything under "preferences". The only thing that isn't suffering from this problem is firefox. I have 2GB of RAM, and 512MB swap... so I doubt that's part of the problem.

I'm running Ubuntu 7.10, 64 bit.

I've tried going to /etc/hosts and editting out those lines at the bottom, as I found suggested in a similar thread, but it didn't fix the problem.

Does anyone have any ideas? 
What other information should I post in order to get some help with this problem?

---

### Post by Fechter on 2008-02-01
I have 2GB of RAM, and 512MB swap... 

64 bit cannot cause the problem, but the swap has to be 1,5 times more than the ram.. I believe you will need 3 gb swap.

---

### Post by oedha on 2008-02-01
do you still use ATI ?
your swap just fine by me......

~E~

---

### Post by Keilious on 2008-02-01
> **Fechter said:**
> I have 2GB of RAM, and 512MB swap... 

64 bit cannot cause the problem, but the swap has to be 1,5 times more than the ram.. I believe you will need 3 gb swap.
No, swap is just virtual memory, if you don't use up your RAM, you don't use any swap, so the problem can't lie there. (besides, I had 512MB swap before, and this problem didn't happen)

> **oedha said:**
> do you still use ATI ?
your swap just fine by me......

~E~

No, Nvidia 8800GT now.

---

### Post by oedha on 2008-02-01
have you set your nvidia correctly......envy might help
you didnt install xserver-xgl right ? this made mine slowly too

~E~

---

### Post by Keilious on 2008-02-01
> **oedha said:**
> have you set your nvidia correctly......envy might help
you didnt install xserver-xgl right ? this made mine slowly too

~E~
I installed using envy, so that's all fine and dandy. I don't have xserver-xgl though... I'll try installing it.
Rendering the screen isn't slow though, which is odd, its just opening a new window/
Edit: Okai... I installed xgl, no difference. Should I uninstall it as it didn't appear to do anything?

---

### Post by ed-koala on 2008-02-01
I had a similar problem with opening windows.  I opened System monitor to see what was running that might be slowing me down, and found an unneeded Firefox zombie running.  Killing that helped speed up program opening.

---

### Post by Keilious on 2008-02-01
I didn't spot any really weird process (that I know of, anyway), except maybe about 6 copies gnome-vfs-daemon.

But this isn't an issue of processing power or RAM running out, each program takes exactly 4-5 seconds to load, no matter how complex or simple, or how much other stuff is open.

Edit: Hmm... There's a zombie "Python" process I can't kill or do anything to. Could this be the problem? Edit edit: According to my research, this is normal.

Edit2: Alright, I'm watching the CPU usage as I open gedit, for example. In the 5 seconds before it launches, the CPUs ramp up their usage, then drop off afterwards as expected...

---

### Post by Keilious on 2008-02-01
Bump!

Maybe something in the motherboard is making the hard-drives go into some sort of sleep constantly? I'm running on an Asus P5E.

---

### Post by Keilious on 2008-02-01
Bump. Any ideas?

Edit: Okay, everything just started working today, for no apparant reason. Possibly due to the 13KB update that popped up.

---

