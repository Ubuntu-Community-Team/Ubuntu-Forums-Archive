---
title: "Possible framebuffer problems, random colors and computer lockup on boot."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by AngryMallard on 2008-01-20
OK this is the absolute last time I try and figure out what is wrong with this computer.

I have a Dell Dimension 2350 that has been a pain in my neck since I got it. It's one of Dell's budget computers that I obtained for free. It has 512 mb ram, 2.00 gHz Pentium 4, and an Intel integrated graphics card that can use either the i810 driver or the intel driver. That's mostly my problem.

Any way, about six months ago it ran Kubuntu Feisty absolutely fine. No problems. Then I put Windows on it for reasons we won't go into here, but now I am trying to run Ubuntu 7.10. About a month ago I used the text installer to put Ubuntu 7.10 on it but when it booted up at first it wouldn't quite make it to the login screen before the whole screen froze on random vertical stripes of color. Total computer lockup. That happened about six times before I tried Fedora 8. I didn't have any problems with that after using it for about a month, but then I decided I liked Ubuntu better and tried again.

This time I used the LiveCD to install it, thinking it was a driver problem (the integrated video is more trouble than any other piece of hardware I've ever had to deal with). The install worked! I got a working desktop using my favorite operating system!

For about two weeks. I came back to my computer one afternoon and it had locked up. I did a hard reboot and now it's back to locking up just after the GUI starts and showing random vertical stripes of colors.

If no one can help me, I think I'll just put text-only Gentoo on it and have it crunch Folding at Home work units. Although I'm a poor college student and I'd like to get this thing working (with Ubuntu) so I can have a computer in my lab without having to spend money on a new one.

---

### Post by AngryMallard on 2008-01-20
OH I forgot to mention. The Ubuntu screen that has the progress bar when the computer starts up has never shown up on that computer. That's what makes me think it's a possible framebuffer problem.

---

### Post by AngryMallard on 2008-01-22
Please help! I'm using Fedora right now but it's so much harder to get all the audio/video plugins working! What a pain!

---

### Post by AngryMallard on 2008-02-02
For some reason, my monitor was the catalyst for the problem. I have a 21'' flat-panel HD monitor from Gateway that was causing the computer to crash for some reason. I'm not sure what the underlying problem was, but when I went back to an old CRT everything worked perfectly and still does.

---

### Post by Shazaam on 2008-02-02
I wouldn't toss that lcd in the garbage just yet. The problem is probably linked to the integrated graphics card that shares MAIN memory for operation and the weak power supplies Dell installs.

---

