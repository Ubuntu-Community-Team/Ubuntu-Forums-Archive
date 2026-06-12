---
title: "Need help with VNCVIEWER"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2007-03-11
Hi

I got a friend with Ubuntu 6.10 (I use that too) and we want to try out the Vncviewer-command. He types in the terminal:

vncviewer MY-IP-ADRESS:0

Then I got a pop up message to allow or deny him. I click yes and it works.

But when I try to do the same, nothing happens. I just got this output:

> wikzo@wikzo-laptop:~$ vncviewer his-ip-adress:0
VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection timed out
Unable to connect to VNC server
wikzo@wikzo-laptop:~$ 


(I haven't wrote his IP correct in this quote)

Why can't I acess his computer when he can acess mine?
In the options menu he has set it to allow other users and he has no password.

My friends output:

> anders@anders-desktop:~$ vncviewer my-ip-adress:0

VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48

Copyright (C) 2002-2003 RealVNC Ltd.

Copyright (C) 1994-2000 AT&T Laboratories Cambridge.

See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

VNC server supports protocol version 3.7 (viewer 3.3)

No authentication needed

Desktop name "LibVNCServer"

Connected to VNC server, using protocol version 3.3

VNC server default format:

  32 bits per pixel.

  Least significant byte first in each pixel.

  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0

Using default colormap and visual, TrueColor, depth 24.

Got 256 exact BGR233 colours out of 256

Using BGR233 pixel format:

  8 bits per pixel.

  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6

Using shared memory PutImage

ShmCleanup called

I have tried this with two friends; I can't acess othes computers. What is wrong?

---

### Post by Delvien on 2007-03-11
I think they need to change their remote desktop settings to allow other users to connect, im at work so im not sure where the path is it should be under System>Admin

---

### Post by Wikzo on 2007-03-11
I have done that, so no, it isn't the problem :\

---

### Post by morequarky on 2007-03-15
Just checking, could it be that your friend is behind a switch that isn't configured to let you through to his cpu?

---

### Post by Wikzo on 2007-03-16
We really don't know. Have tried with 3 friends now, and it won't work ... straaange.

---

