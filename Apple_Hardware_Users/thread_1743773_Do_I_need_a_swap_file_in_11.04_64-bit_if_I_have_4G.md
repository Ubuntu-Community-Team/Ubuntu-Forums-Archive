---
title: "Do I need a swap file in 11.04 64-bit if I have 4GB RAM?"
date: 2011-04-29
forum: Apple Hardware Users
---

### Post by ImAtHome on 2011-04-29
I've got a Macbook Pro 5,5.  I'm triple-booting Snow Leopard, Win7 Pro, and Natty with rEFIt.  I only put in a 10GB partition to play with Linux and I didn't add a swap partition because I tried doing that before and I had trouble with my partition table.  I only have ~6GB free space.  

Should I put in a swap file or should I be fine?

Thanks in advance.

---

### Post by trollger on 2011-04-29
If I where you I would add one becuase I know how to and there is no reason not to.You have a triboot going so it is hard to say what would be 'right' or 'wrong', it depends on your partion layout. Messing up windows 7 or your mac is deffinitly not worth adding a linux swap. Really its up to you but as far as Wether or not you *need *it is unlikely. You should be fine but be warned if you use more than 4 GIB of ram at a time your system will have aconsiderable perfomance drop.

---

### Post by handy on 2011-04-30
I watched the RAM usage of my iMac that had 1GB of RAM installed (using htop). After seeing that I didn't need a /swap I deleted it. 

That was some years ago.

Unless you are using Photoshop, or doing some other extremely graphics intensive work with 3D rendering or movie editing, I wouldn't waste the any space using /swap.

Modern computer hardware has all but made /swap redundant.

---

