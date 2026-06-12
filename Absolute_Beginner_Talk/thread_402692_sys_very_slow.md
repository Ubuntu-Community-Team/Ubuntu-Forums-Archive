---
title: "sys very slow"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by claws_crystal on 2007-04-06
I used windows for some time, as I got a virus in sys I formatted whole hard disk and loaded ubuntu(6.06). From that time, My sys became very slow. I didnt understand the problem..
I installed MPlayer on it. Im getting video but it is saying "Xvideo support is not available". I dont know what it mean.... 
Can you guys help me

---

### Post by LaurelLynn on 2007-04-06
Dear claws_crystal,

There are several thing that could be slowing everything down for an extended time. The two most likely are a program stuck in an endless loop, or a shortage of memory is causing it to use the swap space a lot (storing memory on the disk drive is very slow).

I would look first at the menu bar for:   System->Administration->System Monitor

Click on the second tab resources.  If the blue graph  under ¨CPU¨ if always at the top, a program is stuck (probably MPlayer).

If the memory in green is almost 100%.  And the purple swap space is 50% or more, you have run out of memory.

The tab marked processes has two columns, %CPU, and Resident Memory which indicates how much of that load is comming from each process. You can click on a process if it is consuming all the time or memory, then the ¨End Process¨ to stop it.  BUT I would not recommend doing that until you have asked someone here whether that process is safe to stop.

If it comes back when you reboot, you will need to come back for help on removing it permanantly. We need to know which program is at fault though before anyone here can help you further.

Laurel Lynn

---

### Post by jvc26 on 2007-04-06
You need to install the relevant codecs to play the videos: see [here]("https://help.ubuntu.com/community/RestrictedFormats")
Il

---

