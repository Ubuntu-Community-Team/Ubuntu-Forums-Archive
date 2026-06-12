---
title: "[SOLVED] 7.1 won't load with WiFi installed"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by ilikecoffee on 2007-11-18
Finally got Ubuntu 7.1 installed, but when I install the wireless card, the loading bar freezes at about 80%.

If I take out the wireless card, I can boot up fine. But try it with the wireless card and it stalls. Same place everytime.

What can I do so that I can launch Ubuntu with the wireless card in so that I can get it working?

---

### Post by MegaJim on 2007-11-18
Patient: Doctor, it hurts when I raise my arm like this

Doctor: So don't raise your arm like that

Ok all joking aside, you want your wireless working.  when you say it stalls, how long did you wait for?

Sometimes ubuntu will try to connect to a network fruitlessly for awhile before continuing through the boot process for upto a couple of minutes.

You can also configure ubuntu to boot without a splash screen so you can just watch whats happening while it starts up, this should hopefully allow you to see exactly where the problem is occuring!

---

### Post by ilikecoffee on 2007-11-18
I've tried waiting for five minutes (timed it). 

I currently have a CAT5 line that's 25ft. going from computer to router. Well, this won't work, thus, the wireless.

I've tried removing the line with the card in... nothing. It's the card that makes it stop. Is there anything I can change? I've tried looking over the forums, but either I don't understand it (I'm very new to Ubuntu) or it didn't work.

---

### Post by MegaJim on 2007-11-18
remove quiet and splash from the boot options for linux so you can see whats going wrong, theres also a shortcut key to get to this screen while booting but i don't remember what it is.

edit: ok i just remembered what it is : ALT+F1

so try hitting alt+F1 as soon as the ubuntu splash screen appears and see where it gets stuck

you can skip stuff thats non-essential but holding up the boot process using the continue keystroke (CTRL+D)

---

### Post by ilikecoffee on 2007-11-18
Okay, remove quiet and splash... how do I do that? I checked the help file and put the code in the terminal to turn off splash and I got this:

(gconftool-2:10856): GConf-WARNING **: None of the resolved addresses are writable; saving configuration settings will not be possible
Error setting value: Unable to store a value at key '/apps/gnome-session/options/show_splash_screen', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf

How do I do it?

---

### Post by MegaJim on 2007-11-18
heya, check my post up there again ^ i edited it with some new info

---

### Post by ilikecoffee on 2007-11-18
Okay, Alt+F1. What should I be lookng for? And will I be able to change it? Do I need to know a code line?

---

### Post by MegaJim on 2007-11-18
> **ilikecoffee said:**
> Okay, Alt+F1. What should I be lookng for? And will I be able to change it? Do I need to know a code line?

Nothing in particular, but you're looking for whatever is stopping the system from booting (i.e. the line closest to the bottom of the screen when bootup is stalled)

it might be something like found such and such a card .... then nothing

try hitting ctrl+d to get past it, if that doesnt work then make a note of what it says and come back and post it :)

---

### Post by ilikecoffee on 2007-11-18
Hey, thanks. It loaded a list of things followed by [OK], then It got to:

Starting common UNIX printing system cpusd:

And froze.

---

### Post by MegaJim on 2007-11-18
> **ilikecoffee said:**
> Hey, thanks. It loaded a list of things followed by [OK], then It got to:

Starting common UNIX printing system cpusd:

And froze.

that should be "cupsd" btw, just so you don't get lost searching for cpusd :)

---

### Post by ilikecoffee on 2007-11-18
After a quick search for "cupsd" I found that some other people had the same problem. I couldn't find a fix, though. Any help?

---

### Post by MegaJim on 2007-11-18
don't really know about troubleshooting this kind of startup problem, sorry

something to look at though is the readme files insite /etc/init.d/ and /etc/rc*.d/ - these directories contain the scripts that run at different run levels.  somewhere will be a reference to cupsd and either that, or what follows it is causing the problem.

---

### Post by ilikecoffee on 2007-11-23
Okay, The Airlink 101 card with Reatek chipset 8185 DID NOT work. Went shopping around and guess what? At least HALF the cards I saw had the Realtek 8185 chipset! So, if the Ubuntu team hasn't found a solution for this, then they should start getting on it.
I was able to get hold of an old D-Link card and now it's working.

---

