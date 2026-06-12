---
title: "setting up a socks 4/5 server"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Drew32 on 2006-08-30
Hey
Im running Ubuntu server edition and was wondering on how to set up a socks 4/5 server on it.  I cant seem to find any program on the universe or the multiverse and and i cant get any other programs to compile.  anyone have any suggestions on a semi-easy to setup socks server?

---

### Post by PokerNinja on 2007-01-22
The easiest way is to run ssh. 

ssh -D [port] [username@]host

will start a SOCKS v4/v5 server on the current machine, listening on
socket [port] (Lots of folks use 1080) and will direct the requests to
the internet via the connection at "host"

If you don't have another machine, you could do this:

ssh -D 1080 localhost

This will starts the SOCKS4/5 server on your current machine, routing
out to the internet from your current machine.

If you want to make the server more like a daemon, do this:

ssh -NfD 1080 localhost

If you need other machines in your home network to be able to
access the SOCKS port, add the "-g" switch to ssh, like this:

ssh -NfgD 1080 localhost

If the remote machine is going over a slow link (like T1, DSL, dialup, etc)
then you might want to add compression:

ssh -NCfgD 1080 remotehost

---

