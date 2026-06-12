---
title: "Installation problems iBook G4"
date: 2009-01-21
forum: Apple Hardware Users
---

### Post by doctorbighands on 2009-01-21
I'm trying to install Ubuntu onto an iBook G4, but I'm getting stuck in the same spot. The installation gets to "Installing the Base System," up to about 6%, and it starts telling me that each consecutive file is corrupt.

At first, I thought it may have been a bad disc burn or a bad checksum. But after trying 3 different versions (8.10 server, 8.10 alternate, and 8.04 server) and having the same results with each one, I'm convinced it's something else. The md5sums all check out, and I've tried burning each onto several discs.

I have no idea what might be the issue here, but I know these files aren't corrupt and they should be installing without issue.

Any ideas are welcome!

---

### Post by mkvnmtr on 2009-01-21
I run 8.04 on a Ibook G4 and am about to try to update to 8.10 today. The things to check are do you have enough ram. Mine came with 256MB and that is probably not enough. The other is sometimes people have problems if they don't use a CD-R disk. I have no idea why but it is sometimes a problem.

---

### Post by doctorbighands on 2009-01-21
I'm using CD-R media, so no problem there.

Could a small amount of RAM be the cause of the Ubuntu install telling me that the files are corrupt? I've installed Ubu on a much older and slower G3 and never run into the problem I'm having now. I'll check the RAM, but I'm thinking this must be something else.

---

### Post by doctorbighands on 2009-01-22
No ideas? This one really has me stumped, and I'd like to overcome it if I can.

---

### Post by mkvnmtr on 2009-01-22
Since you like me seem to be good a burning disks google Ubuntu minimal install and download the iso for ppc.It is only like 14MB. See if that will boot. I just had it boot and install on a laptop with 192MB of ram. Like you your problem puzzles me.

---

### Post by doctorbighands on 2009-01-22
So, I managed to get 7.10 installed using the mini CD. Thank you for that suggestion!

Now, it won't recognize my ethernet card. It wants to download restricted drivers for the airport card, but obviously I can't do that until the ethernet card is restored. Clearly the card works, because I just used it to install the OS!

Also, I have no sound.

EDIT: lshw reveals something about "illegal vendor ID" where the ethernet entry is.

---

