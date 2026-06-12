---
title: "M-Audio Keystation"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Hellcom on 2007-05-01
I'm having difficulty getting my M-Audio Keystation 49e usb-midi controller working under 7.04 as there is no documentation (that I can find) about how to set it up. So... help me pretty please? :)

---

### Post by compiledkernel on 2007-05-01
Im assuming you have to build the driver from [http://www.opensound.com/](http://www.opensound.com/) 

on m-audio's site -- 

> Q: Is there a Linux driver for my M-Audio MIDI interface- or MIDI Keyboard?

A: M-Audio uses a 3rd Party Vendor for Unix support. 4Front Technologies develops and supports UNIX drivers for M-Audio products. The software is available for free evaluation and non-profit use but 4Front charges a fee for technical support and commercial use. 

[http://www.opensound.com/press/2007/OSSv4.txt](http://www.opensound.com/press/2007/OSSv4.txt)

---

### Post by Hellcom on 2007-05-02
Well I couldn't find anything there. The only linux drivers I could find dealt with m-audio sound cards, and not the usb-midi keyboard controllers.

---

### Post by ubnewbie2 on 2007-05-02
This is one of the reasons I am forced to run Windows (2K) on the laptop I use for music work :(

---

### Post by GMaq on 2007-05-09
Hi,
     Feisty has built-in support for the new Keystation es models. Plug in your USB port, open a terminal and type "lsusb" you should see a list of USB devices and the Keystation will appear as "evolution" (I can't remember the exact name). Then you need to download qjackctl from the repositories and use it as an interface to whatever software you are using, I use my Keystation with Qsynth and it works very well.

---

### Post by shanepardue on 2007-07-13
> **GMaq said:**
> Hi,
     Feisty has built-in support for the new Keystation es models. Plug in your USB port, open a terminal and type "lsusb" you should see a list of USB devices and the Keystation will appear as "evolution" (I can't remember the exact name). Then you need to download qjackctl from the repositories and use it as an interface to whatever software you are using, I use my Keystation with Qsynth and it works very well.
I'm using a similar M-audio midi controller, but can't figure out how 
to use jack and qsynth...Could you please explain that process a little? 

I'd really appreciate it!!

---

### Post by mikelucasiscool on 2007-07-18
Ok first of let me say this, i am a newb to linux i've had it about 2 weeks and i'm in school full time so i don't have as much time to play with it as i would like.

I bought this M-Audio Keystation 49e usb keyboard, thinking there would be some simple software for windows or linux (as i don't have a mac)

The mac software that comes built into mac (that was demoed with the keyboard at the store) was great i wanted something like that
music garage i think it was called? or garage band? something like that anyway...

I can't find ANY software to make it just play simple notes and possible record them in different layers so i can make some kind of songs if i want.

No matter what software i try to use, i have yet with anything other than fruity loops in windows... been able to make this thing create sounds (very angry and frustrated)
and fruity loops won't record what i play... i can just play it, well at least i can't figure out how to get it to record...

I tried Beast, I tried Jack, i can't get either of them to work both have errors, and i tried everything i could find although i have some newer version of beast to try i don't really know the coding for making source into programs :S anyway...

sorry for ranting... to the point

Does anyone know of a SIMPLE program for linux that I can figure out how to make my piano make sounds on my computer ????

Please help.

- T4ct1cs

ps i would like to mention that i HATED the software that came with it for windows as it was COMPLICATED in the EXTREME and the help files where just wrong when it came to setting it up as an input device none of the screens it said would show up did even when i followed the instructions :S.

pps my summary is this If you bought this thing for a mac You are set to go... if not well then this company could give two hoots about you... they already got your money, and they are "laughing strait to the bank with it....ha, ha,hahahaha!" - some song

---

