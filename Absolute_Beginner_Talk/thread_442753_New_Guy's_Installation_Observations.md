---
title: "New Guy's Installation Observations"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by raylat2002 on 2007-05-13
Hi,
I recently was given an old Dell Latitude C600 laptop--no sound, no mouse pad, no little joystick, and only a 10 gig hard drive. I had tried a Knoppix live version briefly on my desktop and this "new" Dell looked like a good opportunity to try Linux in more depth.

I installed Ubuntu 6.06 from the CD. Things went very smoothly. Ubuntu recognized my wireless LAN and mouse but the video display was very messed up. This is apparently a common problem with the ATI Rage Mobility 4 graphics set. 

I literally just fooled around with the FN keys and an external LCD and stumbled upon a combination of FN crt/lce keystrokes that brought the external monitor up in a useable mode.

Next I looked for Ubuntu updates and found that 7.04 was out but I had to upgrade to 6.10 first. This took some poking around the Ubuntu site but I did successfully download 6.10 and the 7.04, This didn't solve the display problem, though.

I picked up a copy of "Beginning Ubuntu Linux" by Keir Thomas. Turns out it has a section in Chapter 6 specifically on the graphical display problem. Followed the instructions, learned a little about the command line and terminal functions, and after several iterations of Mr. Thomas' instructions to hit the right display resolution and refresh rate now have the graphical display coming up directly upon booting.

Installed Firestarter using Mr. Thomas' guidance and then Grisoft's AVG anti-virus. Understand the arguments that neither may be necessary but going through the installations helped me learn a little more about the command line. AVG won't let me update from the GUI but info in Grisoft's help file told me how to do the updates from the terminal.

Can't get Java to work properly with either Opera or Firefox. I'm stuck on instructions that tell me to "establish a symbolic link" somewhere. Got some research to do on this one looks like. Got Java installed--just can't get it hooked up.

It's been an interesting experience so far. One thing I've found is that the answers to my questions are out there; either in Mr. Thomas' book, in Ubuntu's online help, vendors FAQs, or the forums.

Regards to the Ubuntu community.

raylat2002

---

### Post by Nekiruhs on 2007-05-13
Symbolic links are just like shortcuts in windows. Open a terminal and type
```
ln -s /path/to/file.etc /path/to/link
```

---

