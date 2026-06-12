---
title: "Bios error while booting."
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by soeten on 2007-08-14
Hello, 
When I am starting my ubuntu-laptop i get this "error"-message:
[I]Starting up . . . 
[	0.248778] PCI:  BIOS BUG #81[49435000] found
[	0.522793] PCI: Failed to allocate mem resource #6:100000c0000000 for 0000:0
1:00.0
[/I]

Does anyone knows what this means? (Nothing seems disfunctional)

And just one other small question, the laptop is supposed to have 1gb ram (2x 512) but in 'System Monitor' it says "Memory: 756.1 MB". Is this because my gfx card is integrated and has a shared graphic memory?

Thanks
-Soeten

---

### Post by guguma on 2007-08-14
I do not know about the bios bug, but the memory problem is just as you say so.

---

### Post by oilchangeguy on 2007-08-14
> **soeten said:**
> Hello, 
When I am starting my ubuntu-laptop i get this "error"-message:
[I]Starting up . . . 
[	0.248778] PCI:  BIOS BUG #81[49435000] found
[	0.522793] PCI: Failed to allocate mem resource #6:100000c0000000 for 0000:0
1:00.0
[/I]

Does anyone knows what this means? (Nothing seems disfunctional)

And just one other small question, the laptop is supposed to have 1gb ram (2x 512) but in 'System Monitor' it says "Memory: 756.1 MB". Is this because my gfx card is integrated and has a shared graphic memory?

Thanks
-Soeten

question 1.  don't know what it means, and doubt anyone else wil either. have you done a google search of the error message?

question 2. yes, possibly. have you done reasearch to confirm your ram is what it says it is? try one stick at a time and see what you get. sounds like one stick is 256, not 512.

---

### Post by fastpakr on 2007-08-14
It [looks](http://ubuntuforums.org/showthread.php?t=499811&highlight=bios+bug) like this issue is unresolved.

---

### Post by soeten on 2007-08-14
Okay, thanks. Ill just leave the BIOS message for now then.
Its a brand new laptop so Im a bit worried about opening it and checking the ram, since Ive never opened a laptop before.

---

### Post by Coward on 2007-08-14
I think
[ 0.248778] PCI: BIOS BUG #81[49435000] found
means you have a 64-bit processor running the 32-bit version of Ubuntu. I could be completely wrong, but I don't think it causes any problems.

---

### Post by amazingtaters on 2007-08-14
> **Coward said:**
> I think
[ 0.248778] PCI: BIOS BUG #81[49435000] found
means you have a 64-bit processor running the 32-bit version of Ubuntu. I could be completely wrong, but I don't think it causes any problems.

I get this bug, and have 32 bit Ubuntu running on a 64 bit system. Doesn't cause any issues, at least I haven't run across any. And the memory thing is because of the onboard graphics card. That is very standard for onboard cards. They use system memory instead of their own dedicated memory.

---

### Post by soeten on 2007-08-14
Okay, thanks.. Then I assume I got nothing to worry about. :p
(I got a 32bit processor thou)

---

### Post by oilchangeguy on 2007-08-14
> **soeten said:**
> Okay, thanks. Ill just leave the BIOS message for now then.
Its a brand new laptop so Im a bit worried about opening it and checking the ram, since Ive never opened a laptop before.

the great thing about a laptop is you don't have to take it apart, to get to the ram. it should be located under one of the panels on the bottom. consult the owners manual the see which panel it is.

---

### Post by fastpakr on 2007-08-14
> **soeten said:**
> Okay, thanks.. Then I assume I got nothing to worry about. :p
(I got a 32bit processor thou)

Hmm... eliminates that theory.  In any case, I've also got the bug on my F572 and haven't noticed any issues that I could tie to the error.

---

### Post by fastpakr on 2007-08-14
> **oilchangeguy said:**
> the great thing about a laptop is you don't have to take it apart, to get to the ram. it should be located under one of the panels on the bottom. consult the owners manual the see which panel it is.

Yep - either under an obvious panel on the bottom, or lift the keyboard and it will be right underneath.  Either way, it should be quite straightforward.

---

### Post by hardyn on 2007-08-14
somtimes removal of the keyboard is less than straight forward... but not impossible IF YOU HAVE THE RIGHT TOOLS!

i have that bios issue as well... and its entirely possible that it is not really a bug, but kernel as been written to expect something and something about the implimentation of something by the hardware vendor forces a work around.  the linux kernel is very robust and has been designed to run on just about anything, its possible it is trying to find some depreciated hardware; or is maybe looking for that new style bios (like apple uses)

of course its all just speculation... i have that error messages, and had no ill effects in my 2 years of running ubuntu.

---

### Post by jgriffinpark on 2007-11-08
I am having this same problem too... Maybe I'll try running the 64 bit version.

---

