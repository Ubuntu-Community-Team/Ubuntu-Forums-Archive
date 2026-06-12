---
title: "2 more questions"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by BDNiner on 2007-07-24
What kind of processor is a sempron? Is it 32 bit or 64 bit. I can't find the old box anywhere and can't seem to figure out if i should use 32bit or 64bit version of ubuntu.

Where do people get the various penguin avatars?

---

### Post by sad_iq on 2007-07-24
I think that AMD sempron is 64bits...but you could save yourself a lot of trouble by installing the 32 bit ubuntu...you won't notice any difference in speed and there are apps that have trouble working in 64 bit!!!
 Don't really know about the avatars...try google-ing...there should be plenty!!!

---

### Post by skymera on 2007-07-24
use 32 bit, generally its more supported.

and poenguin..hmm

GOOGLE!!! i searched linux, tux anything like it and you get laods :)

---

### Post by Skrynesaver on 2007-07-24
> **BDNiner said:**
> What kind of processor is a sempron? Is it 32 bit or 64 bit. I can't find the old box anywhere and can't seem to figure out if i should use 32bit or 64bit version of ubuntu.

Semperon processors come in both varieties, as a general rule if the socket on your motherboard is a "939 socket"  or a late model 754 socket [Check here]("http://en.wikipedia.org/wiki/Sempron#Socket_754_32-bit_Semprons")
it's 64 bit.
> **BDNiner said:**
> 
Where do people get the various penguin avatars?
[Tux avatars available here]("http://tux.crystalxp.net/en.html")

---

### Post by RomeReactor on 2007-07-24
Hi. If in doubt, run this command:
```
sudo lshw -class processor
```
and look at the line "width"; it should read **width: 64 bits** (see attachment).

However, I agree that you'll be better off using the 32-bit version.

---

### Post by BDNiner on 2007-07-24
I thank every body for the quick replies. I have a 32bit processor. These forums are very helpful, and not filled with flame wars.

---

