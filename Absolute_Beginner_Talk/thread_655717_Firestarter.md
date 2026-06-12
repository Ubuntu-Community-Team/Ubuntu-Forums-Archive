---
title: "Firestarter"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2008-01-01
I added it to launched programs on startup and it now says:
Only root has privileges to run firestarter!

```
simeon@simeon-laptop:~$ ls -l /usr/sbin/firestarter
-rwxr-xr-x 1 root root 457880 2007-08-31 20:59 /usr/sbin/firestarter
simeon@simeon-laptop:~$ 

```

that's the output. Should be alright to launch it. I have to do so manually now and it doesn't say anything.

---

### Post by bump_ on 2008-01-01
I don't use it, but isn't firestarter just a GUI to change the iptable rules? If so, it should not be necessary to run firestarter at startup. Once you make the changes, they should last even when you shut Firestarter down

---

### Post by llamakc on 2008-01-01
> **bump_ said:**
> I don't use it, but isn't firestarter just a GUI to change the iptable rules? If so, it should not be necessary to run firestarter at startup. Once you make the changes, they should last even when you shut Firestarter down

Yes. There's no reason to run it at startup.

---

### Post by Giradman on 2008-01-01
> **bump_ said:**
> I don't use it, but isn't firestarter just a GUI to change the iptable rules? If so, it should not be necessary to run firestarter at startup. Once you make the changes, they should last even when you shut Firestarter down

Agree - *Firestarter* is a GUI as indicated that allows you to regulate 'inbound' & 'outbound' traffic of the firewall that is already built into Ubuntu and functioning - not really needed to run in 'real time' on just a personal computer - check out the [documentation here]("http://www.fs-security.com/docs.php") - I have the program installed, have read the linked doc, and decided not to make any changes; nor do I have it running in the background.  As a test, I left the program running & then shut it down - checked 'Shields Up' on Steve Gibson's site (grc.com) both ways - absolutely the same results on my Ubuntu computer - completely closed & stealthed - :)

---

