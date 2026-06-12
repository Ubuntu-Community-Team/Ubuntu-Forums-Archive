---
title: "Problem with DVD burner/player"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by linuxneeewb on 2007-12-19
I have been having problems with my DVD burner/player. It cannot play DVD movies for some reason. I thought it was the DVD player itself, so I bought a new one but I still receive problems.

The error message that I receive is 
"An error occured could not be read from resource"

It will recognize the DVD movie that I put in the drive but refuses to play it and gives that error message. I have tried using VLC, totem and other players but they all give me problems.

Any and all help is appreciated. Thanks

:popcorn:

---

### Post by macogw on 2007-12-19
Is it an encrypted (ie. store-bought, not home-burned) DVD?  If it is, you need a decryptor for it (not included by default because of stupid US patent laws...on Windows you usually pay for it with the computer when you buy it or when you buy PowerDVD or whatever).  To get one, in Applications > Accessories > Terminal, copy & paste
```
gksu gedit /etc/apt/sources.list
```
and paste this on the last line> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
then run ```
sudo apt-get update && sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4
```
And you should be good to go

---

### Post by linuxneeewb on 2007-12-19
Thanks

---

### Post by tonymoloney on 2007-12-19
I was having the same problem and your solution worked for me also.
Many thanks and Merry Christmas.

---

### Post by Aizen13 on 2008-02-02
Also:

I still have Edgy on mine and can't seem to install Gutsy.  What if we have Edgy?  Can we still patch through on the code for Gutsy?  That would be great to know.

Cheers,
Aizen13

---

