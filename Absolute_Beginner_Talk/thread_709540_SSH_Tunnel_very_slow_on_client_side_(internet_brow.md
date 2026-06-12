---
title: "SSH Tunnel very slow on client side (internet browsing)"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by lilcalis on 2008-02-27
Hello everyon

I am very new with linux and Ubuntu, so bear with me if I am missing something obvious.

I have Ubuntu 7.1 running on my home computer via microsoft virtual  machine. I read up and installed SSH on it, and have left it running.

At work, I connect to the ssh server via Putty. I then configured firefox to properly use the tunnel. Everything connects fine, but then I start encountering this problem...

It's so very very slow ! When I was setting this up last night, I was using the same client work computer ( laptop) that was connected to someone elses wireless network to test it. When surfing, everything was fine, seemed to go at the same speed. When I got to work to test it, it seems to lag quite a bit, and I'm not sure why. I searched the forum for this, and only seemed to find topics with people encountering slowness transfering files.

Are there any settings or configurations I need to change to make this faster ? Everything is set at default for the moment.

---

### Post by wormser on 2008-02-27
It sounds like the internet connection is slower at your work.  Traffic there could be causing it.  Are you using the switch -D 9999?  I have not tried this but there is another switch for compression (-C).  Try this command:

```
ssh -C -D 9999 user@domain
```

Post your results because I am interested if this works.

---

### Post by lilcalis on 2008-02-27
See, heres the thing tho. The internet at work does work without the SSH tunnel, I am only using it cause they block stupid things like hotmail and gmail.

If I have firefox open and browsing ... lets say CNN, i can bring up the same page in IE ( which isnt set to tunnel/proxy) and it comes in quite fast.

Also, sometimes the connection seems to be only intermittently doing this ( will be fine for 10 seconds, then lag for 30 while it loads a different page).

With that command you suggested, I do that on the client or the server computer ? If the client, do i just input that in Putty as if its a terminal window in Ubuntu ( sorry if thats a stupid question)

---

### Post by wormser on 2008-02-27
> **lilcalis said:**
> See, heres the thing tho. The internet at work does work without the SSH tunnel, I am only using it cause they block stupid things like hotmail and gmail.

If I have firefox open and browsing ... lets say CNN, i can bring up the same page in IE ( which isnt set to tunnel/proxy) and it comes in quite fast.

Also, sometimes the connection seems to be only intermittently doing this ( will be fine for 10 seconds, then lag for 30 while it loads a different page).

You should try it on different connections.  It sounds like it has something to do with your work's network.  They might have a bandwidth limit on ssh ports.    

> **lilcalis said:**
> 
With that command you suggested, I do that on the client or the server computer ? If the client, do i just input that in Putty as if its a terminal window in Ubuntu ( sorry if thats a stupid question)

Sorry, I am not that familur with putty.  If you are using the -D switch, the -C should go in the same place.

---

### Post by lilcalis on 2008-02-27
I switched to using IE7 and seems to  be much much faster

---

