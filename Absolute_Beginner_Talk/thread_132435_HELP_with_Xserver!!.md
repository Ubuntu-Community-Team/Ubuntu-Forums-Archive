---
title: "HELP with Xserver!!"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by Netisan on 2006-02-18
The last thing I had installed was kinda 3D ATI driver (my card is Radeon 7~). After a restart, I get (!) a simple graphical window which says that Xserver is misconfigured, and has an <OK> field to display a report. In a second the text login prompt appears over that window (making the window background and unaccesible). 
When I cope to press that <OK> I get some header of the above report saying to make sure I have the last version, and again the console pops above it. 
I know, the console is all I need. 
The problem is that I don't know what I need to check/change :(

---

### Post by linuxden on 2006-02-18
Hey,

You can do this as a quick way around...

Get to a terminal prompt, in theory after you see that red and blue window if you press enter you should get dropped to a shell...

Then type:

```
 sudo dpkg-reconfigure xserver-xorg 
```

if that doesnt work then:

```
 sudo apt-get remove x-window-system-core 
```

```
 sudo apt-get remove xorg-driver-fglrx 
```

```
 sudo apt-get remove xserver-xorg 
```

then :

```
 sudo apt-get install x-window-system-core 
```

```
 sudo apt-get install xorg-driver-fglrx 
```

```
 sudo apt-get install xserver-xorg 
```

in theory that should work...

---

### Post by Netisan on 2006-02-19
Thank you very much, ubuntulifestyle!
What happened? This command ** sudo dpkg-reconfigure xserver-xorg ** fixed the problem. I don't know how. 
I wrote down the next steps in case I need them in future.
Cheers!

---

### Post by linuxden on 2006-02-19
No worries Netisan...

Am glad you got it fixed, that is a scary screen the blue and red one....

lol

good luck...

---

