---
title: "Cygwin GUI problems"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by blastthisinferno on 2007-07-15
I've looked a lot for an answer to my problem here.  If anyone knows what the problem is or where I could find a solution, please point me in the right direction.  This is what I'm getting for every app that requires X.  

[IMG]http://img.photobucket.com/albums/v288/blastthisinferno/cygwinproblem2.jpg[/IMG]

I ran the startxwin.bat which I believe sets everything up for me on Windows.  I then ssh into my linux machine and try my apps.  I hope that I'm just missing a command or something, but I have no idea.

---

### Post by Tomosaur on 2007-07-15
> **blastthisinferno said:**
> I've looked a lot for an answer to my problem here.  If anyone knows what the problem is or where I could find a solution, please point me in the right direction.  This is what I'm getting for every app that requires X.  

[IMG]http://img.photobucket.com/albums/v288/blastthisinferno/cygwinproblem2.jpg[/IMG]

I ran the startxwin.bat which I believe sets everything up for me on Windows.  I then ssh into my linux machine and try my apps.  I hope that I'm just missing a command or something, but I have no idea.

X forwarding is an option for your SSH client to handle, it doesn't happen automatically. Look at the documentation for your SSH client and see how you can configure it to use X forwarding. If I recall correctly, Cygwin allows you to use X forwarding by simply running SSH using the following syntax:
```

ssh -x user@host

```

If that doesn't work, though, then I think you'll find the answer in the documentation.

---

