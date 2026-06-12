---
title: "Installation Problem"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by borlandk on 2007-11-04
I have reformatted a computer that I am trying to load Ubuntu on. I have downloaded the ISO file and burned to a CD. When I boot the the PC and Ubuntu installation screen comes up, I use the default installation and I get a I/O error, Error Reading Boot CD.

If I burned the disk at a higher speed than the  booting CD drive is rated at, would that cause it? Any ideas to move forward would be great.

---

### Post by candtalan on 2007-11-04
fast burning could easily cause it. I usually burn at half rated speed or less. In the live CD initial boot menu you should see an option to check the CD. This is useful to verify that the CD as burned can also be read correctly in the particular CD drive. I have had problems indicated even if the CD is perfect in another (newer?) drive.

Burning at a much slower speed will usually be a solution, and checking the burn quality in the burner or afterwards with its md5sum  also.

---

### Post by borlandk on 2007-11-04
checking the CD for defects was the first solution I tried and I got the same Read error. So is reburninig the best solution at this point?

---

### Post by borlandk on 2007-11-04
I also burned a new install CD at 4x and had the same problem. I noticed that when InfraRecorder finished the CD it had a notice regarding some CD's don't like fixation or something like that. ???

---

### Post by Therion on 2007-11-04
If it's an option, try burning a DVD instead of a CD.  That, or try downloading the .iso from a different mirror, or both.  I had no end of problems with install CD's, but DVD's work like a charm for me each and every time.  Maybe it's just my burner (Plextor) but it works for me.

---

### Post by borlandk on 2007-11-04
Unfortunately the PC being installed to doesn't have a DVD.

---

### Post by candtalan on 2007-11-05
> **borlandk said:**
> checking the CD for defects was the first solution I tried and I got the same Read error. So is reburninig the best solution at this point?

CD can be checked for defects in more than one way.
an MD5sum check will check the image file (iso) before burning (download verification ok), and with the burned CD in a drive, the image file information can also be extracted and also MD5sum checked (burned image verification, and drive reading function verification). These checks should be done against an md5sum figure which has been obtained from the trusted download site: for ubuntu the ideal source would be canonical servers, but official mirrors should be good too. An additional method would be to run a CD self check. This can be done by booting from the CD in the target CD drive and using the boot menu option to check the CD. This should verify that the particular CD drive to be used in the installing machine can read all files fully and that the files are correct.

Reburning in the same drive, with the same iso file will probably give the same result (?), so while the image or CD or burner is under 'suspicion' it would be useful to make a significant change somehow at some stage here.

---

### Post by candtalan on 2007-11-05
> **borlandk said:**
> I also burned a new install CD at 4x and had the same problem. I noticed that when InfraRecorder finished the CD it had a notice regarding some CD's don't like fixation or something like that. ???

This might be referring to (I think) something to do with how some burner drives finish the burning process - a sign off or maybe end of file or something, I do not really know. IIRC I had similar trouble a couple of years ago with CD checks and a different distro (suse).
You might find more information about this using google etc search.
At this stage it would be worth considering burning an image using a different machine, as a test anyway. Maybe someone local can post you one?)

---

### Post by borlandk on 2007-11-06
Thank you ... I got it right. I check the iso file with MD5sum and the "hashes" didn't match. Deleted the file, downloaded again and burned at 4x and it worked and loaded.

Thanks for your suggestions.

---

