---
title: "How do I get the linux-headers I need?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by soaked on 2007-03-28
Complete noob here, first post.

I am trying to install VMWare v1.0.2 on a new ubuntu server install v6.06, which VMWare list as supported.

During VMWare install it asks for the location of the C headers

If I use 'uname -r' it returns 2.6.15-26-server

So if I use:

'apt-get install linux-headers-2.6.15-26-server'

I get an error that the package could not be found

If I use:

'apt-get install linux-headers'

I get a list of headers for 2.6.15.23

How do I resolve this please? Where can I find the headers I need? Or do I need to use the 2.6.15-23 kernel? If so, how do I downgrade please?

---

### Post by Bachstelze on 2007-03-28
*linux-headers-2.6.15-26-server* definitely *is* in the repos. Make you have them enabled, not only the CD. Also, if I were you, I'd upgrade my kernel to the latest (2.6.15-28 for Dapper).

---

### Post by soaked on 2007-03-28
Thank you for such a quick reply. :)

I have edited the file which says where apt can look for things, but I still get an error (and for 2.6.15-28-server too).

I think that perhaps I need to force apt to look in repositories for updates, but don't know how. Time to RTFM I guess.

---

### Post by Bachstelze on 2007-03-28
Could you pastebin your sources.list ?

---

### Post by soaked on 2007-03-28
Will do if I need to. It's the standard one with all the commented out sources removed so they are reachable. Main repositories ar gb.ubuntu.com

I finally got a connection from aptitude to security.ubuntu.com and have been offered some new things to update. Will post again if I still have a problem after this update. Thanks for your help so far.

**Edit:** Yes the headers are at security.ubuntu.com which is often not responding very quickly. Is there another repository I can use?

---

