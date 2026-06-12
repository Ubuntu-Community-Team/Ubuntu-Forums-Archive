---
title: "[SOLVED] access my CD drive"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by viiv on 2007-10-14
I'm having problems accessing my CD drive. It worked fine after the UBUNTU 7 XFCE install, but now I just can't find it. When I put a cd in the drive, the cd spins, but nothing happens after that, no indication on my desktop or in my file manager that would allow me to access the cd drive. Originally, I wanted to burn to the disk, and I realized it was not working, but it seems I am not even able to read cds from the drive. Is there a way to get in there and have a look? The computer does recognize the presence of a cd long enough to spin it for a while after I put it in the drive, but after that, nothing. 

I'd appreciate any help on this issue.
thanks

---

### Post by Frak on 2007-10-14
Paste the output of
```
cd /dev/
ls
```

---

### Post by Mr.Beast on 2007-10-14
Is the CD drive definately being detected in the bios?
When the compuer first boots up, if you can enter the setup menu and check.
If it's not them perhaps the power cable is o.k. internally, but the data cable has come loose.

---

### Post by viiv on 2007-10-14
> **Frak said:**
> Paste the output of
```
cd /dev/
ls
```

> **Mr.Beast said:**
> Is the CD drive definately being detected in the bios?
When the compuer first boots up, if you can enter the setup menu and check.
If it's not them perhaps the power cable is o.k. internally, but the data cable has come loose.

Thanks for the quick replies
FRAK: I get a huge list. I think I see where you're going with this, but I actually figured out the problem... 
MRBEAST: You made a good point about the Bios. I actually wasn't able to find any sort of configuration of the CD drive in the bios, but restarting solved the problem. 

_Heres a note for anyone running xubuntu 7 with an IBM thinkpad x40. The  CD drive in the DOCKING STATION will not necessarily be recognized unless you dock and then restart the computer. Windows can find it if you dock the computer live, but it doesn't look like xubuntu can figure that out. _

I appreciate the help! :)

---

