---
title: "how to enchance ubuntu performance?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by half_lif3 on 2006-06-15
my computer is currently very slow 
open the evolution mail program it need 15 minutes to open the program.
even after the prorgram
open a mail need a couple of minute

is there anything i can do to enchance or speed up the performance?
such as disk defragment or anything that can help me.
help needed urgently:confused: 
:(

---

### Post by xwipeoutx on 2006-06-15
What's the specs of your PC?

What version of Ubuntu are you running?

15mins to open evolution is insane...

---

### Post by half_lif3 on 2006-06-15
celeron 1.7ghz
128 ram

do ubuntu hav system tool like disk defragment or scan disk ...?:confused:

---

### Post by IYY on 2006-06-15
Fragmentation is not your problem; it very rarely happens in Linux and when it does happen it gets cleared automatically (once every several unclean resets). You are a bit short on RAM to run Gnome. Try switching to XFCE or the even faster Fluxbox or IceWM.

---

### Post by racecat on 2006-06-15
Is this a new phenomenon? The only thing I have seen that causes that kind of slowdown is leaving Firefox up for a couple of days. It has memory management issues and chews up swap. Once swap is full, 15 mins. is normal. If this is the case, shut down Firefox. It may take a while; just wait for it. I learned this the hard way (I had to figure it out myself).

128M of RAM is light. I seem to remember a minimum between 128 and 256 mentioned somewhere in the Dapper install documentation, but I could be wrong. I think it was framed as what to do if you had less than that amount of memory. I'll have a look-see if I can find that reference.

I'm pretty certain there is no disk defrag available or needed in Linux.

Good luck,
Bill

---

### Post by kenweill on 2006-06-27
[QUOTE=racecat]
I'm pretty certain there is no disk defrag available or needed in Linux.
[/QUOTE]

Yes there is. Its "defrag - ext2, minix and xiafs filesystem defragmenter". Found in the repositories(universe). I think the default filesystem for Ubuntu uses ext3. Well, this seems useless. I dont know any defragmenter for ext3.

[QUOTE=IVY]
Fragmentation is not your problem; it very rarely happens in Linux and when it does happen it gets cleared automatically (once every several unclean resets)
[/QUOTE]
It rarely happens so that means it will happen. By the way, what if it doesnt have several unclean resets, how can fragmentation be solved?

I've read in some forums that Bittorrent causes fragmentation. Is it true?

---

