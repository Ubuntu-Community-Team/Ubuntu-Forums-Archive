---
title: "Adobe rgb ICC for Gimp/Ufraw"
date: 2009-05-11
forum: Art &amp; Design
---

### Post by HIPS on 2009-05-11
Hi!
 

 This might be a stupid question, but I have to ask it anyway. How do I get an Adobe rgb ICC file into Ubuntu? Can I use a Windows icc file or do they differ from icc files for Linux?


                                  I want to be able to use Adobe rgb with both Ufraw and Gimp, since I have my camera set to use that color profile (bigger color space than sRGB).

---

### Post by Niva on 2009-05-11
The icc format is a spec which should be platform independent.  The only way to know is to try it, are you having problems with opening the files?

I personally don't have experience with that file format.

---

### Post by Neon Lights on 2009-05-11
They don't differ. I believe you can get it system wide by downloading [icc-profiles]("apt:icc-profiles") from the repos. Color management still needs a little simplification on Linux as far as I gather though. :/

---

### Post by HIPS on 2009-05-12
[FONT=Verdana][SIZE=2]Thank you for your answers. The feeling I got when I did my search was that it wasn’t platform dependent, but then on Adobes download page it said I could choose Windows, Mac or Linux – but nothing happened when I choose Linux.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]I guess I just chickened a bit and didn’t dare to try – I’m still new on Linux and Ubuntu. But your answers helped me take the step, so when I get home I’m going to download the profile and try it with both Ufraw and Gimp.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Yeas, I’ve heard that over all color management has some way to go in Linux, but I think both Ufraw and Gimp should handle it ok.[/SIZE][/FONT]

---

### Post by Macr237 on 2009-08-22
I am hearing you, Hips. I want AdobeRGB and 14 bit compatibility. I feel I am missing the boat on images, which I am getting professionally printed.

---

### Post by AJB2K3 on 2009-08-23
Icc profiles can be set up in GIMPs colour management section.
Sane's colour management is driving me insane.
Xcalib is used for setting profiles in X.

---

