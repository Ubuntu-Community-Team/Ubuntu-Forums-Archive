---
title: "And I thought ATI drivers were a pain..."
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Tr0janV0dka on 2007-08-09
So, I got my brand new PC, and it works a treat, at least in Vista, apart from a few games which is starting to **** me off. Runtime errors ftl.

I decided to give Kubuntu 7.04 64bit a 3rd try. I'm using a 8800GTX.

I tried to install the NVIDIA display drivers (x64). The problem isn't getting to the install, it's just an issue installing the drivers, where it says "X-Server must be shut down".

So I go "ok, fair enough. This shouldn't be too hard? Should it? ATI drivers were impossible, literally and everybody says installing NVIDIA drivers is piece of ****!" Think AGAIN!

I have tried the following:

kdm stop (results in screen no longer receiving signal and going into sleep mode - tried on 2 seperate monitors, both show similar symptoms).

Alt+Ctrl+F1 (get's me into console mode/text mode/whatever - still complains about X-Server)

init 3 (does NOTHING)

init 1 (same as kdm stop - may have done something else, but if it did work, I don't think I would be here)

init 0 (shuts down PC)

Alt-Ctrl+Backspace (logs me out of Kubuntu - have to log back in again, this command is essentially useless)

So, anybody have any ideas? Tricks? Different distro of Linux altogether?
If somebody can fix this, they deserve a bloody medal. Strewth, give em a trunk of medals.

---

### Post by splintercellguy on 2007-08-09
sudo dpkg-reconfigure xserver-xorg? And have you tried using Envy to install the drivers?

---

### Post by Tr0janV0dka on 2007-08-09
> **splintercellguy said:**
> sudo dpkg-reconfigure xserver-xorg? And have you tried using Envy to install the drivers?

I've tried the sudo dpkg-reconfigure xserver-xorg and it wasn't really that useful... it tended to skip things when I wanted to change them (resolution for example).

As for this Envy thing... I only read it on one forum while trying to fix this problem. I'll look into what this Envy thing is.

---

### Post by splintercellguy on 2007-08-09
What do you mean skip? At a certain point in the reconfig when you're asked to select resolutions, just use spacebar to select what reses you want. Envy can be found here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by vexorian on 2007-08-09
I just used the restricted manager to install the nvidia drivers, I am not sure what method you used to install it. I do not really get what "issue" means here, does it freeze saying that you must restart X? 

And do ctrl+alt+F1 then do sudo reboot and see if all works

---

### Post by Tr0janV0dka on 2007-08-09
Also, I'm forced to use a VGA display cable (with a DVI to VGA dongle) when using Kubuntu. Kubuntu doesn't seem to like DVI-D cables at all (indicated by the blank screen on booting into Kubuntu).

---

### Post by splintercellguy on 2007-08-09
I believe what happened is that X Server did not properly detect h/vsync for the monitor.

---

### Post by tgalati4 on 2007-08-09
Control-Alt-Backspace then hold down the escape key or hit Control-C a few times, this will sometimes stop the restart of X and leave you in a terminal.

---

### Post by Tr0janV0dka on 2007-08-09
I'm trying to install it through the console BTW. AFAIK, that was the only way to do it up until now.

---

### Post by overdrank on 2007-08-09
> **Tr0janV0dka said:**
> I've tried the sudo dpkg-reconfigure xserver-xorg and it wasn't really that useful... it tended to skip things when I wanted to change them (resolution for example).

As for this Envy thing... I only read it on one forum while trying to fix this problem. I'll look into what this Envy thing is.

Envy has worked for some as in this thread
[http://ubuntuforums.org/showthread.php?t=515641&highlight=nvidia+8800GTX](http://ubuntuforums.org/showthread.php?t=515641&highlight=nvidia+8800GTX)
Good luck!

---

### Post by Hospadar on 2007-08-09
Yah I would also recommend envy, it's really very complete. go to a text terminal with ctrl-alt-F1 and do something like```
sudo apt-get install envy
envy -t

```
first remove and clean, then install, make sure when envy asks you if it can change your xorg.conf, that  you let it, then let it restart your xserver.

---

