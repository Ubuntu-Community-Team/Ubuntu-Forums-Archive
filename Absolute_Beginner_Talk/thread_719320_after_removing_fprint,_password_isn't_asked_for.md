---
title: "after removing fprint, password isn't asked for???"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by chrish9899 on 2008-03-09
I'm pretty new to Ubuntu, about a month or so... I have a fingerprint reader, so I thought I'd install fprint to use it, I found instructions from thinkwiki.org which directed me to:

[http://www.madman2k.net/comments/105](http://www.madman2k.net/comments/105)

It installed fine, but it couldn't find the fingerprint reader hardware, everything worked OK when  logging in & using sudo in the terminal it just said no suitable fingerpints found and let me type in my password, but I like to run a tight ship and I heard they can be more trouble than they are worth so I decided to remove it.   I used snaptics package manager and completely remove the libpam-fprint + libfprint + fprint-demo Packages. restarted, loggedin (didn't mention fingerprints!) but now whenever the password box would normally pop up (adding or removing progams, etc...) nothing. it just fails to come up and the selected task/app launch doesn't work. in the terminal this kind of thing happens: 

lenny@lenny:~$ sudo nautilus
Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts
lenny@lenny:~$ 

I did change my password awhile ago, don't know it that matters. I was thinking of just trying Hardy but it's not even a beta yet. so I hope I can fix this WITHOUT having to reinstall... ouch just the word hurts my head. as always any and all help is much appreciated. :)

---

### Post by chrish9899 on 2008-03-09
help anyone?

---

