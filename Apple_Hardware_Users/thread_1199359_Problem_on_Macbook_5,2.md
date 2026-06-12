---
title: "Problem on Macbook 5,2"
date: 2009-06-28
forum: Apple Hardware Users
---

### Post by JRuc33 on 2009-06-28
Hey, I'm trying to install Ubuntu 9.04 on a macbook 5,2.  I get to the install screen where it asks you what language and I choose english.  Then, right afterwards I get a text error saying "Not Responding" and the screen turns black and the DVD drive stops along with installation.  I've also tried 8.10 with the same results, along with Fedora 11 with the same "Not responding" error message.  Please help!

---

### Post by MrBadger on 2009-07-04
Blast, first post lost. Retrying. OK...

I'm disappointed that there are no other replies because I'm having the exact same problem. I started using a DVD created at work with 9.04 on it (not sure if it is the 32 or 64 bit version). When that didn't work I downloaded the 64 bit distribution and burned it. Same problem.

A bit more information on the exact symptoms. I am able to select the language and get the initial installation screen. But if I choose the "Verify" or "Install" options it looks like it is starting the load process but then says something like:

[5.1234] Not responding

A second or so later the screen goes blank and stays that way forever (or at least for longer than 5 minutes which is the longest I've been willing to wait for signs of life.)

Is it just this distribution, is it just this flavor of Macbook? Any insights would be appreciated.

Mark

---

### Post by MrBadger on 2009-07-12
Hmmm, no takers, eh?

---

### Post by pxwpxw on 2009-07-12
You could test with a debian netinst to see if anything works -
[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

---

### Post by davideotape on 2009-07-13
I'm getting exactly the same problems here. I'm using 5,2 and a jaunty liveCD, and 'Try Ubuntu' 'Install Ubuntu' and 'Check memory' all result in "Not responding" after about 5 seconds. :(

---

### Post by alexmurray on 2009-07-13
I think you are experiencing this bug:

[https://bugs.launchpad.net/acpi/+bug/341230](https://bugs.launchpad.net/acpi/+bug/341230)

Basically, either try adding ```
acpi=off
``` to the boot command line (which disables all power management stuff so is not really that good) or you can add ```
nosmp
``` or ```
maxcpus=1
``` to only use 1 core of the cpu which should also allow you to boot (but again this is suboptimal).

---

### Post by davideotape on 2009-07-13
How is it possible to change how the liveCD boots? It's just that I've never come across a problem like this before, and I've only ever known how to change boot options on an actual install of grub.

---

### Post by pxwpxw on 2009-07-13
If you can see the F1....F6 bottom of screen, F1 is help . F6 lets you change command line
.

---

### Post by davideotape on 2009-07-13
Thanks for that, I successfully booted and installed. I can now get as far as grub, which seems to freeze. There's no timer, and none of the keys on my keyboard do anything :(

---

### Post by MrBadger on 2009-07-20
Hmm, haven't been paying attention to this thread in too long. I'll have to try that myself.

Mark

---

### Post by damage84 on 2009-07-27
Same problem here. I am able to get the Live CD to boot if I use the boot options, however after installing and rebooting it gets to loading grub and freezes. I would love more input on this I know installing ubuntu on a Macbook isn't exactly a highly demanded thing, but I can't believe that no one has been able to figure this out.

---

### Post by stockley on 2009-07-28
> **damage84 said:**
> Same problem here. I am able to get the Live CD to boot if I use the boot options, however after installing and rebooting it gets to loading grub and freezes. I would love more input on this I know installing ubuntu on a Macbook isn't exactly a highly demanded thing, but I can't believe that no one has been able to figure this out.

Have you tried everything they suggested?
Or did you just read the initial post and join in? :P

---

### Post by CellPhoneDude on 2009-08-03
I've got my 5,2 triple boot with refit works great until it doesn't then i have to pop a terminal and re-enable it but other wise during install I hit F6 and selected "acpi=off" as the only boot option and it installed works great grub works too but I just turned the timout to one second because it was pointless the way I partioned my drive.

---

