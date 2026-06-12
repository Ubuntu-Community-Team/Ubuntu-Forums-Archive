---
title: "Questions: TV application - DVD subtitles"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by hrisk on 2008-02-20
Hello
I am using Ubuntu 7.10 for couple days now and i would like your help in these questions:

1) I have a Hauppauge PCI WinTV-radio card (BT878 chip set). Do i need to install the   appropriate packages first and then look for a TV application? 
if not which is the best TV application for watching-recording TV and which for listening radio?

2) I tried to watch a DVD on totem player but i didn't see any option for subtitles in the program menu (it show ->"empty"). The same problem with SMPlayer. It may sound silly to you but how can i make them appear? How can i make the SMPlayer the default player for DVD's?

Thanks in advance!

---

### Post by rvm4000 on 2008-02-20
> **hrisk said:**
> 2) I tried to watch a DVD on totem player but i didn't see any option for subtitles in the program menu (it show ->"empty"). The same problem with SMPlayer. It may sound silly to you but how can i make them appear? How can i make the SMPlayer the default player for DVD's?

If smplayer doesn't show any subtitles in the menu is because it wasn't able to detect them. 
Could you copy the mplayer log (Options->View logs) after trying to play a DVD?

---

### Post by hrisk on 2008-02-21
I attached a log file from the smplayer.

The VIDEO_TS folder in DVD has only files like these: VTS_xx_x-.BUP, VTS_xx_x.VOB, VTS_xx_x.IFO.

Does the smplayer wants a specific format for subtitles or i am doing something wrong?

---

### Post by rvm4000 on 2008-02-21
It seems you're opening directly the file VTS_01_1.VOB. I think this is not the right way to play a DVD.

First go to Preferences -> Drives and be sure you have selected the DVD device (usually /dev/dvd), and then in the Open menu select "DVD from drive".

---

### Post by hrisk on 2008-02-22
Problem solved!
I have a DVD player and a DVD recorder in my PC (drives D: and E: in window$)
For a reason beyond my knowledge :-k , the subtitles are shown only if the disc is played in DVD recorder.
Thanks for your help!

---

