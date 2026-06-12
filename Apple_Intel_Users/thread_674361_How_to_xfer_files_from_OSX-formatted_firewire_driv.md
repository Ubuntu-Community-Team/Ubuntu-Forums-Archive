---
title: "How to xfer files from OSX-formatted firewire drive to internal HD?"
date: 2008-01-21
forum: Apple Intel Users
---

### Post by neatokino on 2008-01-21
I've got a 500GB firewire drive formatted for Mac OSX (extended journalled) which contains files of all my music CDs, mostly in apple lossless format. 

I can't figure out how to transfer those files to the internal HD of my linux computer (Gutsy on a Dell Pentium 4 machine).  When I try to transfer,  I'm told that I don't have permission to do the file transfer.  If I log onto nautilus with gksudo, I still have the same problem.  

Is there a way to mount the external firewire drive so that I can copy some of my music onto the internal drive of the linux computer?  And if I can do that, how do I make sure that the external disk will still be readable on my Mac?

Oh, and while we're at it, is there a codec that allows me to play Apple Lossless files in Ubuntu?

Thanks in advance for any help on this.

---

### Post by cyberdork33 on 2008-01-21
Mounting a HFS+ drive should be quite possible (though maybe without write priviledges unless you disable journaling). Permissions are an issue, but accessing via root has always worked for me... (and others I have seen). can you just try copying a file via the terminal as root? see what the error message might be there.

---

### Post by neatokino on 2008-01-22
Thanks for your help.  It turns out  I am able to transfer files in root, at least some of them.  

But as far as I can tell, there is no codec to play apple lossless files in ubuntu, so my biggest issue is taking the time to convert my music from apple lossless to flac!

---

### Post by cyberdork33 on 2008-01-22
> **neatokino said:**
> Thanks for your help.  It turns out  I am able to transfer files in root, at least some of them.  

But as far as I can tell, there is no codec to play apple lossless files in ubuntu, so my biggest issue is taking the time to convert my music from apple lossless to flac!


ALAC is a closed format. There is no information on decoding it, thus it is up to people to reverse engineer it to write a decoder. Apparently, someone has written something, but I wouldn't expect it to be the best thing you have ever used since it seems to be undeveloped (last updated September 30, 2006). Additionally, I think this is just a decoder, not a codec.

[http://craz.net/programs/itunes/alac.html](http://craz.net/programs/itunes/alac.html)

---

