---
title: "newbie DVD totem help"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by Mr. Knuffke on 2006-02-14
Hi, 

I'm new to this whole dealy, but I do try to educate myself.  To that end, I installed ubuntu (with no problems at all), and ran automatix.  Really did it up nice.  I had tried to install previous to learning about automatix and so I read the docs and figured out certain things (ie how to cut and paste commands that are largely foreign to me into the terminal to install certain stuff).  I got the system to the point that totem-xine played burned  DVDs, sweet.  Really all I need on this refurbished dell.  

Until tonight, when I tried to play a non-burned DVD in totem and oops.

The message I get is:

The source seems encrypted and can't be read.  Are you trying to play an encrypted DVD without libdvdcss?

No, I'm not.  Automatix installed libdvdcss.  And to double check, when I go into the terminal, I have the most up to date libdvdcss files I could possibly have (something like libdvdcss 3).  so it won't install any new packages.  

In short, what the hell is going on here?  I figure it is probably a relatively easy fix, but I really need someone who knows something to point me in the right direction.  

I have managed to finagle my way into the DVD files on the disk and play selected .vob video files in totem-xine.  No sound and very shaky video (people break down into lines a lot).

Thanks.

David

---

### Post by amisi on 2006-02-14
Hi!

I had a same problem, and I find a solution.
Visit this [link](https://wiki.ubuntu.com/DMA), shows you how to turn on DMA for your DVD player.
 Good Luck!

---

### Post by Mr. Knuffke on 2006-02-15
I really appreciate that attempt at aid, but my DMA is on and is set in hd parm to be on all the time.  I have no problem playing burned DVD's, but for some reason, totem does not believe it has the necessary codecs for css DVD's when I can verify in the terminal that it does.

So very strange.

---

### Post by Mr. Knuffke on 2006-02-15
Murphy's law strikes again.

You see, not only do you have to download the libdvdcss codec, but you must also unzip it.

In my opinion, this is poorly presented on the restricted formats FAQ, the way the command is written on the page only excecutes the first part of the process and it is not particularly clear that you must then execute the second line of the command to unzip the codec.  I guess I would know that if I had more chops, but I don't.

I hope this helps anyone who has a similar issue/provides hours of mirth for the multitudes who know better than I do.

---

