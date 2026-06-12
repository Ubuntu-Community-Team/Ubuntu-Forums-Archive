---
title: "Macbook unmatched memory pair = slow graphics."
date: 2008-10-22
forum: Apple Hardware Users
---

### Post by volanin on 2008-10-22
Today, I intended on upgrading my original macbook 2,1 setup from 1GB of RAM memory (2x512MB) to the full 4GB of RAM memory (2x2GB). I know that the macbook cannot fully address the 4GB, but the maximum addressable ~3.3GB of RAM memory is good enough for me.

Well, one of the new memory chips was faulty and didn't even work. I am waiting for the store to send me a replacement via mail, and it should arrive by friday, so I installed one of the original 512MB chips and the new 2GB chip togheter for a total of 2.5GB RAM memory.

The patched [memtest.bin]("http://matt.ucc.asn.au/memtest/") reported 2.5GB Memory Dual Channel (Unmatched), and the tests didn't report anything wrong.


Ok, now for the problem!


When I booted Hardy, I realized that the desktop effects were a little more sluggish than usual. Operations like maximizing the windows and scrolling pages in Firefox were noticeably sluggish. Abobe Reader was unusable. Glxgears didn't change at all.

After trying this setup for a couple hours, I decided to remove the 512MB chip, leaving only the new 2GB chip even if that would mean Single Channel, because I was worried that it could be faulty as well, so I wanted to test how it performed by itself. But after that, everything returned to normal.


I am running 2GB Single Channel now, and everything is ok.
I am just leaving the warning here, because there might be some people here that use unmatched memory pairs, and it *might* reduce your Ubuntu Desktop Effects flowness and usability.

For information, I use the i810 driver in X.
See ya!
:)

---

### Post by volanin on 2008-10-24
Just a follow up...
The replacement 2GB memory chip arrived today!
After installation, I had the following system information:

[LIST]
[*]Linux 32-bit and 64-bit: 2.96GB RAM
[*]Windows XP 32-bit: 2.96GB RAM
[*]MacOSX 10.4: 4.0GB RAM *(Apple, you liar!)*
[/LIST]

The patched memtest.bin reported 3.0GB Memory Dual Channel (Interleaved), and the tests didn't report anything wrong.
Graphics are again very fast, with smooth Desktop Effects using the i810 driver in X.

That's it.
If you are considering expanding your Macbook memory, a viable option would be to buy a 2GB chip + 1GB chip, but you won't get dual-channel, and you *might* have the slow graphic problems I had. Go to a store and test your system with the unmatched pair first!

:)

---

### Post by rickbsgu on 2008-10-25
Interesting.  I noted that with my Macbook (white 2.0ghz, 4gb mem, 6.04 amd64), when I first boot it up, it runs lickety split, but after anywhere from a couple of hours to a day, it gets real sluggish, as you report, here.

I do a 'top' and I don't see anything out of the ordinary - certainly nothing whacking the CPU or memory that would be out of the ordinary.

I suspect it's either graphics overloading from an opengl screen-saver, or the ath9 network driver is doing something weird.  Those are my prime suspects, at the moemnt.  I have to try to disable either and see if it improves.

---

