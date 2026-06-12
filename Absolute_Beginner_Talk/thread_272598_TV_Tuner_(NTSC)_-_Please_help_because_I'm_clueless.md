---
title: "TV Tuner (NTSC) - Please help because I'm clueless!"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-10-06
I Have a [nVIDIA GeForce FX5600/XT]("http://www.chaintechusa.com/tw/eng/product_spec.asp?MPSNo=14&PISNo=197") and i need to know how to use the tv tuner (NTSC) with linux.  I have no idea how to do this so please be detailed if you can.

---

### Post by fragos on 2006-10-06
I don't believe that the FX5600 has a TV tuner.  If you want to watch TV on your PC you need to buy a card with a tuner on it.  For example WinTV-GO is the one that I use.  Some video cards have TVout via an S-video connector.  Its purpose is to display on the TV screen as if it was a monitor.

---

### Post by insub2 on 2006-10-07
No.  It does.  One of the reasons I got it a few years ago.  It worked in WinXP when I was living with my parents and had cable.  Now I'm in linux.


look under Function for "TV In (CATV In connector, NTSC or PAL)"

i have the NTSC.

---

### Post by firenurse4 on 2006-10-07
What proram are you trying to use for the TV?  I had the best results using tvtime but there are other programs.

---

### Post by insub2 on 2006-10-08
> **firenurse4 said:**
> What proram are you trying to use for the TV?  I had the best results using tvtime but there are other programs.

i have tvtime installed.  but the thing is i have no signal, no video source, and no such file or directory/cannot open capture device /dev/video0.

any recomendations?

---

### Post by fragos on 2006-10-08
It sounds like no driver has been loaded.  Perhaps Linux doesn't see your TV chip.  Another posibility is that it sees the chip but doesn't recognize the tuner.  Try the following on the command line and report the results.

dmesg|grep tuner
dmesg|grep tv

---

### Post by insub2 on 2006-10-08
> **fragos said:**
> It sounds like no driver has been loaded.  Perhaps Linux doesn't see your TV chip.  Another posibility is that it sees the chip but doesn't recognize the tuner.  Try the following on the command line and report the results.

dmesg|grep tuner
dmesg|grep tv


neither of them return anything.

---

