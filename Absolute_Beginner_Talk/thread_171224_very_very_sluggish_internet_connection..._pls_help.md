---
title: "very very sluggish internet connection... pls help!"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by learningtofry on 2006-05-06
Hi all, am a recent convert to ubuntu and a true newbie. But I already totally love Ubuntu, Linux, and all the principles enshrined therein, and hope to learn a lot about it over time. 

However I'm facing a rather silly problem. It is with my Ubuntu (Breezy Badger) internet connection. The problem is not that it doesn't connect - it does connect (i did the sudopppoeconf thingy), but once it does, the connection simply does not work properly - it is extremely slow and rather sluggish. And it sometimes takes upto an hour to just start up. 

To give an idea, it is at least 30% slower than Windows on the same connection. I get streaming radio on Windows, never on Ubuntu. 

My current internet connection is extremely erratic and unstable (and that's another story altogether), but yet, windows seems to deal with it much better. So maybe the problem is some detail in my Ubuntu set up?

I have tried all the basic things like running pppoeconf again, and pon dsl-provider but usually it's no use. And since I don't come from the tech world, I don't even know where to begin. Can anyone help me solve this problem? It is really very frustrating using Ubuntu as things stand. 

I think what could help here would be a list of things that could be wrong - and then I will attack them all one by one, till the solution appears. 

I also want to test and confirm that the problem is not with my network card, the cabling or other hardware. How does one do that? My machine is a P4 with 256 mb ram and an 80 gb hard disk, so i would assume it shouldn't be this slow.

Also, if I need to provide this forum details about my hardware, how do I source that out - can i find that out through certain commands?

Apologies if I've got anything wrong - am totally new here. Is there anything else I need to add? And thanks a ton in advance.

---

### Post by Sef on 2006-05-06
What type of network card do you have?

And you connect to the net via dsl?

---

### Post by learningtofry on 2006-05-07
Thanks so much for replying. This is my hardware:

Device type: Network Adapter
Realtek RTL8139 Family PCI Fast Ethernet NIC

Intel(R) Pentium(R) 4 CPU 2.40 GHz
256MB RAM

As for a DSL connection, I use a cable connection... not through the phone line but thru a separate cable. Hope that is the useful answer.

---

### Post by richbarna on 2006-05-07
I have heard that in Debian based distros this card has a problem with "acpi" (Advanced Programable Interupt Controller).
Try changing the Grub config from the terminal:-
> sudo gedit /boot/grub/menu.lst adding "noapic acpi=off".

This is an example of what it would look like on Debian. 
> Example:
 title Debian GNU/Linux, kernel 2.4.27-2-686 
 root (hd0,0)
 kernel /boot/vmlinuz-2.4.27-2-686 root=/dev/hda1 ro noapic acpi=off
 initrd /boot/initrd.img-2.4.27-2-686
 savedefault
 boot

---

### Post by learningtofry on 2006-05-17
thanks for the suggestions so far, tried them, but nothing has worked... in fact, now things have goten worse, and there is absolutely no internet connection on my machine at all. am this close to giving up on linux, and i really dont want to. need a machine with an internet connection afte all... now my provider tells me i need a router to be able to use linux. makes no sense. what to do. where to begin.

sorry if i am irregular on this post, but am very busy these days, and its almost impossible to get to this page with my current internet connection.

---

### Post by richbarna on 2006-05-17
I agree with your provider, get a router, IMHO it is the easiest way to connect to the internet in any Linux distro.

---

### Post by learningtofry on 2006-05-17
could you please explain why

---

### Post by diw on 2006-05-20
I connect through a dsl router and through windows it is lighteningly fast with 8mb broadband.  But under Ubuntu and fedora it is like a tortoise and is really frustrating.  Under xandros it is pretty good but still not as fast as windoze.  I have never solved the problem but it is a real frustration and won't continue with ubuntu unless i can crack the problem.  Accessing the forum is pretty dire - its like going back to a 56k modem.

---

