---
title: "Viewing and controlling my server's screen."
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-08-13
I need to have control of the server's command prompt over the network, not SSH because if I log out of SSH... my processes stop. It is sort of pointless having a dedicated box if I can't turn my desktop off or close the SSH terminal window.

---

### Post by steveneddy on 2007-08-13
xvncviewer - it's in Synaptic - install it

In terminal

```
xvncviewer server.ip.address:1
```

Go nuts - start - stop - close the window - server keeps on ticking

I set my server to stream music all day and night, among other things. I login via VNC locally or remotely and do whatever it is that I need to do, then just close the window without logging out. 

Works perfectly.

---

### Post by kavon89 on 2007-08-13
Sounds great!  Synaptic says it is already installed. When I try it on my server it says connection refused.

I have a feeling I need to do something on the server first... what would that be? :D

---

### Post by steveneddy on 2007-08-13
Um - try vncserver. On the server, that is.

You know - this is on the forums already. all you have to do is search.

You know how to search the forums, right? I'm just trying to help.

When I have a problem, I search first, read a lot, THEN post as a last resort. 

I mean, you can do whatever you want. But I'm sure that every question that you have has already been answered somewhere.

Don't write that I'm being mean or cruel, I'm just trying to point out the fact that searching cuts down on LOTS of posting. Not that posting is bad. 

Don't forget that after you install vncserver that you have to tell the computer to let another control it.

Good luck.

---

### Post by Wim Sturkenboom on 2007-08-14
You can have a look at the *screen* command.

---

### Post by DeHorde on 2007-08-14
No really, go with Wim's advice. Check out "screen".  It does exactly what you need it to do.  And it doesn't take the overhead and added layers of VNC.

 I find almost everything I run into as an "I would like it if", is an itch someone else already scratched...

---

### Post by kavon89 on 2007-08-14
I would love to try "screen" and I've googled about it. I just don't understand how to use it. Vncviewer asks for my password, but then it says connection refused. I opened port 5900, which is what I thought was default?

Obviously I can't search "screen command" in the forum. I would really like to get one or the other working today. Help please! :)

---

