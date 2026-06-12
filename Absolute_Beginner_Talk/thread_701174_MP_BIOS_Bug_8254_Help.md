---
title: "MP BIOS Bug 8254 Help"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Mattxcore on 2008-02-19
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=4360598#post4360598](http://ubuntuforums.org/showthread.php?p=4360598#post4360598) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				MP-BIOS bug: 8254 timer not connected to IO-APIC is the error i'm getting when I try to boot from CD to install ubuntu 7.10


I've gone with the whole noapic thing and it just brings me up to a prompt to enter codes


I don't know what this means or how to fix it. I've never ever used ubuntu so i don't know what to do.



I've tried taking "Quiet" out when I hit F6 and adding noapic to the end. It starts to start up. And then asks for codes again.


I've come across things asking for a grub menu online.

I have no clue how to get to that either.

Can someone please help?



I am running on:
eMachines T3516
RC-410 Motherboard
Celeron D Processor 352 with 3.20ghz
512MB of Ram
120 GB Hard Drive
Windows XP Home

---

### Post by Thingymebob on 2008-02-19
I think you need the alternate install CD for this machine (64bit AMD & Intel computers)

---

### Post by 3rdalbum on 2008-02-19
When you say "A prompt to enter codes", what exactly do you mean? What comes onto the screen?

Is it something like this:

```
ubuntu@ubuntu-desktop:~$
```

Also, what specific version of Ubuntu are you trying to use. If you are trying to use the server edition, then don't - it's designed for experienced Linux people who know the commands to type in. You would find the desktop edition much easier to use.

---

### Post by Mattxcore on 2008-02-21
I am trying the Desktop edition.

But no it looks different.

It's almost like dos.






And try the 64 bit CD?

Okay, will do. I did order a copy of it just incase.

---

### Post by dcstar on 2008-02-21
> **Mattxcore said:**
> **This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=4360598#post4360598](http://ubuntuforums.org/showthread.php?p=4360598#post4360598) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				MP-BIOS bug: 8254 timer not connected to IO-APIC is the error i'm getting when I try to boot from CD to install ubuntu 7.10
........

Unless the Ubuntu installation stops then you can ignore this message - it is essentially saying that your PC's BIOS does not conform to the standards that the Linux kernel expects.

This message comes up on my PC and my Ubuntu works fine.

If it does stop the install, then go into your BIOS and disable APIC.

---

### Post by JimBuntu on 2008-02-22
im having sort of the same problem. What is APIC and how do you disable it???

---

### Post by snakeboy on 2008-02-24
I also have this (Toshiba Laptop Model - Satellite A60), and I'd also know what exactly is APIC?  I have NO option in my bios to disable it.

---

### Post by cmapesjr on 2008-02-27
Thanks for the tip. I had this error show on boot forever, but never seemed to
cause any problems. I disabled it in BIOS. Error gone.

---

