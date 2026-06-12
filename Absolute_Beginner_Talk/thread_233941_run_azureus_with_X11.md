---
title: "run azureus with X11?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by roderashe on 2006-08-10
I have dapper server installed and would like to do most of what I want to do remotely. I'd like to set up an azureus client on the box. Can I access it from my mac with X11? Or is there a command line interface to it? Thanks! ](*,)

---

### Post by roderashe on 2006-08-15
bump?

---

### Post by kaamos on 2006-08-15
Install azureus and openssh-server, ssh to the box with X running in the mac and X-forwarding in use and it should work. Note that azureus will close when the connection/X/mac is closed!

A better solution would be use some command line client (like transmission) with gnu screen.
1)
```
sudo aptitude install screen
```
2) Install transmission (there is a howto in the forums)

3) start a torrent with ```
screen transmissioncli somefile.torrent
```

4) Transmission will now be running regardless of the login (so you can log out and back in with ssh). Use "screen -r" to check on your torrent

---

### Post by roderashe on 2006-08-15
thanks, kaamos! I'll give it a try.

---

