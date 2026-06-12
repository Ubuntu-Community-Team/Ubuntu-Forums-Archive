---
title: "Formatting out bad sectors on HDD when installing"
date: 2011-11-02
forum: Apple Hardware Users
---

### Post by nrg710 on 2011-11-02
I'm about to install Ubuntu on my Mac Pro, but the HDD has got a major error on it.

The error was found using the Apple Hardware Test just after startup. I checked the Apple forums and the error - 
4HDD/11/40000004:SATA (0,0)
seems to be terminal and people report having to replace the HDD.

Question is, during and install of Ubuntu (to replace OSX- not dual boot) do you folks think that I can reformat the HDD to exclude bad sectors? Or do I need to just buy a new HDD?

---

### Post by westie457 on 2011-11-02
Hi 
Just to confirm the state of the HDD bott into a LiveCD in Try mode. Open Disk Utility to check the S.M.A.R.T. status and run a short diagnostic test.

If there are bad sectors the disk-surface itself is damaged and is unrepairable. 
If damaged sectors are near the MBR area of the drive no OS will install afaik.

Recommendation then is to bite the bullet and get another HDD ASAP save any personal files you want to keep.

---

