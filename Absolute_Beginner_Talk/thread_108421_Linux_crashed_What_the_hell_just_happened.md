---
title: "Linux crashed? What the hell just happened?"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by qiemem on 2005-12-26
Ok, so, this is really weird. I was trying to copy songs to iPod via YamiPod when it errors. I try to close it and nothing happens. I try to force quit it, nothing happens. Eventually it closes (don't know why), but then I realize there is something seriously wrong. I can open programs from launchers and such things, but no menus will open (they just highlight, don't open) and nothing actually does anything. Worried, I hit ctrl+alt+backspace and nothing happens. Uh, do it again and again and again. Nothing... I try ctrl+alt+f1-f6. Nothing. So I tap the power bottom to see if I can force a shutdown (not like cut power, but you know, signal a shut down; I didn't even know if this would work normally). Anyway, eventually I get to the console login screen, but I can't type anything. So I tap random keys to see if I can get it to work and after a long delay, all that comes up is "sad" (friggin weird, eh?). Anyway, it won't do anything else, so I tap the power button and it eventually shuts down. I turn it on again, and now everything seems to be fine. Any ideas? Even if no one does, I just thought it was a pretty weird crash that should've been shared anyway. Oh, I've never had linux itself stop functioning before, nothing a ctrl+alt+bckspc couldn't fix anyway.

Oh ya I almost forgot. So while this was happening, I was still able to open programs. So I opened firefox, went to this site (via bookmark, so I guess some stuff was working). But when I tried to post, I couldn't type anything. So ya... there it is... anyone have any idea what the hell was going on?

---

### Post by stuporglue on 2005-12-26
Did you apply some updates and then not reboot for a long time? I had the same problem once last week after applying some Dapper updates, but before I rebooted. Once I rebooted, everything went back to normal and I haven't seen anything since. 

I agree it's weird though. :-)

---

### Post by etc on 2005-12-26
Sounds like a [kernel panic]("http://en.wikipedia.org/wiki/Kernel_panic"), but I could be wrong.

---

### Post by stuporglue on 2005-12-26
Assuming qiemem had the same problem I had, I don't think it was a kernel panic. The kernel panics I've had (when I built my own kernels) usually froze the machine and nothing worked. With the crash I had last week, and the one qiemem had, some programs would continue to work to some extent.

---

### Post by etc on 2005-12-26
Woops, I just reread it and he said stuff still worked, so you're right.

---

### Post by qiemem on 2005-12-26
ya, that could've quite possibly been it stuporglue, I think I had recently installed a bunch of stuff... weird though. Glad to hear it actaully happened to someone else, er, you know what I mean. Oh, for future reference, how should I restart my computer? I mean, when ctrl+alt+bckspc fails, what should I use?

---

### Post by Gowator on 2005-12-26
Then why not just restart Xorg from another machine or at least try and login from the other machine?
I guess the updates could have been the reason ... but its usually possible to at least get to the consoles.  If you have something sucking CPU though then often the consoles take a while to appear and you have to be real patient since tapping the next one just moves it on.,..  I recommend a cup of ubuntu to take your mind of the wait :D

---

