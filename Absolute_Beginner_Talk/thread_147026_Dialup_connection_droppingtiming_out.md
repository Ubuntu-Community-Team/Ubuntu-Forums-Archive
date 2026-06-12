---
title: "Dialup connection dropping/timing out?"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Kersus on 2006-03-19
So I have my internet up and going now, but if I don't do anything after a few minutes, it drops.  is there an automatic timeout in Ubuntu I can change?

I'm now using the System/Administration/Networking to connect to the internet.  The same drop is occuring though after awhile if I use wvdial at command line.

In fact while writing this message, the connection dropped and I had to reconnect to post.

---

### Post by navilon on 2006-03-19
You might have a telephone wire shorting out. If possible, try to run a new line to the telephone box outside.

---

### Post by Pragmatist on 2006-03-19
Read this:
[https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dial%29#head-8f5dfcf07a408945df0dcd5a4eed9d5a8d20dacb](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dial%29#head-8f5dfcf07a408945df0dcd5a4eed9d5a8d20dacb)

> If you lose the connection a short time after connecting (30 sec - 3 min), you might need to edit options for pppd:

sudo gedit /etc/ppp/options

Find lcp-echo-interval30 and lcp-echo-failure4. Comment out these options by adding a '#' at the start of these lines, eg. # lcp-echo-interval30 and # lcp-echo-failure4. 

---

