---
title: "Password no longer working?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-04-06
So, I feel pretty stupid. My login user name or password no longer works.

Caps is not on. Num lock is normal. Keyboard is working. I haven't changed passwords for 3 months. I didn't forget it. But I'm not able to log in. What can I do?

---

### Post by kellemes on 2008-04-06
> **imaginal said:**
> So, I feel pretty stupid. My login user name or password no longer works.

Caps is not on. Num lock is normal. Keyboard is working. I haven't changed passwords for 3 months. I didn't forget it. But I'm not able to log in. What can I do?

[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by tamoneya on 2008-04-06
try booting into recovery mode by hitting escape during GRUB.  This will give you root shell access. then run ```
passwd username
```

---

### Post by saj0577 on 2008-04-06
A little of topic anyway to stop people doing this to your system other then drive encryption?

Saj

---

### Post by JoshuaRL on 2008-04-06
> **saj0577 said:**
> A little of topic anyway to stop people doing this to your system other then drive encryption?

Saj

BIOS password.  But don't forget it, you probably won't be able to reset that.

---

### Post by saj0577 on 2008-04-06
Okay then. Cheers, just whats the point in having a password if someoen can change it that easily, (without doing other passwords, bios, etc)

Saj

---

### Post by tamoneya on 2008-04-06
well you can put a password into grub so that people cannot boot into the recovery mode.

---

### Post by aysiu on 2008-04-06
> **saj0577 said:**
> A little of topic anyway to stop people doing this to your system other then drive encryption?

Saj
Nothing.

Physical access is root access.

---

### Post by saj0577 on 2008-04-06
> **tamoneya said:**
> well you can put a password into grub so that people cannot boot into the recovery mode.


How?

Saj

---

### Post by saj0577 on 2008-04-06
> **aysiu said:**
> Nothing.

Physical access is root access.

Yeah but their must be things to prevent it and people are only willing to try so much to get into your computer.

Saj

---

### Post by JoshuaRL on 2008-04-06
> **saj0577 said:**
> Okay then. Cheers, just whats the point in having a password if someoen can change it that easily, (without doing other passwords, bios, etc)

Saj

Well, physical access is the weak point of all computer systems.  With almost all OSs, if someone really knows what they're doing and has physical access to your computer then you're in trouble.  And if you have a BIOS password and/or drive encryption then you're set.

But I agree that Recovery Mode may be one of the biggest security issues Ubuntu has.  I've had this discussion with some really smart people, and all I can offer is this:

You can put an encryption on the disk, and you can disable Recovery Mode in GRUB so that no one can get into it.  But in the end Recovery Mode is such a valuable tool for fixing a computer that it needs to stay as it is.  And how awesome is it that Ubuntu is so secure that we're worrying about physical access?

---

### Post by bsharp on 2008-04-06
> **JoshuaRL said:**
> BIOS password.  But don't forget it, you probably won't be able to reset that.

Not entirely true, if you know your jumpers you can either find the one that resets CMOS settings or take out the motherboard battery.

---

### Post by tamoneya on 2008-04-06
The only way that is considered foolproof is to encrypt your harddrives.  Anything else can be circumvented in some way or another.  Even this is now debated though as some researchers (stanford?) managed to extract encryption keys off of the ram by cooling it down and rebooting the computer quick enough so that the ram data wasnt lost.

---

### Post by saj0577 on 2008-04-06
Got to be a way to clear ram, swap and all temp files on shutdown?

Saj

---

### Post by JoshuaRL on 2008-04-06
Which brings back the point that physical access is the weakness of any computer system.

---

### Post by aysiu on 2008-04-06
> **saj0577 said:**
> Yeah but their must be things to prevent it and people are only willing to try so much to get into your computer.

Saj
I think the words you're looking for are *slow down* or *make inconvenient* instead of *prevent*.

---

### Post by saj0577 on 2008-04-07
Yeah thats what i was thinkin just didnt type it lol.

Saj

---

