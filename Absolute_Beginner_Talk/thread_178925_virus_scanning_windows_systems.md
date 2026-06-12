---
title: "virus scanning windows systems"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by m4gnesium on 2006-05-18
I'd like to be able to virus scan the two Windows XP systems on my network from my Ubuntu system. What's the best way to do this?

---

### Post by Mustard on 2006-05-18
I was going to dive in and answer this one, but then I realised you were talking about checking for viruses over a network.  I've not had much experience with using network connected hardware myself, so I'm not sure about this one. :)

---

### Post by mlind on 2006-05-18
This could work : 
* mount ntfs drives through network using NTFS read/write driver like CaptiveNTFS or fuse

* use ClamAV. Once it has write access to the drive provided by drivers, disinfection should work.

Dunno how realiable write support is with those NTFS drivers though..
I'd use native virusscanner instead.


/edit typo

---

