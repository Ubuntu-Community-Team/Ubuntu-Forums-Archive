---
title: "Unable to upgrade to 6.10 from 6.06"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by jwb3vs on 2007-03-05
Hi,

I have tried several times to upgrade from 6.06 to 6.10, without success.

I have an installation of 6.06 which has worked flawlessly for me for about a year.  I recently tried $ gksu "update-manager -c" to upgrade that installation to 6.10.

The upgrade seemed to go fine, but upon rebooting, the PC kept cycling through the login screen.  I supplied my user id and password from the 6.06 install, with no luck.  I hit 'enter' on the user ubuntu prompt, same problem.

Then I tried installing from CD (having previously downloaded and burned the 6.10 ISO), and obtained the same result the first time.  The second time I tried this, I got an error partway through the install (sorry, I don't recall the error exactly, but it was a problem reading the CD.)

I have since checked the checksum on the original ISO download, and it's fine.  I will check the CD itself when I get home today, though that seems a forlorn hope, since the CD installation went all the way to reboot the first time.

So I have done a clean reinstall of 6.06, and again, it works flawlessly.

I'd sure like to upgrade; anyone out there experience the same problem, or have any ideas?  So far I have found nothing similar in your forums, but they are fairly extensive, so that will take a bit of time.

Thanks, John (jwb3vs)

---

### Post by housam on 2007-03-05
try to reburn the 6.10 iso with the slowest speed i.e. 4x or 2x.

---

### Post by jwb3vs on 2007-03-05
Gonna check the first CD first, but yeah, good suggestion.  I should mention that this is all on an older 'generic PC, 400 MHz MMX with 1 Gb RAM...

---

### Post by igknighted on 2007-03-05
Haha, thats a great combination of proc/ram.  It is possible that some support for your older mobo is not included in the Ubuntu compiles of the newer kernels, though I doubt that.  Did you include all boot options you used before?

---

