---
title: "How do I share a printer?"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Talon2 on 2006-12-13
My experience sharing printers over the years is with Peer to Peer.

I am fairly new to Ubuntu.  It isn't obvious to me how to share a printer.  Here is my local network:

- System 1: Running Ubuntu with Brother HL5050 connected via parallel port.  System connected to DLink router via ethernet cable.

- System 2: Running Ubuntu.  System connected to DLink router via ethernet cable.

- Systems 3 and 4:  Running Ubuntu.  System connects to DLink router via wireless.


Printing works great on system 1 but I have no idea how to get systems 2, 3 and 4 to print to the printer connected to system 1.

Help appreciated.

---

### Post by _simon_ on 2006-12-13
I had huge problems doing this.

In the end I just bought a parallel auto switch.

Like this: [http://www.amazon.co.uk/Belkin-Compact-Parallel-Auto-Switch/dp/B00004Z5ZJ](http://www.amazon.co.uk/Belkin-Compact-Parallel-Auto-Switch/dp/B00004Z5ZJ)

All you do is connect it to the printer and to each of the machines - (obviously if you have 3 machines you'd need one with more ports) then just set each machine to connect to the printer as normal. The auto switching means that the switch will detect which pc is trying to print (first).

---

### Post by Talon2 on 2006-12-13
> **_simon_ said:**
> I had huge problems doing this.

In the end I just bought a parallel auto switch.

Like this: [http://www.amazon.co.uk/Belkin-Compact-Parallel-Auto-Switch/dp/B00004Z5ZJ](http://www.amazon.co.uk/Belkin-Compact-Parallel-Auto-Switch/dp/B00004Z5ZJ)

All you do is connect it to the printer and to each of the machines - (obviously if you have 3 machines you'd need one with more ports) then just set each machine to connect to the printer as normal. The auto switching means that the switch will detect which pc is trying to print (first).

Simon, I appreciate the info but that won't work here.  Systems 3 and 4 are located in different parts of the building and running 30-50 feet parallel cables is not going to work.

Previous operating systems in use worked great for sharing the printer via peer networking.  I've been reading everything I can find but either sharing a printer is FAR more complicated in Linux than it should be or I'm missing something.  I hope I'm missing something.

---

### Post by _simon_ on 2006-12-13
It does seem to be far more complicated hence why I gave up and purchased the parallel switch. 

I'm sure you'll work it out sooner or later, with or without any help that other people may offer. Sorry my suggestion isn't practical for you.

When you do get it sorted out, maybe you could write a definitive HOWTO on it! :)

---

### Post by Talon2 on 2006-12-14
At this point I've found bits of information but still nothing that working for setting up CUPS to CUPS printer sharing.

If anyone can point me to a HowTo that is complete and works for Dapper I'd appreciate it.

Observation:  My 2 months of learning Ubuntu are mixed.  Some things just work.  Other things (like video and printer sharing) are just not ready for the desktop market.

Cheers.

---

