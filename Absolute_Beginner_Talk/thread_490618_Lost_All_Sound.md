---
title: "Lost All Sound"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by oeolycus on 2007-07-02
I've been using Ubuntu since the 7.04 release.  My sound has worked flawlessly until yesterday.  I'm not sure what happened, how to fix it, or even where to start investigating.  Searching the forums yielded little help, so I turn to your expertise.

I think I lost sound when I locked it (ctrl+alt+L). I came back to an unresponsive blue screen (first occurence). I had to do a hard reboot. Ubuntu loaded spiffy and everything seems to be in order, except no sound. The volume doesn't seem to be muted, at least through the volume control...

I'm unsure how to proceed.

Another post thought it had something to do with /etc/modules (I don't know what this manages, but here are the contents of that file anyway)

```
fuse
lp
sbp2
```

I am on a Compal CL50 laptop, and if it helps, the audio controller is Intel's AC'97.

Thanks in advance,

O.

---

### Post by oeolycus on 2007-07-02
Resolved.

Followed the instructions in [_this thread_]("http://ubuntuforums.org/showthread.php?t=205449").

Ended up that the master volume was unmuted, but PCM was muted.  Fixing this with alsamixer resolved the problem.

---

