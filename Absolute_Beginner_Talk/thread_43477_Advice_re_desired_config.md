---
title: "Advice re desired config"
date: 2005-06-22
forum: Absolute Beginner Talk
---

### Post by SWo2005 on 2005-06-22
Hi

My first post ...

Finally got my first ubuntu install working ... and now I know what I want to do with it but don't really know where to start so am looking for pointers 

(It just connected to the web -- no tweaking ... nothing --- amazing !! so you can tell I've been brought up on Windows)

1) I want my ubuntu box  simply to act as a proxy and junkbuster for my home lan. I was doing this on an Win2k machine with SQUID+Privoxy and it worked well but now I want to get this going on my linux machine.

2) I'm short of office space and so my ubuntu box  will be screen-less and keyboard/mouse-less. Each morning I want to just switch on my ubuntu box and then to be able to control it from my Win2K machine. I've had VNC running fine and I can control my linux box from it **BUT** I need to login. How can I get round that. Can I get a remote console? Are there other ways of achieving this?

Many thanks

Simon

---

### Post by tonym on 2005-06-24
squid should be easy enough.  Install the package first then lok at the config file.  The only change I had to make was to add an acl for my local network and give access to it.  This is easy enough as the config file is well commented.  I don't know anything about privoxy.

I have a headless box in a similar manner.  I mainly use ssh to access it - install ssh server on the Ubuntu box if its not there already and something like putty for an ssh client on Windows.  However,  because of a number of past hardware problems that required me to rebuild the box a number of times I've also got a 2-way KVM switch.

---

