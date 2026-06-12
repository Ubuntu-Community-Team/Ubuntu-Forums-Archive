---
title: "Wake from Suspend, screen brightness problems on Gateway"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Andy S. on 2007-11-28
Hi, this is my first post! I LOVE Ubuntu, I'm a new switcher from Vista. Not dual-booting, I'm diving right into Linux.

I've seen various fixes on how to fix the following problem, but they all involve doing stuff I'd rather not do because I'm afraid the problem is too hardware-specific.

When I put my Gateway MT3423 in Suspend, it works. The problem is waking back up. I can tell the computer tries, when I press the power button, but the screen stays black. No flicker, nothing. I tried tinkering with settings in the acpi-support file, but nothing worked. Again, I can't tell what the cause is.

Secondly, and what might be related; is not being able to adjust the screen brightness.

I've enabled and disabled the Nvidia driver, as well. It's an MCP51 PCI-X GeForce, I guess.

Any help at all would be greatly appreciated. Thanks!

---

### Post by gvoima on 2007-11-28
I had similar problems, that waking up from suspend only resulted in a black screen, no matter what I did.
My cause was the nvidia drivers, there's a bug that nvidia claimed to have fixed with the newest beta (169.x beta) drivers. I installed them and it worked. It's a shame that they are proprietary drivers, this could have been fixed ages ago.

I understood that this is hardware related and therefore suspend didn't work even with the xorg nv driver.

Atleast you can try, if it doesn't help you loose nothing :)
And with the newest beta, you get PowerMizer support! (Only adaptive clocking on my adapter, 6200TC).

---

### Post by Andy S. on 2007-11-28
Where can I find this beta driver?

---

### Post by Andy S. on 2007-11-28
Never mind, I found it. I'll give it a try.

---

### Post by Andy S. on 2007-11-28
I couldn't install it because I was given this error: No precompiled kernel interface found.

Do not have libc header files.

Install libc development package.

What in the world is this? It took me long enough to figure out how to install the damn thing, which asked me to disable X. It's taken me hours to get this far, now I need to decipher new Linux code. libc? Huh? Please help!

---

### Post by gvoima on 2007-11-29
Well you should (apt-get) install your current kernels source and linux headers, then also install build-essential. Then instead compile the kernel module when the installer asks for if it should check a module from the net.

Then at the end of the installer, don't do the xserver configuration when it asks for it.
If all goes well, you should be able to boot with the new module (and have nvidia in xorg.conf).

What kernel are you running?
type uname -r in terminal..

```
sudo apt-get install linux-headers-`uname -r` build-essential
```
Should install the required pakcages, but you may need the source, it's named linux-source-`kernel version here`

---

### Post by Andy S. on 2007-11-29
Thank you very much for helping me. But I'm still understanding the ways of the terminal, and need help knowing what exactly to type.

I did uname -r and got 2.6.22-14-generic.

So I tried:

sudo apt-get install linux-headers- generic build-essential

didn't work. So I tried

sudo apt-get install linux-source-generic

didn't work. So I tried sudo apt-get install linux-source-2.6.22-14-generic

didn't work. So I tried

sudo apt-get install linux-source-x86

Confused! I know I'm a pain, but I kind of need my hand to be held. Sorry.

---

### Post by gvoima on 2007-11-29
Well copy&paste the code what I typed in my previous post and then also do```
sudo apt-get install linux-source-2.6.22
```
That should do it.

---

