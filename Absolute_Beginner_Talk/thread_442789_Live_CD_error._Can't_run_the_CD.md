---
title: "Live CD error. Can't run the CD"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Hobo Joe on 2007-05-13
Ok, I installed Feisty 64-bit fine with my new computer. But I want to back down to 32 bit, or even got back to 6.10. But the problem is: I can't. It doesn't work
I have 5 live CD's sitting around, and the only one that works is the 64-bit Feisty one. All the others return an error message. But the thing is, I know that they work, because I've done a perfectly fine install with 2 of them.
Here are the ones I've tried.
Ubuntu 6.10 32-bit - error, successful install on different computer
Kubuntu 6.10 32 bit - error, successful install on different computer
Ubuntu 7.04 32-bit - error
Ubuntu 7.04 alternate install 32 bit - error
Ubuntu 7.04 64-bit. No error, running successful install right now on current computer. 

When I stick in the live CD, it loads fine to the normal startup menu, but when I click on an option(This is ANY option on the list) I get the following error:

```

MP-BIOS bug: 8254 timer  not connected to IO-APIC
Kernel Panic-not syncing: IO-APIC + timer doesn't work! 
boot with apic=debug and send a report. T
hen try booting with the 'noapic' option


```

Any help would be greatly appreciated, this is getting to be extremely frustrating.

---

### Post by Hobo Joe on 2007-05-13
Ok, I've figured it out! To anyone who has this problem and needs a solution, here's what you have to do:

When the menu shows up on the live CD, press F6, this will give you a command line of sorts, that already has a big loooooooong line of code in it. Just go to the end of the code and type in 'noapic'.

That's it.

---

