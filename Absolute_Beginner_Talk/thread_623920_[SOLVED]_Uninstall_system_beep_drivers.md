---
title: "[SOLVED] Uninstall system beep drivers?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2007-11-26
So I wanted to completely disable the system beep. I found a post that said:
        1) sudo gedit /etc/rc.local 
	2) modprobe -r pcspkr (ABOVE the exit 0 line)

Is this what I want? I don't really know what modprobe does. Any help would be appreciated

---

### Post by Dr Small on 2007-11-26
Try it. I love system beeps, so I don't want to do it, but if it doesn't work, just remove the line and try other alternatives. it can't hurt to try.

---

### Post by nickpaton on 2007-11-26
I've Googled modprobe and found the following typically:

[http://linux.about.com/od/commands/l/blcmdl8_modprob.htm]("http://linux.about.com/od/commands/l/blcmdl8_modprob.htm")

And somewhat clearer:

[http://en.wikipedia.org/wiki/Modprobe]("http://en.wikipedia.org/wiki/Modprobe")

Re removing the beep, I also found a similar post [here]("http://ubuntuforums.org/showthread.php?t=618832")

If if doesn't work, make a note of what you did so you can undo it later.

Nick

---

### Post by Sqwishy on 2007-11-26
just run
```
sudo rmmod pcspkr
```
It pretty much does the same thing as modprobe. The instructions you mentioned in your first post would work. The one i just mentioned will also work, although I'm not quite sure it'll work after reboot, I did it once and I think it suck but I'm not sure.

---

### Post by mellowd on 2007-11-26
Cut the wires :)

---

### Post by slughappy1 on 2007-11-27
Uhhhh, no I don't think I'll do that. But thanks :)

---

