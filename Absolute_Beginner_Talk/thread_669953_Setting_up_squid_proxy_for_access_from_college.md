---
title: "Setting up squid proxy for access from college"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by ckennow on 2008-01-16
I think I am on the right track but tell me if I'm not...

I want to access my server from my schools wireless but they block port 81 and 25 and multiple other ones.  So when I'm sitting in class while the instructor lectures about all the stuff I already know I can maintain my server. (BTW it the beginning of my 2nd semester for my 2 yr. Associates in IT Web Design)

I have come to the conclusion that I need a proxy server setup on my ubuntu box so I had installed squid but I don't believe I have found a walkthroough for my specific needs.  Most are for setting it up for local networked machines and I need it so I can just use my server's IP as a proxy to bypass the schools wireless proxy.

Help Ubuntuwan's, your my only hope.

---

### Post by ckennow on 2008-01-16
can anyone at least offer a link to good tutorial or walkthrough i'd like to get this working tonight before school in the morning.

---

### Post by ftolead on 2008-01-24
I'm working on this configuration now and will post a quick and dirty howto when I'm done.

---

### Post by emarkd on 2008-01-24
You didn't mention port 22.  Can you ssh?  That's how I do it from College :)  You can even use sshfs and mount your remote filesystem.  Makes it very easy...

---

