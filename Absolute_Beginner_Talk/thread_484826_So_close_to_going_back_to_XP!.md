---
title: "So close to going back to XP!"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by davie668 on 2007-06-26
I'm just about to move back unless i get the sound fixed on FF! There is a really irritating hiss then on occasions no sound at all! I have no idea how to use Linux/Ubuntu so if some one could help it'd be so greatly appreciated.

A step by step walk through for complete idiots page would be nice :D

Dave

---

### Post by cogadh on 2007-06-26
What sound card do you have?

---

### Post by kevdog on 2007-06-26
Download alsamixer.  Possibly you already have this installed.  You probably do not have something activated.

---

### Post by davie668 on 2007-06-26
its an onboard one 
HDA VIA VT82xx

---

### Post by kelvin spratt on 2007-06-26
you need to post as much info about your system as you can first.Then look in the How too and multimedia sections while you wait most answers are their and it may save you time.

---

### Post by davie668 on 2007-06-26
What sort of info should i include?
Cheers for the help 
Really can't wait to get this sorted and start enjoying Ubuntu

---

### Post by davie668 on 2007-06-26
> **Vismund Cygnus said:**
> OK, there's the solution I've found:

set "options snd-hda-intel position_fix=1 model=3stack" to "/etc/modprobe.d/alsa-base"

Here's the reference: [Audio Left Channel Problem]("http://forums.nvidia.com/lofiversion/index.php?t18109.html")

I've found this solution but i haven't a clue what it means or how to do it...... Could someone please help! I hope this works:D

---

### Post by rpw on 2007-06-26
If this is the solution (can't tell at this point), you have to do the following:

1) Open the file "/etc/modprobe.d/alsa-base" with sudo
=> sudo gedit /etc/modprobe.d/alsa-base

2) At the end of the file you will find some entries begining with "option ...". There you can write the needed entry
=> options snd-hda-intel position_fix=1 model=3stack

3) After saving the file you can let the system reload the modules, but due to brain failure I can not remember the command to do this ;-) What will work - of course - is a reboot of the system, so the modules will get loaded.

Regards,

rpw

---

### Post by davie668 on 2007-06-26
I think I may have just found GOD! 

Hahaha Sound is working! Yipppeee!

Roll on a happy life with Ubuntu as all you need is music!

Cheers everyone!

Dave :D:D:D:D:D:D:D:D

---

### Post by tgalati4 on 2007-06-26
Sound fixed in one hour.  Not bad for support.

---

### Post by FleetAdmiral74 on 2007-06-26
You had no idea what you were doing and were ready to move back? What the heck is your motivation for using Linux in the first place, if at the first sign of trouble you are ready to quit?

---

### Post by mjwhitfield on 2007-06-26
thats less time than my average call to dell.

---

### Post by ITdrummer on 2007-06-26
Does anyone else think that it's a coincidence that Dell rhymes with Hell? :evil:

---

### Post by ITdrummer on 2007-06-26
Does anyone else think that it's a coincidence that Dell rhymes with Hell? :evil:

---

### Post by ITdrummer on 2007-06-26
Does anyone else think that it's a coincidence that Dell rhymes with Hell? :evil:

---

### Post by ITdrummer on 2007-06-26
Does anyone else think that it's a coincidence that Dell rhymes with Hell? :evil:

---

### Post by ITdrummer on 2007-06-26
i apologize for the multiple posts, my connection was interrupted while sending.  Wow i feel like an idiot now! lol

---

### Post by FleetAdmiral74 on 2007-06-26
Qua-Qua-QUADRUPLE POST!!!

---

### Post by zero244 on 2007-06-26
Hey this was your lucky day...........we prevented you from going back to Dell Windows Hell.
Dell and Hell...........arent they one and the same.

---

### Post by Cypher on 2007-06-26
> **ITdrummer said:**
> Does anyone else think that it's a coincidence that Dell rhymes with Hell? :evil:
You know that would be really interesting if Dell wasn't the last name of the person who started the company. If it was a made-up name then that's something..

---

### Post by kittyhawk63 on 2007-06-26
ITDrummer's four posts show good cause why the writer of a post should have the ability to "delete" a post. If we had this ability, ITDrummer could delete the last three posts he made.
kh

---

### Post by ITdrummer on 2007-06-26
> ITDrummer's four posts show good cause why the writer of a post should have the ability to "delete" a post. If we had this ability, ITDrummer could delete the last three posts he made.
I agree! Sorry 'bout that guys(or girls) damn Politically correctness!

---

### Post by ITdrummer on 2007-06-26
> You know that would be really interesting if Dell wasn't the last name of the person who started the company. If it was a made-up name then that's something..
I realize that the company was named after Michael Dell.  I was just saying that that i was a coincidence. geez!

---

### Post by w4ett on 2007-06-26
There has been some site maintainence going on, and there have been several multiple posts, but I agree with the "remove post" option.

---

### Post by tgalati4 on 2007-07-01
Well, I noted that it was 58 minutes from the first post of the problem to resolution.  It could have been quicker, but the original poster didn't post any hardware information and it took 3 more posts to get useful information.  We could have fixed it in 15 minutes if we had a detailed first post.

Let's see Dell beat that statistic.

---

