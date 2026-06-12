---
title: "VNC slooooooow over SSH"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by DarkKoopa on 2006-09-25
I finally got this working, works great on my home LAN.

Tried it from my workplace and oh my god.... how slow....

When my server box was Server 2003 it was great using Remote Desktop Connection, so it's not a bandwidth or connection from here to home issue.  I can't use VNC directly from my workplace to my home as our firewall will not allow it to be opened, and I don't want to ask as I don't really have a work related reason to get it opened..... :-k 

Is VNC slow, or do I need to do something?

Keep in mind that the CLI generally scares the hell outta me, but I'm willing to use it.  (The reason it scares me is because I'm not knowledgeable about it, and I want to be able to reverse anything I do/stuff up.)

---

### Post by henriquemaia on 2006-09-25
In ssh everything gets encrypted, so it becomes much slower than a direct connection. You get the same results when you share files through an ssh connection.

---

### Post by DarkKoopa on 2006-09-25
> **henriquemaia said:**
> In ssh everything gets encrypted, so it becomes much slower than a direct connection. You get the same results when you share files through an ssh connection.

I positive that it's not SSH (PuTTY) causing this, as I have to use PuTTY when using Microsoft's Remote Desktop Connection to log into another of my work's state servers, and it works perfectly.

Any other suggestions?

---

### Post by MrHorus on 2006-09-25
> **DarkKoopa said:**
> 
Keep in mind that the CLI generally scares the hell outta me, but I'm willing to use it.  (The reason it scares me is because I'm not knowledgeable about it, and I want to be able to reverse anything I do/stuff up.)

Well it's always going to scare you unless you make the jump into the deep and and learn :)

---

### Post by DarkKoopa on 2006-09-25
> **MrHorus said:**
> Well it's always going to scare you unless you make the jump into the deep and and learn :)

I've been doing that lately (like the last hour ;) ), editing my xorg.conf trying to fix my monitor resolution under VNC. 

(And always making sure I make a backup)

Still stuck with this slow connection though ](*,)

---

### Post by lamego on 2006-09-25
SSH (SSL) encryption does slow down your connection regardless if its using VNC or RDP (Windows Remote).
I know the techical details of both protocols but as far I could read VNC does use more data than RDP.

You could try FreeNX:
[https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

---

### Post by DarkKoopa on 2006-09-25
Sorry to sound like the complete n00b that I am, but does this mean that I don't use PuTTy anymore and that the NX client encrypts everything?

It also seems that I had to use an old 1.5 client instead of the version 2 client, as it didn't work at all.

---

### Post by DarkKoopa on 2006-09-25
> **DarkKoopa said:**
> Sorry to sound like the complete n00b that I am, but does this mean that I don't use PuTTy anymore and that the NX client encrypts everything?

It also seems that I had to use an old 1.5 client instead of the version 2 client, as it didn't work at all.

Sorry, I should have said that I installed FreeNX when asking these questions.

---

### Post by skymt on 2006-09-25
The NX client doesn't encrypt anything. The [tutorial](https://help.ubuntu.com/community/FreeNX) lamego linked to sets it up to tunnel through SSH, just like how you have VNC set up.

NX has much better encryption than VNC, so you should see a drastic increase in speed.

---

### Post by DarkKoopa on 2006-09-25
My God FreeNX is much faster.

I have ticked encrypt everything through SSL otherwise it doesn't work.  Is this as secure as SSH? (Or is it the same thing?)

---

### Post by skymt on 2006-09-25
> **DarkKoopa said:**
> My God FreeNX is much faster.

I have ticked encrypt everything through SSL otherwise it doesn't work.  Is this as secure as SSH? (Or is it the same thing?)

It's as secure in a practical sense. That is, both are uncrackable in a reasonable amount of time. There are probably slight differences, but they really don't matter.

---

### Post by DarkKoopa on 2006-09-25
Excellent.

Thanks for the help.

---

