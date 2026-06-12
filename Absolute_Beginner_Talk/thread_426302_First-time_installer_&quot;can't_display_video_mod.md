---
title: "First-time installer: &quot;can't display video mode&quot;"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Chriscic on 2007-04-28
Hello,
Wanting to try out the Linux world for the first time.

I am booting from the Ubuntu 7.04 install disk.  Boots fine, and I select "start or install Ubuntu"

Then get the Ubuntu logo screen with the little back and forth cyclon eye so I know its loading.

Then after a few minutes I get what looks like the completion bar which moves to full.

My monitor (Dell 24") then goes black an then says "can't display video mode."

I have a very old Radeon card in there (well before X-series... think its actually the original Radeon).

Seems like Ubuntu is sending a signal my monitor can't handle, although I have no idea what kind of signal that would be since my monitor is modern.

I also tried installing in "safe mode" to no avail... same issue.

Any suggestions?  I have another video card I could try but hoping for a quick fix first as I don't want to be switching cards around all the time when I go back and forth to Windows.

Thanks!

-Chris C.

P.S. PC has a 1.2ghz Celeron processor.
I did check the integrity of the CD.. no problem there

---

### Post by PartisanEntity on 2007-04-28
You could try the alternate CD. I had similar issues with Edgy and an Acer laptop, I tried the alternate CD and that worked.

---

### Post by fwojciec on 2007-04-28
Try pressing Alt-Ctrl-Backspace (it'll restart X server) when you get the error (try it both in regular and save video modes).  This is the only way I can install Ubuntu on my computer (safe mode + Alt-Ctrl-Backspace).  Get ready for some video card configuration once Ubuntu is installed.

Alternate CD is another option.

---

### Post by Chriscic on 2007-04-28
Hey, some tentative success.

First I tried replacing the really old  ATI Radeon card with the less old ATI 8500 All-In-Wonder card I had laying around.

No joy; same problem.

Also tried the Alt-Ctrl-Backspace suggestion, but that just got me no signal at all to the monitor.

Then rebooted in safe graphics mode, and got to the desktop.  So I am running Ubuntu now : )  At least from the CD.

Sadly, my Linksys WMP54GX4 wireless card is unsupported.  I'm not surprised since they must not have sold a lot of them; the SRX400 series was more of a transitional product line between plain ol' G and N.  It does work great though, even for streaming hi-def video files to my HTPC. 

I guess Ubuntu is not quite for me yet, although I'll continue to play around even if it can't be the main OS for my server PC.  I am planning on moving soon and getting the new place wired with Cat5 and maybe then I'll return to Ubuntu.

Thanks for the help,
-Chris

---

### Post by Nythain on 2007-04-28
yeah, continue to play around, read forums, ask questions, find answers, since its not your main os yet, hell nuke it a few times, by the time you're done, when/if you do decide on giving it another go, you will be much more comfortable, and probably wont ecounter near as many problems (since you will have already encountered them) :)

---

### Post by sisseck on 2007-04-28
when boot menu appears, try pressing F4 and change to 640x480x16 then select to boot in graphics safe mode. Worked for me.

---

### Post by UbuntuniX on 2007-04-28
I get this when using a Dell monitor, but after about ten seconds it disappears and everything is fine.

This problem is your monitor, not video card.

---

