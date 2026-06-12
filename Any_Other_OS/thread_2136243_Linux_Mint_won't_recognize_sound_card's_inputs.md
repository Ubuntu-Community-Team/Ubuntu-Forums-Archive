---
title: "Linux Mint won't recognize sound card's inputs"
date: 2013-04-17
forum: Any Other OS
---

### Post by Ender Shadow on 2013-04-17
I have an old sound card, exactly like this one *[here]("http://www.tomshardware.com/reviews/big-sound,370-5.html")*, and I ever since I switched to Linux I've never been able to get the inputs to work.
I was able to see them with Ubuntu 12.04, but wasn't able to get any sound through them. Now, with Linux Mint 13, I can only see some of the inputs (using Audacity), and can get a popping noise of sorts from one them, but that's about it. 
Do any of you have any idea of what's wrong (besides it being an old sound card), and any ideas on how to fix it?

---

### Post by mips on 2013-04-17
[http://ubuntuforums.org/showthread.php?t=1471330](http://ubuntuforums.org/showthread.php?t=1471330)

---

### Post by Ender Shadow on 2013-04-17
Thanks, man. I'll try what was suggested in that thread.

---

### Post by Ender Shadow on 2013-04-18
Alright, qjackctl got the inputs working (kind of),  but I'm having trouble recording from them. Audacity skips random frames while its recording, which isn't exactly ideal.
As for the inputs...I haven't yet isolated all of the problems with them, so I'll have to let you know later.

---

### Post by Ender Shadow on 2013-04-19
Qjackctl refuses to work now, so I would be back to square one, except that the inputs work fine on another account, so mine must be set up differently...hopefully I'll figure out what the difference is.

---

### Post by mips on 2013-04-20
Copy the config files across maybe.

---

### Post by Ender Shadow on 2013-04-20
I fixed it. All I had to do was, in the hardware tab of the sound preferences, switch my sound card profile from "Analog Stereo Output" to "Analog Stereo Duplex." I don't know why I didn't notice that sooner (although there were quite a few profile options).
I got Audacity to work (briefly); it was monitoring the sound and letting me listen to it while it was doing so, but as soon as I tried to record, Audacity spazzed out, and now it won't let me record. Oh, well, at least the inputs work now.

EDIT: Now how do I mark this thread as "Solved"?

---

### Post by BlinkinCat on 2013-04-20
Hi,

Here's how to mark thread as solved,

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

### Post by Ender Shadow on 2013-04-20
Ahh, I see. Thanks!

---

