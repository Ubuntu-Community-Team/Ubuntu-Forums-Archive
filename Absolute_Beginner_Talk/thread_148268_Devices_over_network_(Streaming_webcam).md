---
title: "Devices over network? (Streaming webcam)"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Kurt` on 2006-03-21
Hi,

I would like to be able to attach a webcam to one of my other Ubuntu boxen, and stream it into a player on this comp (preferably xawtv).

What I did was mount /dev on the computer with the webcam to /stuff locally. Then I tried to invoke xawtv as follows:

xawtv -c /stuff/video0

But it gave out some errors saying /stuff/video0 is not a 'device node'.

Is there a proper way to access a device across a network?

Also, when using ls -al, what does "c" mean? e.g. 'crwxrwxrwx'. I know d = dir and l = symlink, but c is a mystery to me. :)

---

