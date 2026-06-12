---
title: "Xchat file transfer : ("
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by giddy1945 on 2007-09-25
I cannot send or receive files.  I am using a community "free wifi".  My Mac lap top airport is picking up the signal, and the signal is then transfered to my linux desktop via ethernet cable.  This is the code I receive when I attempt to send a file to someone:

ZMR> --- Received a malformed DCC request from nameman.
<ZMR> --- Contents of packet: DCC SEND Bruce_Lee_Biography.jpg  29530 232

Maybe it's an Xchat configure problem.
Maybe it's a network problem.
Could be a user problem....wouldn't doubt that.

Thanks for the help.

---

### Post by darc on 2007-09-26
That DCC request doesn't look right... it should be : 

DCC SEND <file> <IP>  <port> <filesize>

I think.  

Might also try it on your mac and see if it works there.  If it doesn't work there either, and it's not the DCC command, it may be network funkyness by your wifi provider, but that's fairly unlikely.

-darc

---

### Post by giddy1945 on 2007-09-26
I didn't actually command line it.  I drug the file to the dialogue window and dropped it.  That is the message I get.  I'm going to check for available ports that may be closed, and see if that works.

---

### Post by giddy1945 on 2007-09-26
[Solved]  I went into my Mac and enabled the IRC port.  Silly me.

---

### Post by giddy1945 on 2007-09-27
I cannot figure out how to send files.  I can accept, but can't send.

---

