---
title: "Core 2 Duo 64-bit but my comp is 32-bit?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by akiratheoni on 2007-11-22
So my computer has an Intel Core 2 Duo E4400 and the label says it's a 64-bit. I remember on Vista I believe said that my computer was 32-bit, though. I have 32-bit Ubuntu, though. So is my computer really 64-bit? I'm really confused on this subject. Sorry if it's a dumb question.

---

### Post by Dr Small on 2007-11-22
Your system is a 64bit but you are running 32bit version software.

---

### Post by overdrank on 2007-11-22
> **akiratheoni said:**
> So my computer has an Intel Core 2 Duo E4400 and the label says it's a 64-bit. I remember on Vista I believe said that my computer was 32-bit, though. I have 32-bit Ubuntu, though. So is my computer really 64-bit? I'm really confused on this subject. Sorry if it's a dumb question.

HI you can use this command 
```
cat /proc/cpuinfo 
```
and if it reports back 64 bit then :)

---

### Post by jaybombalous on 2007-11-22
Poster number two hit the nail on the head, u have a 64 bit system, u are running 32 bit software on a 64 bit system.

If u are a beginner and just like things to work then stick with 32 bit software for now.

---

### Post by delphiguy on 2007-11-22
yep you have installed a 32bit os in a 64bit system. nothing wrong with that
since theres not too much applications anyways that take full advantage of
64bit computing.  I would stick with 32bit Ubuntu since it has better support
i think.

---

### Post by LaRoza on 2007-11-22
I have heard that 64 bit has definate advantages, but for now, stick with what you have. No sense changing IMO.

---

### Post by akiratheoni on 2007-11-22
Thanks for the replies. I guess I'll try out 64-bit when Hardy comes out, then switch to 32-bit if I don't like it. Thanks :)

---

### Post by Paulmd on 2007-11-23
> **akiratheoni said:**
> So my computer has an Intel Core 2 Duo E4400 and the label says it's a 64-bit. I remember on Vista I believe said that my computer was 32-bit, though. I have 32-bit Ubuntu, though. So is my computer really 64-bit? I'm really confused on this subject. Sorry if it's a dumb question.


Not a dumb question:

What this means is that your HARDWARE is 64 bit, but has 32 bit Vista installed.

What are the practical limitations of having a 32 bit OS on 64 bit hardware?

1) You get "only" 4GB ram.
2) You may see slightly less than "optimal" performance. 64 bit hardware is a capable of a few % better performance when running 64 bit code, as opposed to 32 bit code.

Why, knowing this, was 32 bit Vista installed, instead of 64 bit?

1) It's cheaper

2) There are more drivers written for the 32 bit edition, than the 64 bit. And, using the 32bit drivers on a 64 bit system may not always work.

3) Chances are your hardware does not support more than 4GB RAM.

4) More than drivers, some software has been reported to be problematic on the 64 bit ed, vs the 32 bit. 


Can you run 64 bit Ubuntu? Yes. Should you? It might run a few % faster than the 32 bit, but otherwise... you get most of the same issues with 64bit Ubuntu as with 64 bit Vista.

---

### Post by bobpur on 2007-11-23
In my opinion, 64 bit Ubuntu is loads better than it was just a few versions ago. The difference is neglible and not worth changing as others have said. As far as I know, the only worthwhile benefits are a couple percentage points better performance and crisper sound in audio playback. However, I bet you'd have to be a serious audiophile to tell the difference. 

You made me notice though, that my new Acer laptop is a Pentium D 2.66 ghz dual core 64 bit running 32 bit Vista (for now). I hadn't caught that. I never, even, thought about it.

---

