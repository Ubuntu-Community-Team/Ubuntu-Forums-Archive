---
title: "n00bie brasero cd burn error (all other programs don't work either"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by md11driver on 2007-12-03
gutsy 7.10, panasonic dvr-105, memorex cdrs, newly cleaned drive.

overview:  i can't burn cds on any program resident on my puter.  all programs seem to give the same result.  i put a fresh cd and ubuntu recognizes it as a blank cd.  after opening a program and trying to write data to the cd i get an error message to insert recordable media.  the cd had been written to (verified visually)  and is now a coaster.  it's not recognized as anything by any optical drive.

when doing a simulated burn on brasero everything goes perfectly.  when doing a real burn on brasero an error message appears:

"error while burning--the image does not seem to be a proper iso9660 file"

boom!!  another coaster!

i'm probably just absolutely doing something stupid, but am brand new to linux. moderate windows experience.

please, please help an old beginner.

---

### Post by zeller on 2007-12-03
What are you trying to burn?

If Brasero's output is be set up to burn an iso and you are giving it data files instead then it will return an error like that. Check the output settings and see if that is the case.

I know in Windows using IMG_Burn you have to specify what mode you want to be in: Build, Write, etc. I haven't really used Brasero so I don't know how it burns.

---

### Post by bbbaldie on 2007-12-03
The old noob is my brother, and I've been trying to help him resolve this. I'm no ace, but have been running multiple Ubuntu installs for about eight months.

I just installed brasero myself, and we both went side-by-side through the same processes of burning discs. I successfully burned a data disk. When his dialog came up as far as "writing cue sheet," that when his machine bombed with the bad iso error.

He's NOT writing an iso, or creating from one. He's simply trying to copy files to a data CD.

Hope this helps.

---

### Post by md11driver on 2007-12-03
further info from md11driver

i found a file in my home folder labeled .xsession-errors

most meaningful comment seems to be this:

(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd1: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd1: MODE SENSE with real length 65535 failed.
(K3bDevice::Device) /dev/scd1: modeSense 0x05 failed!
(K3bDevice::Device) /dev/scd1: Cannot check write modes.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd1: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd1: MODE SENSE with real length 65535 failed.

does this shed any light on my gremlins?

i tried to burn from k3b program as well.  this is when error messages were generated.  i found no error messages from brasero.

---

### Post by md11driver on 2007-12-03
i pulled the trigger and reloaded gutsy gibbon.  cd writing is normal now.

md11driver "out"

---

### Post by zeller on 2007-12-04
Glad you got it solved!

---

