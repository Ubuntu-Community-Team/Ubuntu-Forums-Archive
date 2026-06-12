---
title: "SSH + VNC question"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-12-31
I can connect to my ubuntu server with Putty from windows machines, but how do i do the same from another ubuntu machine?

---

### Post by aJayRoo on 2007-12-31
Its simple, the ssh application comes installed with Ubuntu. Just open up a terminal and type:
```
ssh username@machine
```
And if you want to forward the display so that you are able to use graphical apps then you can use the 'X' switch to do so:
```
ssh -X username@machine
```
From there on it should be exactly the same as it was with putty. Hope that helps.

---

### Post by Steveway on 2007-12-31
Also, there is putty for Linux, too.
Just open Synaptic and search for it.

---

### Post by aJayRoo on 2007-12-31
Sure, if you need any of the advanced features like changing settings mid-session then putty might be a good idea. I just tried out putty on linux and noticed it won't allow me to specify the server as username@machine, I can only specify the machine and then have to enter my username once the connection is made. I'm sure this was not how the Windows version behaved, perhaps its just a problem at my end.

I prefer to use ssh from the command line, if you are not using the advanced features of putty the I can recommend this method. I connect to a few different servers for work on a daily basis and have set up custom launchers for each so that one click of a shortcut initiates an ssh session. If you wanted to set this up it is very easy, just create a custom launcher and set its command to (if you are using Gnome Terminal):
```
gnome-terminal -x ssh -X username@machine
```
This will start a gnome-terminal with an ssh session to the machine specified rather than starting your local shell. The same can be done with other terminal emulators too, this is just an example.

---

### Post by markyb86 on 2007-12-31
what would the equivilant of this be in linux? using ssh

```
putty -D 8080 -P 443 -ssh 10.10.10.10 (not really the ip)
```

---

### Post by aJayRoo on 2007-12-31
Very similar:
```
ssh -D 8080 -p 443 10.10.10.10
```
Try looking at the manpages for putty and ssh, this is where I got this from! I think a lot of the switches are similar.

---

### Post by dgrafix on 2008-01-01
thanks, i can open the ssh connection now and log in as i could with putty but when i try and VNC localhost:0 to it like i do when using windows, it tries to control the PC i am on rather than the remote one.

---

