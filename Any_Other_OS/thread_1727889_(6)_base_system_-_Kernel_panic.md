---
title: "(6) base system - Kernel panic"
date: 2011-04-13
forum: Any Other OS
---

### Post by fdm on 2011-04-13
I have two computers that I have been using to test a Kernel panic that has recently popped up after I upgraded my Ubuntu 10.10 base system and added the polipo and museekd daemons. I have reproduced this panic on two completely different hardware setups(no shared parts). The harddrive and memory where tested several times, making sure the slots were okay(SeaTools, MemTest 2&4). One is a 700mhz P3, the other is a 1400Ghz Celeron. Other than that, they have very similar Intel chipsets, PC-133 SD Ram and controllers.

I have looked through all my logs, and couldn't find anything about the panic, so I had to wait for a friend to give me his phone so I could take a picture. I have also tried Natty, hoping to escape the problem with newer packages/Kernel(Crashed also). The crash occurs randomly generally between 24 and 48 hours.

This is all from Debian 6, as it is what I am testing now. At this point I am stopping one services at a time and waiting for a crash, so museekd is excluded from the process list. Tor and Polipo are from the tor stable repo and uTorrent server is the latest public alpha available. Everything else is from the main repo.

Screen-shot of panic: 
[http://bayimg.com/NAHahAadJ](http://bayimg.com/NAHahAadJ)

Here is some info from the Celeron:

uname -a:
Linux tbox-mc 2.6.32-5-686 #1 SMP Tue Mar 8 21:36:00 UTC 2011 i686 GNU/Linux

sudo lspci -v:
[http://pastebin.com/1W9a4YME](http://pastebin.com/1W9a4YME)

lsmod:
[http://pastebin.com/AanLnuqk](http://pastebin.com/AanLnuqk)

ps aux:
[http://pastebin.com/A7k3zh57](http://pastebin.com/A7k3zh57)

I thought that user-restrictions and the kernel should protect me from the more uncommon or risky daemons that I install from writing over kernel owned memory and mem leaks knocking out the system(though I've seen no sign of one). It seems all the problems I've had in the past came from X or divers, never the kernel(as far as I could tell). Any info about how this might be triggered or how to locate the lines in the source code from the virtual addresses(or offsets) in the call trace would be much appreciated.

---

### Post by fdm on 2011-04-23
This is old and inactive, but I thought I'd share the solution. The error message is memory related as I originally guessed. I was running 256MB PC-133 SD x 2 and getting crashes no matter what I crippled. So I pulled one stick at a time, and I got days of uptime with each each(no more random seg faults or kernel panics). The solution was to revert back to 320MB(64 x 1, 256 x 1), as that is more than enough to run what I need for now.

---

