---
title: "remote desktop sharing with freenx?"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by melchior on 2006-03-06
Freenx is great! it's fast, sessions stay open. it's sweet. VNC is uselessly slow, remotely.

It doesn't seem to do the one thing I want it to though... *sigh* I want to share the active session on the system. I don't want to create a display:1 I want to move the mouse remotely and the user on the other system sees the mouse move. 

So, I don't want to open a new remote session. I want to observe and control the current session. 


Vnc can do this. Freenx cannot. 


The only way I have found to get around this is by running a VNC session inside the freenx session, which is stupid. Having two concurrent sessions and vncing into the local session. 


Not only is it still slow, though not as bad as plain vnc, but the vnc session seeems to time out or something. It is still not really functional.

I am asking three questions:

Can I use freenx to *share* the current desktop session and have it appear on the local desktop?

Is there a way to make VNC behave better within my freenx session?

Is there a better method to access the other desktop session other than vnc? Try as I might, for example, i couldn't find a way to switch into the original display of the xserver... Any help would be appreciated, and note, I am stupid so a howto would be lovely. 

Thanks for any help or suggestions folks can give. This pc is running the dapper dev release and it is connected to the tv, which is why i need this functionality. thanks.:rolleyes:

---

### Post by melchior on 2006-03-07
Well, ok....  I've read people talk about using freenx as a proxy to tunnel a vnc connection.... how do I do that? It's not mentioned in any howto i can find.... I am using the mac client.... Any help would be appreciated!

---

### Post by berahmed on 2008-02-27
Hi melchior,
I am facing the same problem and I would like to know if you found a solution to your problem ?

Cheers

---

