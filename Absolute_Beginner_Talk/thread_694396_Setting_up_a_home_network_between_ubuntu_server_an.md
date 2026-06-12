---
title: "Setting up a home network between ubuntu server and a windows laptop using putty"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by James27 on 2008-02-12
maybe you guys can lead me in the right direction, or even help me understand if what i want to do is possible
i have a linux box running the latest version of ubuntu server, as well as a couple windows machines (specifically my laptop) that are using putty to ssh into my box. i have my IP and everything set up now, and i have all my files set up as i want them. this leads me to my question. When i get this all smoothed out, how can i transfer pics, .odt files, music etc between my laptop running putty and my linux box when sshing. in other words, if i forget my report at home (and im at school) and i hop on my laptop, how can i (using putty) get the file off onto my windows machine?
thanks in advanced for your help and i look forward to being a better member of the community (as opposed the occasional lurker that i already am). home this is in the right place, if not i apologize. thanks
james

---

### Post by emarkd on 2008-02-12
I don't use putty much, but does it have sftp?  or scp?  That would be the answer to your problem.

A more useful solution may be to skip putty for cygwin.  Check it out if you haven't

---

### Post by KCPokes on 2008-02-12
Look into WinSCP (winscp.net).  It is a great Windows GUI for SCP, which will allow you a FTP-like interface to access your files.  It even has FTP fallback, now, so you can use it as your preferred FTP client, if you so choose.  It is all I've used for years.

---

### Post by James27 on 2008-02-12
Awsome, thanks for the help guys, im going to check out all the options you gave me. 
thanks again, james

---

### Post by hyper_ch on 2008-02-12
just install openssh-server and then use WinSCP --> very simple :)

But if it's a homenetwork, why using SSH? Why not simply setting up samba?

---

