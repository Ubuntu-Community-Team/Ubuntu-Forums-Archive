---
title: "Rosegarden"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by bharani on 2007-09-08
Hello,
              Has somebody ever used rosegarden...I just don't know how to make it work right...Like I import the banks...and none of the instruments get tuned to the right channel...Say for example is use some Korg serries and it has got all FX,Drum variations,Synths...I just don't know how to get them to proper channels...would somebody help me with this...

Bharani.

---

### Post by aonegodman on 2007-12-23
Thought I might find an answer here to my similar problem with new install of Rosegarden.

Wish I could be of help. Perhaps you are having some of the following problems also and we can help out each other.


I installed it using the following command:

sudo apt-get install rosegarden

everything seemed to install ok, but upon running first time I get the following message box on screen:

[B][I]System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low.
Please contact your Linux distributor for more information.[/I][/B]

It also added the following message box afterwards:

[B][I]missing the following support file -  flac
[/I][/B]
I'm going to attempt to locate and find flac and install it. Also said I needed have the JACK control module running prior to start.

I have this installed and was wondering if anyone knows how to set this up to run automatically on startup and place itself in the taskbar?

All replies appreciated. Thx.

---

### Post by CyberCat7 on 2007-12-23
Ijust installed rosegarden, but when I try to run it from the applicatications menu, nothing happens - no error messages, it just does not run.

My screen resolution is set to 1024x768, I can't get it set any higher. 

How do I get rosegarden to work?

---

### Post by aonegodman on 2007-12-24
My resolution is set to 1024x768 also and it loads and runs fine.

My only problem is the system timer or latency and

I can't get NO Sound out of it. Tried tweaking JACK. Tried changing the output selections from GM MIDI to Synth to Audio.

Programs loads files and runs them, just no sounds.

---

### Post by aonegodman on 2007-12-27
I've got Rosegarden working or at least I have sound now.

Follow this link and use Terminal to make all edits. I simply did a cut-n-paste on each suggestion and it worked for me.

[http://www.funnestra.org/ubuntu/gutsy/#timidity](http://www.funnestra.org/ubuntu/gutsy/#timidity)


BUT - I'm having problems with JACK Server and Rosegarden compatability right now.

I shut down JacK and run Rosegarden and It works with some time lag issues.

I have not installed the low-latency kernal yet but I thought I'd share my progress. :guitar:

---

