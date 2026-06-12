---
title: "enabling DVD operation in 7.04"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by snakra on 2007-07-29
Hello,

I've had a look at the thread from timberdc but having only just started the move from Windows to Ubuntu I confess to being a bit in fear of the command line - I will get more comfortable but need more time!

In the meantime is there any other way to get the required codecs etc to enable DVD operation?

I've tried easyubuntu and some progress was made in that using vlc the dvd started and the menu page of the film appeared along with background sound.  However when clicked 'play' it refused to go.  Tried again to play the dvd without menu and I got sound without picture.

If I use movie player the Totem player still give the mesage about needing plug ins.

Can any body help - without using the command line.

If I have to use the command line processs then instructions in very plain and infant language would help!

Thanks in anticipation

SN

---

### Post by ron999 on 2007-07-29
Hi
VLC should play a DVD without problems. Just make sure you are using it correctly. This is how to do it:-
 
Put the disc in the drive.
Start VLC.
Then
File > Open disc > DVD(menus) > OK

---

### Post by AlexenderReez on 2007-07-29
hm..if you want to use Mplayer ,you need manually set --> open Mplayer ,right click ,preference --> video output xv xv/x11 ,open removable drviers and media preference <-- system menu --->multimedia --> vdeo disc ---> put
> mplayer %m

or gmplayer,just install it..it will set automatically for you:)

make sure you have all codec for playing the file:)

---

### Post by az on 2007-07-29
7.04 has a new mechanism which helps you install these codecs.  If you want to do it by hand, see here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by sailor2001 on 2007-07-29
in synaptics;  win32 codecs

---

