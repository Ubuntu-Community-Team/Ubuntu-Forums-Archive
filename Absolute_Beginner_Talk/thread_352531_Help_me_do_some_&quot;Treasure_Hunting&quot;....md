---
title: "Help me do some &quot;Treasure Hunting&quot;..."
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-02-03
Hello!

Today I bought a really good PC & it was a bargain...!!!
But the problem is, that I can't find the Mobo Model & Manual...
So, you want to do some "Treasure Hunting" with me...?

The funny part is the following:
The guy did NOT have a Mobo manual to give me.
All he gave me is a [color=blue]VIA[/color] CD-Rom which says on the outside "[color=blue]Via Driver P4[/color]".
So, I opened up the CD-Rom & looked to find the model of the Mobo...
Nothing!!! Totally Nothing!

So, I thought, what the heck, I will open up the Box & take a look at the Mobo itself...
So, I unscrewed the Box & used a flashlight to check the Mobo for some Model Info...
Nothing was printed on the Front Part...!!!
Then I unscrewed the Mobo to check the Back of it...
Nothing...!!! :confused:
So, can somebody help me solve this mystery...?

_Target/Mission_:
**To find a copy of the Mobo [color=blue]Manual[/color] & see what the Mobo can really do...**

Now the PC is installed Windows XP (I know, I know... :))
So, I booted & visited the Device Manager...

Under:

1. "IDE ATA/ATAPI Controllers", I can see: [color=blue]VIA Bus Master IDE Controller[/color]
2. "Processors", I can see: [color=blue]Intel(R) Pentium(R) 4 CPU 1,90GHz[/color] 
3. "Sound, video and game controllers", I can see: [color=blue]Avance AC'97 audio for VIA (R) Audio Controller[/color]
4. "System devices", I can see: [color=blue]VIA PCI to ISA Bridge[/color]
5. "Universal Serial Bus controllers", I can see [color=blue]VIA Rev 5 or later USB Universal Host Controller[/color]

The above looks like that the maker could be "[color=blue]VIA[/color]"...
But I searched their Site & could NOT find the Mobo listed...
So, I thought that the "[color=blue]VIA[/color]" part could refer to the Maker of the Chips, but NOT the true maker of the Mobo...
Hmmmm.....

Since I could NOT find much, I decided to use the program "[color=blue]Belarc Advisor[/color]" hoping to get more info out of it...

And got the following...
Under:

1. "System Model", I can see: [color=blue]infoquest P4X266-8233[/color]
(Note: "infoquest" is the company in Greece that sells computers - don't be mislead by that word - just disregard that word...)

2. "Main Circuit Board", I can see:
a. "Board": [color=blue]P4X266-8233[/color]
(Note: I think the "8233" part refers to the VIA VT8233 chip set)
b. "Bus clock": [color=blue]100 megahertz[/color]
c. "BIOS": [color=blue]Award Software International, Inc. 6.00 PG 10/29/2001[/color]

3. "Memory Modules", I can see:
a. 512 Megabytes Installed Memory
b. Slot 'A0' has 256MB
c. Slot 'A1' has 512MB (this is strange: if b+c=768MB, why does "a" state that Installed Memory is 512MB?)
d. Slot 'A2' is Empty

4. "Display", I can see: [color=blue]NVIDIA RIVA TNT2 Model64/Model64Pro [Display Adapter][/color]
(this is a separate/not embedded to Mobo, non-PCI VGA Card - not sure but I thing it is AGP connection... I guess I need a manual for this one too!) 

5. "Processor", I can see: [color=blue]1,9 gigahertz Intel Pentium 4
8 kilobyte primary memory cache
256 kilobyte secondary memory cache[/color]

The guy I bought this from, claims that the Mobo is the: [color=blue]Apollo P4X266[/color].
But I can't find any Motherboard created by Apollo...
A search in Yahoo gives me:
[color=blue]Via Apollo P4X266 North Bridge and the VT8233 South Bridge[/color]
So the chipsets used could be these, but the Mobo?

_Questions_:
1. What is the Model of this Mobo? (is it: P4X266-8233?)
2. Who is the maker? (VIA?, Chaintech?, etc etc)
3. Where are its specs/**Manual** to see what the Mobo supports/can do?

_Why do I care_:
1. Cause I might want to add some more Memory...
2. Cause I want to know the Sochet for the CPU - is it [color=blue]s478[/color]?
3. In the end I might decide to buy a diff Mobo & dump this... (so I want to keep the CPU & Memory to put in the new Mobo -> I need to know what Mobo I have!)

BTW, to help you help me, this is a snaphot of how my Mobo looks like:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/SnapshotofmynewMobo.jpg[/IMG]

Note: **Do NOT be mislead by the Model Name of the Mobo in the Picture!!!**
My Mobo has NO name on it...
Basically I borrowed _that_ Mobo's snapshot, and I moved all chips around, icluding IDE channels, transistors (or how do you call these things that look like batteries...), power button switches, etc etc - almost everything...
I mean this looks "almost" (99% like) my Mobo!
Even the positions of stuff are the same!!!
The Mobo says on it: [color=blue]MADE IN TAIWAN[/color]
And that sticker with the Bar Code & the number under it...
The actual number in mine is "[color=blue]1B006800758[/color]". 
Does that help a bit?

Thanks.

P.S.1> If you want me to check anything on the Mobo (using the flashlight) please tell me...
P.S.2> This is a true Treasure Hunting, isn't it? :)

---

### Post by xmastree on 2007-02-03
When you first turn on the PC, before even the video BIOS thing shows up, there will be a number along the bottom edge of the screen.
This article
[http://www.motherboards.org/articles/tech-planations/13_1.html](http://www.motherboards.org/articles/tech-planations/13_1.html)
tells you how to identify it from that number.

AWARD

    * 2A5LE**F0**9C-00
    * Characters 1-5 ID the Chipset, in this case 2A5LE is the Via 597VP3 chipset.
    * Characters 6-7 ID the manufacturer, in this case F0 is FIC.
    * The bold numbers are the portion that identify the manufacturer

Stick that number in [here](http://www.motherboards.org/tools/moboidtools.html) and see what comes up.

---

### Post by Omnios on 2007-02-03
This help any?

[http://www.google.ca/search?q=P4X266+VL33-s+motherboard&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.ca/search?q=P4X266+VL33-s+motherboard&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a)

---

