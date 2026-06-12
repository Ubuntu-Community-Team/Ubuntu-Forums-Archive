---
title: "Linux Experts - What would you do if your os only booted half the time?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by plasticM on 2007-09-26
I was just wondering what the more experienced users on these forums would do in my position.  I'm new to Linux and have an install of Feisty that only boots half the time.  I've fully documented the problem (as best I can) here:
[http://ubuntuforums.org/showthread.php?t=558001](http://ubuntuforums.org/showthread.php?t=558001)
so I won't go into details.  But so far the thread consists of 4 posts by me, 1 requst for some file contents (posted and never replied to), and one random complaint about an unrelated problem (cheers).  I'm a bit tired of talking to myself.

So I thought I'd do a quick straw poll - what would you do?

- Put up with repeatedly restarting the machine until it works?
- Look elsewhere for help (if so, where)?
- Just use Windows?  I didn't want to go with this but at least it boots when I ask it.
- Or something else entirely (I'm sure you don't need asking to keep it polite).

Thanks for reading.  Incidentally, if anyone thinks they might be able to help with the problem, that would be great too.

Tim

---

### Post by Lord Illidan on 2007-09-26
Well, you are taking it very patiently. I might have started breaking things by now :P

Did you try removing it completely, and trying again? Or else, I'd grab Gutsy when it is in Beta (next week), and try from there.

Now, this might sound strange, but does your Dell have a floppy drive?

---

### Post by plasticM on 2007-09-26
> **Lord Illidan said:**
> 
Did you try removing it completely, and trying again? 

I could, but I've spent hours copying my old hard drives into the same partition (d'oh).
> **Lord Illidan said:**
> 
Or else, I'd grab Gutsy when it is in Beta (next week), and try from there.


I may well do that, but it does leave me with a beta OS.  And both these options could have the same problem (of course I don't know until I try).

> **Lord Illidan said:**
> 
Now, this might sound strange, but does your Dell have a floppy drive?
I have a drive from my old machine and the board has a connection, so in that sense, yes.

---

### Post by mcduck on 2007-09-26
If the machine only boots half the time I'd say it's quite likely a hardware problem. If it was software problem it would either boot every time, or never boot..

---

### Post by Lord Illidan on 2007-09-26
Try putting a floppy in that drive, and leave it there. See if the reboot problem persists. Make sure your BIOS is not set to booting from floppy.

---

### Post by Jimmyfj on 2007-09-26
If your system does come up with an error message when it refuses to boot this message would help us a lot. It seems to be a hardware specific issue. If either GRUB or your system BIOS gives any error message this might reveal the problem.

---

### Post by Lord Illidan on 2007-09-26
> **Jimmyfj said:**
> If your system does come up with an error message when it refuses to boot this message would help us a lot. It seems to be a hardware specific issue. If either GRUB or your system BIOS gives any error message this might reveal the problem.
It does, check out his thread over here : [http://ubuntuforums.org/showthread.php?t=558001](http://ubuntuforums.org/showthread.php?t=558001)

---

### Post by MinstrelBoy on 2007-09-26
As with all faults its a process of elimination.

Question - did Ubuntu work Ok before you loaded Vista ?

    yes - remove Vista and any hardware you've added, and reload Ubuntu from recovery CD, in other 
             words get the machine back to as it came from the factory.  If it works, great, if it doesn't its 
             probably a hardware problem, return it to Dell for repair.

    no - its a brand new machine with a fault, send it back to Dell for repair.

    Don't know - follow instructions for yes.

Easy .....

---

