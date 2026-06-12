---
title: "No sound"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by sneffers on 2007-03-22
Hi, I am really new to ubuntu and linux and everything and I need some help. I installed ubuntu edgy eft and had some problems installing it. I had to install it like 6 times before it actually installed. But then it like crashed on  me or something so I installed dapper drake which worked no problem. Except i had one problem I had with  edgy: [COLOR="Red"]THERE IS NO SOUND!!!!![/COLOR] When I start up my laptop I hear the beep, and when I can't like click somewhere or something i hear that beep but there is no sound for anything else like when you start it up. I also had an error when I would run it off the live cd that said that my sound card is busy or there is no sound card. I think it said my sound card was Yamaha OPL3-sa and also i think it said something about OPL3-sa2. If anybody knows how to fix this PLEASE TELL ME!!! thank you.

---

### Post by karthikp on 2007-03-22
I've seen something similar happen to a friend of mine. Just open a terminal and type alsamixer. This opens a text-based system volume indicator. I believe right-left lets you choose channels and up-down increases or decreases the volume. Play around there and increase the volume there. Sometimes, it defaults to no volume, I guess.

As a bonus, you could also get rid of that beep (which I think is probably your PC speaker...) by muting the PC speaker

---

### Post by sneffers on 2007-03-22
I get an error when I put that in. It says the following: alsamixer: function snd_ctl_open failed for default: No such device
  Also when I click on the sound volume icon it says there is no device to control or it is busy and I might not have the right gstreamer plugin installed. I went to synaptic package manager and ther wer like hundreds of gstreamer things. well not really hundreds but a lot.

---

### Post by j002 on 2007-03-23
You need to install the sound driver.

The instructions are in the "excerpt from Ubuntu book" under Help.  You need to scroll down about 2/3rds down the document to find the right bit.

You need to add script to the file given (X11 -something I think, or was that xorg ?, that's a capital X) using gedit, like :

>gedit /path/filename


then type in new line

snd-es18xx

not that though, thats for an ESS soundcard.  Then save the file.

---

### Post by sneffers on 2007-03-24
That sounds like jibberish to me. Please explain better. I am a complete newbee. I understand I have to put those codes into terminal but I don't know what to put in for some of them. And I didn't get the first part either about the ubuntu book under help. I tried installing a driver once from the web and found the one I needed but I couldn't download it.

---

### Post by sameoldude on 2007-03-24
> **j002 said:**
> You need to install the sound driver.

The instructions are in the "excerpt from Ubuntu book" under Help.  You need to scroll down about 2/3rds down the document to find the right bit.

You need to add script to the file given (X11 -something I think, or was that xorg ?, that's a capital X) using gedit, like :

>gedit /path/filename


then type in new line

snd-es18xx

not that though, thats for an ESS soundcard.  Then save the file.


nope, not enough

---

