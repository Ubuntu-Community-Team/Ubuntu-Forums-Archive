---
title: "Webcam"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Jokeaflorias on 2007-05-01
I have the Xbox 360 webcam from Microsoft that is plug and play on Windows. When I plug it in, Ubuntu doesn't detect it. What can I do to install it? Thanks in advance.

-Jokeaflorias

---

### Post by chemtut on 2007-05-02
get camstream from synaptic
it detected both my webcams---one cheap,the other expensive
give it a go!

---

### Post by kvonb on 2007-05-02
Well, being a microsoft product, you have more chance of growing a third eye than getting support for Linux with that thing!

What you can do is open a terminal and type this:

```
lsusb
```

That will give you a device number as in this example from my computer:

```
kev@kev:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0c45:60c0 Microdia 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
kev@kev:~$ 
```

OK, so I know it's not going to be the mouse, so it must be the 0c45:60c0 Microdia which is the important bit.

Search the forums and also google for the ID numberwhich in my case is:

```
0c45:60c0
```

...obviously put your own number in there :).

That will identify the chipset it uses, also look here to see if it is supported under Linux at all:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

