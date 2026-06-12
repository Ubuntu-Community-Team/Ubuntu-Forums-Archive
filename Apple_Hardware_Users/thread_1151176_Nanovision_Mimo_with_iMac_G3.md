---
title: "Nanovision Mimo with iMac G3"
date: 2009-05-06
forum: Apple Hardware Users
---

### Post by Boodlezoid on 2009-05-06
I have an iMac G3 that I have upgraded to the G4 standards. Though I have a MacBook Pro now, I don't have a lot of use for the iMac G4, so I want to turn it into a small server here at home for myself.

The last bit of software that I see that I can use for my iMac is the 6.06.02 LTS (Dapper Drake) for the Mac (PPC). Since I want to make a server out of it. I have yet to get my iMac to boot off of the CD to install the Server Software, but I was wondering if anyone knows of a program that I can install onto the Ubuntu Server Software that will allow me to use the Mimo as my main screen. 

Since I don't have a lot of desk space and I don't need a lot of screen just for a server, though a decent powered computer would be nice!

The other issue I have right now, is that the Mimo is said to only work for the different versions of Windows, and OS X. Does anyone have Ubuntu and a Mimo that they would happen to be able to test that on? 

If you have any info on any of this, you can also contact me on Twitter @Boodlezoid.
Thanks!

---

### Post by stream303 on 2009-05-07
For a server, a nice conservative 8.04.1 LTS can be found here:

[http://cdimage.ubuntu.com/ports/releases/8.04.1/release/](http://cdimage.ubuntu.com/ports/releases/8.04.1/release/)

I can't help you with mimo, but if you do decide to go with just a simple window manager to run a few xterms, it would be easy to do.  Check out this minimal ram install wiki that details how to get a small X environment running:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Howtoforge also has a nice series about "The Perfect Server - Ubuntu XXXX" which applies to ppc just as well as X86.

The server should be no sweat if all you need is a cli, although you *may* have to start up with

```
Linux nosplash
or
Linux nosplash video=ofonly
```
at the 2nd yaboot boot: prompt.

Be sure to burn that .iso image at a speed low enough for the G3/G4 cdrom drive to handle...

---

### Post by Boodlezoid on 2009-05-07
Thank you, I did not realize that 8.04.1 server had the PPC ability.

---

