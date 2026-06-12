---
title: "Extremely dangerous mount behaviour"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Roque on 2007-09-23
The BIOS of one of my home PCs got corrupted somehow and I had to reflash it following the usual procedure: I made a DOS bootable diskette and added a FULLY AUTOMATIC flash command to the autoexec.bat. Once the job was finished, I  WRITE-PROTECTED the diskette and mounted it in Ubuntu:

mount /dev/fd0

There was NO message saying it had to be mounted READ-ONLY. Then I edited the autoexec.bat to comment out the dangerous flash command:

pico /media/floppy0/autoexec.bat

and saved the changes. Again, there was NO message saying the file could not be saved. Ignoring the original autoexec.bat was still intact, I unmounted the diskette and by chance put it in the other machine's drive.
When I booted it the autoexec.bat executed and reflashed the BIOS again!. It could have been much worse: it could have "reflashed" another PC with an incompatible BIOS, rendering it unusable (the flash command was set to ignore such incompatibilities)

This should not happen. The system should alert the user when a diskette is mounted read-only and when a file can not be saved.

---

### Post by crjackson on 2007-09-23
> **Roque said:**
> The BIOS of one of my home PCs got corrupted somehow and I had to reflash it following the usual procedure: I made a DOS bootable diskette and added a FULLY AUTOMATIC flash command to the autoexec.bat. Once the job was finished, I  WRITE-PROTECTED the diskette and mounted it in Ubuntu:

mount /dev/fd0

There was NO message saying it had to be mounted READ-ONLY. Then I edited the autoexec.bat to comment out the dangerous flash command:

pico /media/floppy0/autoexec.bat

and saved the changes. Again, there was NO message saying the file could not be saved. Ignoring the original autoexec.bat was still intact, I unmounted the diskette and by chance put it in the other machine's drive.
When I booted it the autoexec.bat executed and reflashed the BIOS again!. It could have been much worse: it could have "reflashed" another PC with an incompatible BIOS, rendering it unusable (the flash command was set to ignore such incompatibilities)

This should not happen. The system should alert the user when a diskette is mounted read-only and when a file can not be saved.

Did you test this on another ubuntu machine to confirm it's not just that one machine?  I'm in bed right now on the laptop so I can't test it tonight, but I'll test it myself tomorrow and see if I have the same result.

---

### Post by Roque on 2007-09-24
Yes, it also happens with KNOPPIX 4.xx and 5. 

But after some more tests I found that it is a random "bug": there are times when the diskette is correctly mounted read.only and others when it is not and thus you can "write" to it (of course, nothing is really written to disk). Occasionally I also get garbage reading text files.

Maybe the drive is faulty or something...

---

