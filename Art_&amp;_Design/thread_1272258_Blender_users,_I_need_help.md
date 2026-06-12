---
title: "Blender users, I need help"
date: 2009-09-21
forum: Art &amp; Design
---

### Post by razor180 on 2009-09-21
I'm posting here because I'm more likely to get a reply on here than general help (since that forum is pretty much full)

I use blender, but I didn't get the 2.48 version off of add/remove programs (I got blender using a deb package, not add/remove programs, just because add/remove programs didn't have the latest version of blender) and I was rendering something in blender, I know for sure that it was done before the power surged and went out (a storm happened about an hour before I got home)

okay, I started rendering something last night, and I checked at about 7 this morning and it was still going (slow computer) but it was nearly done (probably only had a couple of hours or less to go) so about an hour before I got home a storm broke out (HUGE STORM) and when I got home, my computer was off (I didn't save the render because it finished rendering while I was away from home). Now I know once it's done, it usually saves it in some sort of buffer (that way when you press f11, it can recall it), does anyone know where I might find that?

also, on a secondary note, where would I find blender's "program files" (I know it's not called program files, but the ubuntu equivalent of them) so I can put in python exporter scripts for yafaray and luxrender in it

---

### Post by hessiess on 2009-09-22
If you have anything saved, it will eather be in /tmp which is wiped every reboot or in .blender in your home dir, press ctrl+h to show hidden files.

As it was taking so long I assume you were rendering an animation, if so in the future render as a PNG or EXR sequance, then combine it into a video after. this prevents you loosing everything.

---

### Post by razor180 on 2009-09-22
no, I wasn't rendering an animation

it was a still image, I just have a computer that wasn't even remotely created for anything like this (it's an emachines). but I figured I had the time, so I had my AO settings on 15 samples and let it render through the night and day. the computer has 2gb of RAM in it (that's the max the motherboard will hold) and the procesor is an AMD athlon 3800+ single core clocked at 2.4ghz (the computer was only 300 dollars after shipping and I needed a cheap fix)

yes, I'm planning on upgrading, just don't have the money to buy the parts (I have my parts picked out and I"m planning on building a new computer, I just don't have the money to buy the parts yet)

---

### Post by hessiess on 2009-09-23
> 
AO settings on 15 samples.


Do you really need such a high sample count? generally I find around 8 to be optimal for stills.

---

### Post by dsavi on 2009-09-24
Press F10, and in the buttons window press the "Render buttons" button. Under the output header, there should be two folders. The one on the top is where the output of your renders goes.

In this example, the output folder is /tmp/.
[IMG]http://img17.imageshack.us/img17/5199/screenshot4kl.png[/IMG]

---

