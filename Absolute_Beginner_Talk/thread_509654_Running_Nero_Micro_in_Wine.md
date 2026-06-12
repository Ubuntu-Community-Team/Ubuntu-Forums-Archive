---
title: "Running Nero Micro in Wine"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by nemo.r on 2007-07-25
Firstly, I am a complete newbie so please write any replies as simply as possible! 
Thank You

I'm trying to run Nero micro 7.7.5.1 in Wine. I know Nero and Wine don't like each other, but I want a program that can change .avi files to dvd files in just one process.

I've tried using avidemux, k3b devede and nerolinux, but I just can't get my head around the long process. So I was wondering if there was ANY way I could get nero working.

I ran the nero install and that seemed to work, but then when I clicked on nero.exe I got the message I was missing 'olethk32.dll'. I then typed olethk32.dll into google and downloaded it. I put it in the nero core file, and then clicked on nero.exe and nothing happened. I then moved it (through nautilus) into windows system_32, and clicked on nero.exe and again nothing happened.

Is there some other .dll file that I need to get, or am I not using wine right? I just go to Main Menu>Accessories>Wine File, then navigate to the c:\ drive, should I be doing something else?

---

### Post by ddrichardson on 2007-07-25
I'm not an expert with wine - but I know Nero installs its own driver under Windows so I'd imagine it isn't the solution you're looking for.

AviDemux can transcode the files and qdvdauthor can sort out the disc for you - both are available through Synaptic.

---

