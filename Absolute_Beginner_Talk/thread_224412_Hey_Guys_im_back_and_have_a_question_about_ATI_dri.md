---
title: "Hey Guys im back and have a question about ATI drivers"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2006-07-27
Hi guys im back after heading off and trying knoppix and openususe. Well i have a problem getting my ati drivers to install. I tried a howto and it did not work. The control center installs but the fglrxinfo still says mesa. Any Idea how to get them to work?

---

### Post by jasonpeinko on 2006-07-28
I get this error message several times
```

fglrx] API ERROR: could not register entrypoint for GetRenderbufferParameterivEXT
[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEX

```

---

### Post by Ramses on 2006-07-28
If you have older or same age graphics card than radeon 9250 then try this solution [http://ubuntuforums.org/showthread.php?t=185033](http://ubuntuforums.org/showthread.php?t=185033)

---

### Post by koshari on 2006-07-28
also the "radeon" drivers work well with the 9250, i was getting problems with the fglrx drivers and did the lib.so.so switch and it fixed most of the probs, however i couldnt get direct rendering therefore couldnt get compiz to work, but i followed the ati mobility guide for compiz and it worked a charm :-)

heres the link.
[http://www.ubuntuforums.org/showthread.php?t=219336](http://www.ubuntuforums.org/showthread.php?t=219336)

---

### Post by koshari on 2006-07-28
and with the radeon drivers i get aroung 1000fps on glxgears in a gnome seesion, and about 200fps in xgl.

---

