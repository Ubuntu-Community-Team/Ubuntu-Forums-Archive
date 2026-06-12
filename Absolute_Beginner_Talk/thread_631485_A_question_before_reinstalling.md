---
title: "A question before reinstalling"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by jobbesat on 2007-12-04
I have 2 hard disks, on one there's ubuntu gutsy, in the second i have windows xp and debian.
i have (SIGH) to reinstall windows xp, because it crashed and lost some files and now it does not work properly, even if i use it 2 times in a month.
I can loose debian because I installed it but never use it; the question is how to reinstall windows xp without loosing grub data?
I mean now grub contains all informations to start ubuntu/windows/debian, I want to reinstall windows on the second hd, but I don't want windows to overwrite the mbr where grub resides; is there a chance to avoid this or not? And if not, i. e. windows installation will overwrite mbr, how can i recover it? I can't reinstall ubuntu because I would loose a lot of data.

Thanks a lot in advance for your help.

---

### Post by tszanon on 2007-12-04
Select the Windows disk in BIOS to be your first disk. Installing windows in that disk you rewrite that disk's MBR, but, since grub is in the other disk, it's safe. I've done that 3 times. After installing windows, go back to BIOS and select the ubuntu disk as the first disk again. Maybe then you'll need to configure grub in order to being able to boot windows, but that's another story.

Other option is reinstalling grub after installing windows, using a livecd. I'm gonna search for the thread telling how to do it.
Edit: here's the thread: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Another option is simply disconnecting the Ubuntu disk before installing windows.

---

### Post by sethvath on 2007-12-04
If you go for the 3rd method, remember to reset the primary/secondary slave pin arrangement at the back of the hdd. Happened to me several times before.

---

### Post by jobbesat on 2007-12-04
;Many thanks for the replies, i will try this afternoon

---

### Post by jobbesat on 2007-12-05
I forgot to mention a fundamental detail; since I installed debian after ubuntu, the grub has been installed by debian, consequentelly i think that grub resides on second hd, that one with windows and debian. So what to do in such a case?

Thanks a lot

---

### Post by tszanon on 2007-12-05
Maybe debian rewrote grub, so now it points to debian boot files.

Just to be sure, I would simply reinstall windows (methods 1 or 3, as I stated before). After installation, if grub does not come up, use a livecd to reinstall it (method 2).

Generically speaking, If you're prepared to face a problem, then it's no big deal.
Come back after the procedure and tell us any problems you've had.

---

### Post by hyper_ch on 2007-12-05
just reinstall grub again. It's not a big deal there. There's plenty of howtos for that ;)

---

### Post by jobbesat on 2007-12-06
Just to let you know that everything is fine now; i used method n. 3 and then reinstall grub
So, many thanks for your help

---

### Post by tszanon on 2007-12-06
It's good to hear that you've succeeded. Congratulations! :)

---

