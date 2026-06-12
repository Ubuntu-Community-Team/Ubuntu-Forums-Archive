---
title: "How input is handled on ubuntu vs windows"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Pro_D on 2007-05-11
I don't know if this is absolutely a beginer question but seems simple on the surface.

I have always felt strange using linux distros that had a gui (knoppix, red hat, ubuntu in that order) when doing things.  It just felt kinda slow but that isn't quite right either.

Well I happened to have ubuntu up when a friend came by, he wanted to show me some funny fighting flash game.  I popped open firefox, went to the game, and he showed me.  He complained over and over that it didn't seem to respond to his input and so I tried.  I am a bit faster on the keyboard than he and I just couldn't seem to get the game to work right till I slowed my input WAY down to about when it was needed (rather than before it was needed).  This gave me an idea and so I opened up the text editor and tried to hit alt-file-save very fast and got either nothing or the file menu, if I slowed down I got the file saved.  Same way with open.  Now I think I understand why I felt so odd using linux distros.  Something is odd about how input is handled in it.

As I understand it (somewhat simplistic), on windows when you make input the input goes immediately to a buffer and then software gets a message that input has been made to it, it then gets input from the buffer one at a time, responding to each bit of input it retrieves, till empty.  Ubuntu (at least in the software I have tried) doesn't seem to work this way.  It almost seems like if you make input before the software is ready to recieve it then the input gets ignored.  Typing (like right now) doesn't seem to be affected by this, just gui/graphic related stuff.

Is there a way to make it feel more like windows?  I also don't know if this is different from Kubuntu (I kinda got hooked on ubuntu first and don't have any kubuntu disks about).  I am curious about this for more than just myself.

---

### Post by Foxmike on 2007-05-11
Well, I am not a coder, but I began reading Python stuff lately (object oriented scripting language...).  One interesting thing I saw and maybe it is teh same thing over C/C++ is that there is a "mainloop" called upon loading softwares in GUI, which seems to be a server that wait for any input ant then sends signals to the proper funcion in the software.  That being said, maybe the answer is in the responsiveness of that layer between input devices and processes.  But again, maybe is there the exact same concept with Windows apps so the answer is somewhere else.

Regards,

-FM

---

### Post by Henry Rayker on 2007-05-11
Well, actually, the input is probably going to be handled via hardware interrupts. Using a loop to take input (also called a polling method) is VERY inefficient. I don't know how much of a difference there could be (I've never experienced one, nor have my brother or girlfriend). I have heard of video drivers slowing the things down (although I don't quite understand how or why)...maybe that could be your issue?

---

### Post by Pro_D on 2007-06-03
Thanks for the tidbits, I just wish I wasn't 3 weeks without being able to touch this system - it took me a day to remind myself of how things work in ubuntu and what I was working on exactly.  This gives me a few more ideas on where to look when I am ready to takle that bit of learning.

I am thinking it might not be an issue in quite the way I was thinking.  For one thing my testing under both ubuntu (soon to be kubuntu) was very flawed.  My tests were largely based on rapidly pressing alt-f, s in apps that had file-save and were quick to make something with (I tried other hotkeys btw).  In windows apps holding alt and hitting f and then s is acceptible but in the apps I have tried in ubuntu (and gimp on windows) alt-s is ignored after the alt-f, After you hit alt-f you are expected to release alt and then hit s (or whatever your submenu hotkey is).

What this all tells me is that my test for input latency was totaly out the window and I should look elsewhere for why something in firefox acted strange/slow.  This also tells me why linux (not just ubuntu) feels slow/wierd sometimes, it's that I am pressing the s key faster than I am releasing alt (which it feals natural to be releasing alt anyway).  I am just fine with this behavior btw.  Most users I have watched (when they use hotkeys) generaly release the alt key before inputting the next key for menus also.

---

