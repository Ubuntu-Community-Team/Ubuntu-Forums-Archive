---
title: "Synaptic Package Manager/openssh question"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by crimsonguard on 2007-04-28
Hello Ubuntu world!

This is my first post on this forum so please be understanding...

I've just installed Ubuntu 7.04 (Feisty Fawn) on a test computer to play around with it and see what it can do. I have very little Linux experience, but I would rate myself as an otherwise competent computer user.

Currently I'm trying to get my head round something - I want to use an SSH terminal client to log on to my webserver. Using the 'Places/Connect to Server' option gives me a GUI folder explorer which is handy but not what I want.

I've looked in Synaptic and I can see that OpenSSH client is already installed. However when I go to 'Applications/Internet' I can't see a link to it there. Searching for 'openssh-client' on my machine lists a variety of files, including some shell scripts, but nothing there looks like an 'executable' that I could run to start the program.

Could someone tell me how to link these installed apps either to my desktop or the application menu? Failing that can anyone recommend a good SSH client that I could use?

Thanks in advance for the help!

---

### Post by az on 2007-04-28
You run it through a terminal.

Open up a terminal and run

ssh user@192.168.0.100

and you will log into 192.168.0.100 as the user named "user".

---

### Post by crimsonguard on 2007-04-28
Ah, OK I'll give that a go.

Thanks!

---

