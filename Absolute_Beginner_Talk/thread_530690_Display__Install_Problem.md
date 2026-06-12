---
title: "Display / Install Problem"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by DVisions on 2007-08-20
I've been trying to get into the open source scene as it seems to fit my simple needs more effectively than other systems but everytime I muster up the courage to backup my data and go head first into an install I meet the same problem everytime.

First I was quite silly and thought I would go for the hardest and immerse myself into my computer with a gentoo install (a full install not the bare minimals) but it started up, recognized a few things then went to what I call the Blank Screen with Blinking Cursor (BSBC). Hours I tried everything, no results.

Few months later I pickup a Linux magazine with a poster and how to guide to install Fedora, I got past the splash screen then the BSBC came.

So a year now, I really really want to try this again, I ordered a LiveCD from the good folks here and recieved it last night. Excitedly I put the disk in, hit restart and am welcomed with a hurried blur of text, a splash screen... then the BSBC again.

I've searched other forums (when I had the problem before) but I've heard that the Ubuntu forums are paralleled to none in friendly help.

My specifications are a Gateway M680E Laptop, I think it may be a screen issue so I looked up my part:

17-inch WXGA+ LCD Display Panel [Part #QND1LDRZZZ00X1] 

or possibly a HDD issue so

 80-GB 4200-RPM Hard Drive [Part #QND1HDDZ5ZTAD1]  

Everything runs fine in XP Pro, just would like to make the transition. Any help would be greatly appreciated (hopefully it's something silly that's not even worthy of a post.)

Thanks again,

~DV

---

### Post by bluemech on 2007-08-20
You are booting it off the CD, correct? There should be a menu that allows you to boot into the GUI.

In any case, try typing
```
startx
```
into the prompt, see what happens.

---

### Post by DVisions on 2007-08-21
I've been fiddling with it for awhile now, the problem was the display adapters I believe. As far as to my earlier problem it wasn't a prompt, just a blank screen with a cursor blinking - couldn't type or anything.

I tried booting into Safe Graphics Mode which is set to 800 by 600 but the Ubuntu installation is too big to be run under that resolution (you can't see the next/back buttons and you can't resize the window smaller) but so after trying to install and enable my video card drivers through the safe graphics mode and meeting failure I started over and just hit F4 and selected 1024 x 768 16bit color. This worked.

However, after it installs it gets to about 70% or so and restarts, asks me to take out the disc and press return. Then it gives four lines of error. 

It says cannot SQUASHFA  read block (buncha hex nums/letters)
three more lines just with different hex values.

Every 15 or so seconds it tries again, different hex values, same error.

My guess is that the partitioning was messed up. I did a Guided on largest free block (I have an XP partition and a blank partition) so it gave a swap partition of 2000 and the rest in an ext3 mounted as "/" primary partition. I think that it has something to do with it being a primary and having windows as a primary. I think I read somewhere that there is a file that you can edit in windows that configs the MBR. 

Or it could be a bad disk now that I think about it (hence why it stops at 70% and gives a read error).

Any help towards the next step (I'm going to keep mining old posts for possible workarounds) would be greatly aprreciated.

Thanks
~ DV

---

### Post by DVisions on 2007-08-21
Okie dokie, I found my problem:

The liveCD I ordered (well, asked and recieved) was faulty. I did a "Check disk for errors" and it stopped at 70% (same place as my install would stop) and got this  "errors found in 476 files!". So next step is to burn one myself I guess.

Does anyone else have problems with a new liveCD straight from Ubuntu ?

---

