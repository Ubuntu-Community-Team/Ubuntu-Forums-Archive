---
title: "Standby Problem"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-01-24
My computer will not go into standby or hibernate anymore it will just lock the screen. When I  unlock my wireless connection cannot be detected anymore and I have to restart. When I restart I get an error message saying:

unregister_device: waiting for eth1 to be free usage count = 1

So then I have to manually shutdown. Help!

---

### Post by energiya on 2007-01-24
Did suspend worked for you before? What video card do you have?

---

### Post by dbbolton on 2007-01-24
ubuntu is notorius for standby/hibernate problems. as far as i know, there aren't any true solutions.

you might just have to disable those actions in your power management.

---

### Post by syalam on 2007-01-24
I have been using Ubuntu for about a month now and suspend has always worked up until today. I am using a laptop so my videocard is actually the Intel 855 graphica media controller chipset.

Yesterday I installed some network security library Snort for a course im taking. I'm not sure if that has anything to do with anything.

---

### Post by nsleiman on 2007-01-24
> **syalam said:**
> My computer will not go into standby or hibernate anymore it will just lock the screen. When I  unlock my wireless connection cannot be detected anymore and I have to restart. When I restart I get an error message saying:

unregister_device: waiting for eth1 to be free usage count = 1

So then I have to manually shutdown. Help!

i tried a lot to make it work but i gave it up lately :) i think it has to do with the kernel/vga card

---

### Post by syalam on 2007-01-24
Maybe, but it worked before with no problems. I think the error message is a clue, some process is using my eth1 and it can't be shutdown therefore i cant go into standby...

---

### Post by syalam on 2007-01-24
I uninstalled my network security progs:

Wireshark, Nessus, and Snort. One of those was keeping eth1 alive preventing the system from shutting down. 

Can anyone tell me how to show the running networkI services that way I can pinpoint which app it really is?

---

### Post by phr0ze on 2007-01-24
When I installed AirSnort, My hybernate function started giving the exact same error.

---

### Post by syalam on 2007-01-24
yeah snort is hogging eth1 preventing it from being shutdown. i dont know how to manually stop it without hard booting.

---

