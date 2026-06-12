---
title: "Imac G3 very very slow after installing 5.10 or 6.06"
date: 2006-12-18
forum: Apple PPC Users
---

### Post by lfmiller on 2006-12-18
I have an interesting problem - and hoping that someone will have an answer for it.

I have a Imac G3 - 500mhz/384mb ram/10gb hard drive That I have installed ubuntu 5.10 on it runs very very very slow, like you click on something and walk away for 20 mins and it might come up when you come back.  I thought maybe it was something in 5.10 so I tried 6.06 still very slow. SO I thought, well, if going up doesn't fix the problem maybe going backwards would - So I installed the out of date version 5.04 runs very quick very fast, click and go -- I thought maybe there was something wrong with my install CDs so I did a system upgrade to 5.10 and right back to being so slow --- 

I thought that maybe it was the memory so I replaced it, with the same results, I thought maybe the hard-drive was too slow or something so I replaced it with a faster one. 5.10 and 6.06 are still very slow. 

Now here is the weird part of the whole thing - I have an Imac 400mhz with only 128mb ram (still 10gb hard drive) with 6.06 installed and it is quick and stable.  I don't know what is going on with the 500mhz machine, I don't understand why 5.04 runs great on it, but nothing else.

Someone suggested to me that it might be the kernal - but I wouldn't think so, because I used the same CD to installed 6.06 on both machines (same CD means same kernal right?) 

I am at a loss, and am very confused about this - Oh and just for the info of everyone, I am using a G3 450mhz Blue and White machine now with 6.10 installed on it, and it only has 256mb ram and a 20gb drive. It is very quick.

Could it be something in the processor? Are there big changes from a 400/450mhz G3 to a 500mhz G3?

Well, Thanks for the info in advance, I look forward to someone who might have an answer for me!

LeRoy

---

### Post by linear on 2006-12-18
The solution is really very simple - you need to edit xorg.conf and disable **dri**. Easiest if you give up on the gui temporarily and drop to a shell prompt:

1. **ctrl-opt-F1**
2. **sudo nano /etc/X11/xorg.conf**
3. Put a # (hash mark) in front of the line that reads "load dri"
4. **ctrl-O** to save, **crtl-X** to exit
5. restart Gnome: **sudo killall -HUP gdm**

---

### Post by lfmiller on 2006-12-18
> **linear said:**
> The solution is really very simple - you need to edit xorg.conf and disable **dri**. Easiest if you give up on the gui temporarily and drop to a shell prompt:

1. **ctrl-opt-F1**
2. **sudo nano /etc/X11/xorg.conf**
3. Put a # (hash mark) in front of the line that reads "load dri"
4. **ctrl-O** to save, **crtl-X** to exit
5. restart Gnome: **sudo killall -HUP gdm**


And It worked too -- Great! I am very thankful for that. But I would like to learn something, so if you don't mind.
 Could you please explain what I just did?  I understand the ctrl-opt-f1 will get me to the command prompt, not a problem there. I understand nano is an editor, not a problem there. I even understand the use of the # -- 

but what is "DRI" what does it do? Why would it be loaded if it makes the system slow.


I understand the save command and the exit command in the editor,

I know what sudo killall -HUP gdm does, because I just saw it do it... but I'd like to know what the -HUP stands for.

I am happy that it worked, I can pass along the info if needed! 

OH BTW: I am currently using the 500mhz G3, something that I wouldn't/couldn't do before so it worked!

Thanks, 
LeRoy

---

### Post by linear on 2006-12-18
DRI stands for direct rendering infrastructure. You can read about it [here]("http://dri.freedesktop.org/wiki/"). On most machines it works and is a Good Thing, but since Ubuntu 5.10 it has not worked properly for iMac G3's.

"-HUP" basically tells the process to restart after being killed.

---

### Post by lfmiller on 2006-12-19
> **linear said:**
> DRI stands for direct rendering infrastructure. You can read about it [here]("http://dri.freedesktop.org/wiki/"). On most machines it works and is a Good Thing, but since Ubuntu 5.10 it has not worked properly for iMac G3's.

"-HUP" basically tells the process to restart after being killed.

Ok, I understand -- I was wondering if it wasn't the video card that was slowing things down -- 
but since it's on board, I wasn't too sure how to test that out -- till now that is!

Is it a problem with only some Imac G3s?  Like I said I have 6.06 installed on a 400mhz G3 Imac and it works great -- and I have it installed on a 450 G3 blue and white with out problems -- it wasn't till I got this 500mhz Imac that I was having problems....so it must be with only some models or video cards?

LeRoy

---

### Post by lfmiller on 2006-12-20
> **linear said:**
> DRI stands for direct rendering infrastructure. You can read about it [here]("http://dri.freedesktop.org/wiki/"). On most machines it works and is a Good Thing, but since Ubuntu 5.10 it has not worked properly for iMac G3's.

"-HUP" basically tells the process to restart after being killed.

Ok, I understand -- I was wondering if it wasn't the video card that was slowing things down -- 
but since it's on board, I wasn't too sure how to test that out -- till now that is!

Is it a problem with only some Imac G3s?  Like I said I have 6.06 installed on a 400mhz G3 Imac and it works great -- and I have it installed on a 450 G3 blue and white with out problems -- it wasn't till I got this 500mhz Imac that I was having problems....so it must be with only some models or video cards?

LeRoy

---

### Post by linear on 2006-12-20
> **lfmiller said:**
> so it must be with only some models or video cards?

Yes, without a doubt.

---

