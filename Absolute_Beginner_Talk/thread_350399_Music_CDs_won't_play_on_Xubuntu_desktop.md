---
title: "Music CDs won't play on Xubuntu desktop"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Brendantb on 2007-01-31
Hi, 

I have just installed Xubuntu (6.10/ Xfce 4.3.99.1) on the system in my signature.

CDs play automatically on the hardware using Windows, but when I attempt to play the CD on the Xubuntu destop there's no CD icon on the desktop, and /media/cdrom is empty. 

The computer is playing other sounds, beeps etc, normally. 

The sound card is detected when I "aplay -l" in the terminal.

Am I omitting doing something obvious?

---

### Post by Happy_Man on 2007-01-31
Well, I'm reasonably sure that CD's are in a restricted format, so xubuntu doesn't support them out of the box. If you download the plugins thru synaptic, however, that should remedy them. Just search for gstreamer and install gsteamer ffmpeg video plugin, gstreamer extra plugins, and cd player. That should take care of everything, plus now you can play mp3, mpeg, and just about anything else! enjoy!

---

### Post by Brendantb on 2007-01-31
Doh. 

Yeah, something obvious was right. 

Thanks for the quick reply.

---

### Post by Jorge32 on 2007-02-05
here comes a silly question:oops:, how to install gstreamer if all that shows up on synaptic are plug-ins, which option do i need to check?

---

### Post by Brendantb on 2007-02-07
Hi, Jorge32

I used synaptic to download and install the packages. 

You will find a list of the packages you need to install on the default web help pages set up on install, under Welcome to Xubuntu, Xubuntu desktop guide, 3. Common tasks: Get Multimedia Support. Highlight, and copy these. 

Go to Synaptic: under Applications, system, synaptic package manager. 

In Synaptic, click settings, repositories; this will open a Software Sources window. 

Check the two entries ending in Universe and Multiverse, and close window. 

Click search. In the find window, you can paste in the list of packages. After a few moments you will see the list in the left pane. 

I then had to search for each package separately. If there is a quicker way to do this, I would like to know it. Paste each item into the search field, and click search. Each search will throw up a short list of items. Right click on the ones you want, and click install.

When you have gone through the list, click on the apply button in the top toolbar. 

All the items should be installed automatically. 

It is a good idea to have a cpu monitor, like System Load Monitor in a panel, to check that something is happening, as if the mouse moves off the active window, the progress wheel disappears.

---

### Post by emry on 2007-03-03
Is there a logical rational reason why audio CD's (which are generaly simple wave files that play on pretty much any CD player made in the last decade or two) would be under restricted formats?

---

