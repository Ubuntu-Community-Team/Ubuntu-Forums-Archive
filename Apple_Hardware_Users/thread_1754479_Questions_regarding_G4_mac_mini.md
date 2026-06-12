---
title: "Questions regarding G4 mac mini"
date: 2011-05-10
forum: Apple Hardware Users
---

### Post by mrwooster on 2011-05-10
Having tried to get my 6yo PC to work with ubuntu, I am considering getting an old mac mini instead (looks like the old PC has motherboard issues).

The main use will be to server a VPN for my home network and a NAS for some of my media.

I am thinking of getting a Mac Mini G4 off ebay.  My questions are:

1) (No 100% ubuntu related) How easy is it to upgrade the HDD, and what sort of HDD does it take (PATA?)

2) Will it work with Wake on Lan?

3) Can I install ubuntu form a USB key?

4) Any other things I should be aware of about using a PPC system?  

Thanks

---

### Post by jmtd on 2012-05-12
1. - it takes a PATA / ATA / IDE HDD. The one I'm playing with has 5400rpm 80G which is not much.

2. I haven't got WOL to work yet. Part of the puzzle is getting a WOL packet across wifi in my case. I haven't tried from Ethernet.

3. Yes.

4. there are just lots of little gotchas. Different bootloader from PCs; slightly different partitioning requirements (the installer should handle these); suspend-to-ram is more difficult due to problems with the video card (a pain for me because I'm using it headless anyway).

It's still a very quiet, easy-to-stash machine. The fact it has built-in WIFI means you can hide it anywhere in your home within reach of a power socket.

---

