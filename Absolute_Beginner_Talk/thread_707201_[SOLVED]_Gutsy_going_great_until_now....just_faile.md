---
title: "[SOLVED] Gutsy going great until now....just failed!!"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Redptc on 2008-02-25
I'm using Windows to send for help. Ubuntu has been going really well, a few 'sound' problems, it was flawless!

Today, It just failed to boot up! Nothing has changed, no updates, no new hardware or even new programs. Not even an electric storm! It tries to fire up but doesn't.

I have to boot windows with the Live CD and select"Boot from First Hard disk"

Ubuntu says...[COLOR="Blue"][260.536137] hub 1-1:1.0 connect-debounce failed, port 2 disabled.[/COLOR]
It repeats this phrase over and over but with a different selection of numbers....as if searching endlessly!

I can't run a terminal in Ubuntu, anybody know how to :cry:fix it???



Redptc

---

### Post by justleen on 2008-02-25
hmm.. got any USB devices hooked up to the machine?
if so, can you try booting without them plugged in?

---

### Post by Redptc on 2008-02-25
> **justleen said:**
> hmm.. got any USB devices hooked up to the machine?
if so, can you try booting without them plugged in?

Yes, I connect to the internet via a usb ethernet card. I'll unplug and see.

---

### Post by Redptc on 2008-02-25
Tried that but nothing changes. This has been running cleanly for many months- this is not a new install. It is a strange business.

It is a dual boot and it has been running well.:confused:

I can't even run it from the live CD which I could previously.

---

### Post by steveneddy on 2008-02-25
what were you doing right before you shut down last?

Have you done a memory check from the Live CD?

---

### Post by philinux on 2008-02-25
Just guessing that it could be a kernel update thats borked your system. When you boot does grub stage 1.5 show up? If so press esc when it does and select an older kernel.

---

### Post by Redptc on 2008-02-25
> **steveneddy said:**
> what were you doing right before you shut down last?

Have you done a memory check from the Live CD?

This has been going so well that the missus now uses Ubuntu as first choice. She was on the Internet.

No I haven't done a memory check but what would that tell us? In any event I will do one and get back.

---

### Post by Redptc on 2008-02-25
> **philinux said:**
> Just guessing that it could be a kernel update thats borked your system. When you boot does grub stage 1.5 show up? If so press esc when it does and select an older kernel.

I can't recall if it does show up but I will re-check.

---

### Post by bhavi on 2008-02-25
same question here mates:

[https://answers.edge.launchpad.net/ubuntu/+question/25582](https://answers.edge.launchpad.net/ubuntu/+question/25582)

---

### Post by Flyingjester on 2008-02-25
That's bad business if you can't run  from the live  cd, that would lead me to believe it's a memory problem.

---

### Post by bhavi on 2008-02-25
> **Flyingjester said:**
> That's bad business if you can't run  from the live  cd, that would lead me to believe it's a memory problem.
hmm.. looking into it.. You seem right it could a memory problem or a kernel update problem..

---

### Post by Redptc on 2008-02-25
Oddly, I fired it up first thing in the morning and it acted normally. I continued to work on the PC to try to locate the problem. At about the #10 or#11 boot the problem developed again and got progressively
worse in that it took longer and longer to boot. It eventually refused to boot at all.

I let it rest and 'cool down'. After a time it booted normally again only to fail to reboot after 60mins use.

Is it possible that overheating, somewhere, is the problem?:confused:



The memory test indicated that there was no problem evident.

---

### Post by Redptc on 2008-02-29
This is a known bug....#88530. To solve it, we installed Hardy kernel vers 2.6.24.........and back to running a perfect system!

Results from answers.launchpad.net/ubuntu/+question/25582

---

