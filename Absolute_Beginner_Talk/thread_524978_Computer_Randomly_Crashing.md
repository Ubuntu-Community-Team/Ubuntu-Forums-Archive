---
title: "Computer Randomly Crashing"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by gammapulsar on 2007-08-13
Hello, I have been running Dapper for about 2 days and after the 1st day (which went pretty well) it started crashing, a great amount of times, almost always when I'm using mozilla (is this important? :X).

Anyway, this isn't a exclusive of Ubuntu. Before installing it I had the same problem with windows, but I thought it was because of some virus, buggy registry or "whatever"... and the 1st day using ubuntu sounded like backing up that theory, but now, it's doing the same thing so,, 

I mean, does this sounds like Hardware or software related problem?
Is it time to get new pieces? :x
Advices on fixing this?


Thank you for your time and help.^^

---

### Post by Bart_D on 2007-08-13
> **gammapulsar said:**
> Hello, I have been running Dapper for about 2 days and after the 1st day (which went pretty well) it started crashing, a great amount of times, almost always when I'm using mozilla (is this important? :X).

Anyway, this isn't a exclusive of Ubuntu. Before installing it I had the same problem with windows, but I thought it was because of some virus, buggy registry or "whatever"... and the 1st day using ubuntu sounded like backing up that theory, but now, it's doing the same thing so,, 

I mean, does this sounds like Hardware or software related problem?
Is it time to get new pieces? :x
Advices on fixing this?


Thank you for your time and help.^^

Could be a failing hard drive.  But, this is one of many possible reasons...I'd wait for someone else reply.

---

### Post by gammapulsar on 2007-08-15
A friend of mine told me to do memtest, I did it and the fist time there was an error:
"test: 7
pass: 0
Failing address: 00058356988 - 1411.3 MB
Good: 6559999ae
Bad: 659199ae
Err-bits: 00080000
count: 1"

I don't know what this means, but I know it shouldn't present any error, so then I did the memtest with 1 piece of RAM at a time (I have 2 "sticks" of 1GB and 512MB), but this time no error was found, and I ran the circle for about 5 times. But still, I tested each of them and still got the crashes... :/

And I've replaced the harddrive for another and still crashed. :/

Anymore ideas?
Btw, is there a problem if I put a PCI graphic card on a motherboard that has both AGP and PCI slots? Because on the Motherboard's manual it says: "the AGP slot is used to install a graphics card". I really don't want to damage anything more :/


 (ps. the mb is a ASROCK 775v88 ),

---

### Post by st33med on 2007-08-15
The memory has to be the same models. You can't have two different modules, else the OS 'chugs' because it is trying to translate some memory that was swapped. Either get rid of one of those modules (keeping the gig) or get an exact module that matches the other.

It also explains why it crashes using Firefox because it is a high memory user, so that means more data to translate.

---

### Post by Hobo Joe on 2007-08-15
Have you installed Beryl or something similar?

EDIT:

I didn't read your post right, this is a hardware issue, my bad.

---

### Post by gammapulsar on 2007-08-15
> **st33med said:**
> The memory has to be the same models. You can't have two different modules, else the OS 'chugs' because it is trying to translate some memory that was swapped. Either get rid of one of those modules (keeping the gig) or get an exact module that matches the other.

I've already tested with only one piece at a time and the crashes persisted :/

---

### Post by st33med on 2007-08-15
Hrmmm... It could be a bad motherboard. Can you try testing the memory in another computer?

300th post. Woohoo!:popcorn:

EDIT: Better if you did this, can you try replacing the memory with something else from another computer?

---

### Post by gammapulsar on 2007-08-15
> **st33med said:**
> Hrmmm... It could be a bad motherboard. Can you try testing the memory in another computer?

300th post. Woohoo!:popcorn:

EDIT: Better if you did this, can you try replacing the memory with something else from another computer?

Oh,, Not the motherboard! ;__;
Not really, since right now I only have a working laptop and this computer on my house :/. The other computer is old and the ram is diferent...

By the way, what seems to be rulled out as the "main cause" of these crashes?
The harddisk and the RAM or nothing yet?
Is there any more likely suspect?


Sorry if I'm being too pushy but this is seriously very annoying, specially when this computer almost never crashed in 2 years and a half (not counting this week, of course :x),


PS_ Congratulations! xD

---

### Post by st33med on 2007-08-16
The memtest is telling us that some memory is unusable. Check the connectors on the motherboard, just to make sure the connections are right.

Could you also give us the memory module? Meaning, what manufacture made it?

---

### Post by oilchangeguy on 2007-08-16
also, random crashing could be a failing power supply.

almost forgot, could be overheating. how long has it been since the computer has been cleaned? cloged vents are a death sentence.

---

