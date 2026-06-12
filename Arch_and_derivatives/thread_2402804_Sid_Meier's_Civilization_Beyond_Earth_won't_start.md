---
title: "Sid Meier's Civilization Beyond Earth won't start"
date: 2018-10-04
forum: Arch and derivatives
---

### Post by i7Fd-2sCB1 on 2018-10-04
I haven't been able to find any post relating to this but was wondering if anyone knew of a fix. Basically I play on steam-native and the Civilization Beyond Earth game works without issue but with steam-runtime it refuses to work nor load. At the moment I'm using Ubuntu but would like some assistance with this on Arch. I really don't know why Beyond Earth works with steam-native but not Arch's steam-runtime client with runtime enabled. Is there a reason for this? I've already contacted Aspyr but they haven't yet responded and I did it yesterday. Could anyone with Arch who has the game get it to work with steam-runtime if possible all it states is "-running" and then dumps and I have tried the Arch Wiki with steam's troubleshooting game guide but they don't work.

---

### Post by sdjf on 2018-10-07
I do not have access to the game, but can suggest some troubleshooting. You could try debugging this yourself.  Have you tried starting it on command line?  If $DISPLAY is set to the DISPLAY you are running it in otherwise, there may be some helpful information when you start or run it.

The other more complete way to debug GUI apps is to start on command line using strace, which traces system calls and may show you where it fails, especially if it will not start or crashes.  And it is easy to install with pacman if it is not already on your system.  Output can be voluminous but often will turn up a missing library or whatever, and you can have it save the output in a file to make it easier to study later.

---

