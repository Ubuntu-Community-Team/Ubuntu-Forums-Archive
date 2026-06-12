---
title: "[SOLVED] 32 or 64bit?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by ThomasWM on 2008-03-29
I recently bought the Tesco eSys machine with ubuntu loaded, as I have been meaning to get away from XP for a while.
I've been doing a lot of experimenting with the system, and I like it.
The processor is Celeron D 3.2 GHz which, I believe, is 64 bit.
What I would like to know is how I can tell if the 7.10 now on the machine (it was 7.04 as delivered, with a 6.06 disk provided!) is 32 or 64 bit version.

---

### Post by wolfen69 on 2008-03-29
see this [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by Andavane on 2008-03-29
> **ThomasWM said:**
> I recently bought _the Tesco eSys machine_ with ubuntu loaded, as I have been meaning to get away from XP for a while.
I've been doing a lot of experimenting with the system, and I like it.
The processor is Celeron D 3.2 GHz which, I believe, is 64 bit.
What I would like to know is how I can tell if the 7.10 now on the machine (it was 7.04 as delivered, with a 6.06 disk provided!) is 32 or 64 bit version.

A machine loaded with Ubuntu from TESCO? Really?
Wonders never cease!
Any more info you can give here?
Regards
John

---

### Post by jdrodrig on 2008-03-29
Can you post the output of typing *uname -a* in the terminal?

---

### Post by ThomasWM on 2008-03-29
Firstly, the Tesco machine details.:- TescoDirect. (they undersell it on their website)
eSys, Celeron D 3.2 Ghz, 512M DDR2 533, 80G SATA HD, DVD Rom, 300W PSU,  KBD, Opt Mouse, Speakers (tatty), £140 (no monitor, of course)

Now, wolfen69....Thanks for the reply.
I've seen your link, but what I am after is a way of finding out from my loaded program if it is 32 or 64 bit ( a sort of equivalent to 'Help............About) I didn't see that in the link, but maybe I missed it!

---

### Post by jdrodrig on 2008-03-29
in the system I use, I get the following from uname -a ...so the last part x86_64 would indicate it is a 64bit platform...(at least as far as I know)

*Linux cartman 2.6.9-67.0.1.ELsmp #1 SMP Fri Nov 30 11:57:43 EST 2007 x86_64 x86_64 x86_64 GNU/Linux*

---

### Post by ThomasWM on 2008-03-29
twm@esys-desktop:~$ uname -a
Linux esys-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

Thanks, jgrodrig.   does the underscore64 imply 64 bit, or am I assuming too much?

---

### Post by Inxsible on 2008-03-29
Yes.. If you had a 32 bit, it would just say x86 architecture.

---

### Post by NightwishFan on 2008-03-29
64-bit for the win! Processor is always scaled at half power because it never needs to use any more than 10%

---

### Post by ThomasWM on 2008-03-29
Thanks again JD, you answered my question before I got the answer to it!:)

---

