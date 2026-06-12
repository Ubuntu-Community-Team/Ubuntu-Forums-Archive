---
title: "DVD play trouble in Totem, mplayer, xine"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by tparker on 2006-10-22
I have tried everything I found searching to get DVD's to play and still can't get it so I am asking for help. I am very new to Ubuntu and have very little linux experience, I will give whatever info I'm guessing might be helpful.

I am using Ubuntu 6.06 (amd64) and have run all the updates the desktop told me about. I have added all the repositories through Synaptic and checked to be sure they were there. I have made sure that my dvd drive is correctly labeled and mounted. My sound works fine (can play mp3s in xmms) and video driver (nvidia) is updated and works fine (can play WOW in wine).

First I followed the directions at [https://help.ubuntu.com/ubuntu/desktopguide/C/codecs.htm](https://help.ubuntu.com/ubuntu/desktopguide/C/codecs.htm)

When DVD playing still didn't work I followed the directions at
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and everything worked except for installing gstreamer0.10-pitfdll, for this I got the error: E: Couldn't find package gstreamer0.10-pitfdll.

I tried searching for it in synaptic to install and couldn't find it.

When I try to play a DVD with Totem (the default one that came with Ubuntu) I get the message: Totem cannot play this type of media (DVD) because you do not have the appropriate plug ins to handle it.

I downloaded and installed mplayer-amd64 through synaptic and it doesn't do anything - can't seem to find the dvd at all.

I downloaded and installed xine through synaptic and it finds the DVD, starts to play it, then stops playing right after the FBI warnings and goes back the looking just like it does when you first start it up, before hitting play or anything.

So I know Ubuntu can find and play the DVD because it starts to in xine, but I can't figure out why it stops or why the other players don't work.

Any ideas?

---

### Post by gn2 on 2006-10-22
Re-install with 32-bit Ubuntu would be my advice.

---

