---
title: "Computer freezes on install"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by ablot on 2007-07-24
I have a good working cd 
... I have a laptop with no system on it (windows was wiped off during previous unsuccessful attempt at loading ubuntu)
So far I have had to install via the safe mode 
... in partitioning I choose guided using entire disk
... I get to 7th dialogue page (installing ubuntu) 

... It freezes at 15% install whilst detecting the system.

Please can someone help.

---

### Post by Bachstelze on 2007-07-24
Have you tried using an Alternate CD ?

---

### Post by ablot on 2007-07-24
Why should I use an alternative CD? Is it any different? Where do I get it from? Will I have sum5 check it?

---

### Post by Bachstelze on 2007-07-24
It has an "old-school", text-based installer. So it's a bit less pretty but also far less likely to fail on you, and no more difficult. You can get it from the same location you got your Desktop CD from.

---

### Post by ablot on 2007-07-24
Ive downloaded the alternative iso.
sum5 ... ok
burned the iso onto cd
put in the laptop ... was given the options
I decided to check the cd
... it checked it ... but all that came up on the screeen was incomprehensible - no text at all
I used Deep Burner to burn the iso (which I have used successfully before)

... so what went wrong?

---

### Post by dptxp on 2007-07-24
Post hardware details. You will get better answers.

---

### Post by ablot on 2007-07-24
hardware details? You had better know that I'm not just an ubuntu newbie ... I also know very little techno stuff ... I can draw you a picture ... but hardware ... hm lets see ...

40gb laptop
256mb memory
It had windows ... which doesn't work any more

... thats about it ... what do you need to know?

---

### Post by ablot on 2007-07-24
Is there no one out there that can help me install ubuntu.

I have the cd ... I have the laptop.

But what ever I try to do it freezes on 15% of system installation onto the hard disk while it is "detecting file systems"

---

### Post by ablot on 2007-07-24
Just for your information ... I have tried loading MEPIS ... it worked a dream - no problems.

Thanks for all your help.

---

### Post by dptxp on 2007-07-25
> **ablot said:**
> hardware details? You had better know that I'm not just an ubuntu newbie ... I also know very little techno stuff ... I can draw you a picture ... but hardware ... hm lets see ...

40gb laptop
256mb memory
It had windows ... which doesn't work any more

... thats about it ... what do you need to know?


Your RAM is 256 MB. That is the problem.
One way to install is to use the alternate CD.
But you can also use the method given below:-
Download GParted. Make live CD of GParted. make a 2 GB (minimum 1 GB) SWAP partition at end of the drive (you can make anywhere).
You will be able to install from Live CD.

---

### Post by mivo on 2007-10-03
> **dptxp said:**
> Your RAM is 256 MB. That is the problem.

I experience the same "hanging at 'detecting file system' at 15%", and that is on a 1 GB RAM machine with 3.0GHz. It happens with both the 7.04 and 7.10beta Live CDs. Kubuntu had no such problems, so I am relatively sure that the problem is specific to the Gnome version of the installer. Downloading the 7.10 Alternate Installation CD right now.

There are other threads about the "15% problem", so it seems to be a more common trouble. It's curious that it only seems to affect Ubunutu but not Kubuntu.

---

### Post by mivo on 2007-10-03
Installing Gutsy with the alternate CD worked flawlessly. It sat a long time at 90%, saying "please wait ...", while it apparently downloaded at least 100+ MB. It gave no indication of what it was doing, though, I only "guessed" by the noises the hard drive made. :)

---

