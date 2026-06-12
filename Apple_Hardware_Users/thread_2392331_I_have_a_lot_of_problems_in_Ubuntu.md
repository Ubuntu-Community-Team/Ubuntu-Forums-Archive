---
title: "I have a lot of problems in Ubuntu"
date: 2018-05-19
forum: Apple Hardware Users
---

### Post by icebunny08 on 2018-05-19
1 No sound output when I am using my headphones and earphones
2. When I use the built-in speakers, the sound quality is kinda bad
3. I downloaded a game via Ubuntu Software, and now... It won't install!
4. Why can I only use the sudo apt command one-at-a-time and I have to kill the process again and again to use it on another terminal window?
5. Rhythmbox is really slow, or it doesn't respond at all.
P.S. I am using an iMac late 2012 with 8GB ram

---

### Post by TheFu on 2018-05-19
Welcome to the forums.

Isn't there a Mac-specific subforum here?  That is where Mac questions tied to Mac hardware  are best asked.  Always lead with "Mac " in the question title if it is hardware related to help people unfamiliar avoid.

4.  there is 1 DB for package management. To reduce the chances of corruption, exclusive locking is used. You should not "kill" apt. That is a good way to corrupt the DB or at least leave it marked as *in-use*.  Also, since Unix is multi-user and many systems are remotely managed. This protection is very important since there might be 10 other admins trying to perform admin tasks on the same system.

5.  Yes.  There are 20 other audio players you can try to see if those work better on a 6+  yr old system.  I like cmus, but some people like Clementine or xmms or one of the others.  Different players for different tastes. It also helps if the music is organized into different directories (single directories with over 500 files can be slow). The first run, all the media has to be scanned and organized, so it takes a while for any non-trivial collection.  But after that is finished, it should be much faster.  A slow disk will be slower than a fast SSD or even a fast spinning HDD.

BTW, it is best to ask 1 question at a time since the expertise for everything are seldom something a single person knows.  As examples, I don't have a clue about mac stuff or "Ubuntu Software". 

It is also helpful to say your experience level, so replies can be written for that target expertise.

Lastly, which version of Ubuntu are you using?  Each different release has slightly different tweaks and settings, as do the different GUIs, so sharing that data would be very helpful, always.

---

### Post by QIII on 2018-05-19
Moved to Apple Hardware Users

---

### Post by icebunny08 on 2018-05-21
I am using Ubuntu 18.04 LTS. And thank you for the recommendations and help!

---

### Post by icebunny08 on 2018-05-21
This isn't an Apple Hardware Issue... Everything is fine, but if I boot into Ubuntu, headphones do not work, and the quality of the bad is a little bit more bad.

---

### Post by TheFu on 2018-05-22
> **icebunny08 said:**
> This isn't an Apple Hardware Issue... Everything is fine, but if I boot into Ubuntu, headphones do not work, and the quality of the bad is a little bit more bad.

Understood.   And that is very good to know.

Often times the way Apple does things is different from the ways every other vendor does it.  Not bad, not good, just different.  Headphone jacks are 1 example.  Sometimes only another apple user would have done the research to figure out how to make apple hardware work perfectly with Ubuntu as the OS.  I've known more than a few expert Linux people who run it on Apple hardware and were very happy, but they'd all learned the little differences to make their systems work very nicely.  Hope that helps explain a little.

**2012 iMac Headphone Quality poor** might be a better title, in the Apple sub-forum. With the current title, busy people/volunteers won't take the time too look deeper at the question(s).  A good title gets the right eyes on the issue when folks are skimming the forums to see if they can help. 

I'm not using 18.04 at this point. Sorry.

Here's hoping someone can help.

---

### Post by icebunny08 on 2018-05-23
Ok. Thank you, TheFu.

---

