---
title: "Start x-server"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-04-02
Hey guys got a terminal log in how do i start the x server?(gnome) Hope its simple enough :D

Saj

---

### Post by Crafty Kisses on 2008-04-02
> **saj0577 said:**
> Hey guys got a terminal log in how do i start the x server?(gnome) Hope its simple enough :D

Saj
I think it's: ```
startx
```

---

### Post by saj0577 on 2008-04-02
Same through putty? 

What about i heard you can start an x-server if you got the files on your client computer when connecting to a server how would you do this?

Saj

Thanks for speedy reply

---

### Post by Dr Small on 2008-04-02
You can't start an Xserver with PuTTY, you will need Xming to do that.

---

### Post by Crafty Kisses on 2008-04-02
> **Dr Small said:**
> You can't start an Xserver with PuTTY, you will need Xming to do that.

Yeah, he didn't originally what he was using. Xming would do the trick though. :)

---

### Post by saj0577 on 2008-04-02
On the server or client?

Saj

---

### Post by Dr Small on 2008-04-02
PuTTY would naturally be run on the client. So would Xming, as it is a portable X11 client for Windows.

---

### Post by saj0577 on 2008-04-02
> **Dr Small said:**
> PuTTY would naturally be run on the client. So would Xming, as it is a portable X11 client for Windows.

Thanks i will give it a go later see if i can get a X server running on my server.

Saj

---

### Post by bodhi.zazen on 2008-04-02
> **saj0577 said:**
> On the server or client?

Saj

You need an X server on the client. If the client is windows you can use cygwin or Xming.

Don't forget to enable X forwarding on putty (it is in the SSH -> X11 menu / config window).

On a linux client you forward X with ssh -X

---

### Post by saj0577 on 2008-04-02
Thanks i will give it ago and once got it working i will reply and mark as solved.


thanks
Saj

---

### Post by Rocket2DMn on 2008-04-02
> **bodhi.zazen said:**
> You need an X server on the client. If the client is windows you can use cygwin or Xming.

Don't forget to enable X forwarding on putty (it is in the SSH -> X11 menu / config window).

On a linux client you forward X with ssh -X

+1 for the ssh -X, that's very important to use when you do the SSH connection, or you will get an error when you try to open a GUI program.
```
ssh -X ip[:port] -l username
or
ssh -X username@ip[:port]
```

---

### Post by saj0577 on 2008-04-02
So it will use the client to run X what about any programs liek for example system monitor. Will i need to install that on the server but just use the clients X to access it?

Saj

---

### Post by Rocket2DMn on 2008-04-02
AFAIK, any programs you use have to be installed on the server, and they are tunneled to the client.  That is my experience using X-windows on remote UNIX systems, anyway.
Differerent setups may work differently though.

---

### Post by saj0577 on 2008-04-02
Okay i thought that would be the case. Thanks

Saj

---

