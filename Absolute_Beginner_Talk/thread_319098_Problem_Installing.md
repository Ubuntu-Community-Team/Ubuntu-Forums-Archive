---
title: "Problem Installing"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by BlackSmith on 2006-12-15
Hey guys, i downloaded the 64bit Ubuntu image file, put it on a disc, and when i boot from it..i click on install and it goes to a grey text loading screen.. looks like it has some video problems on the loading bar though..heres a pic...(dont mind the colors the camera picks them up differently). everything is grey. 

[IMG]http://img350.imageshack.us/img350/4458/loadnl8.jpg[/IMG]

After this screen is done..it goes to a blank black/blue tintish screen..and nothing happens. so im forced to reboot. anyone know the problem? im running an ati radeon 9800 pro 128mb.

---

### Post by Bachstelze on 2006-12-15
ATi cards are known to have poor Linux compatibility. Have you tried running the CD in "Safe graphics mode" ?

---

### Post by BlackSmith on 2006-12-15
> **HymnToLife said:**
> ATi cards are known to have poor Linux compatibility. Have you tried running the CD in "Safe graphics mode" ?

Yes, I have..same blank screen..

---

### Post by meng on 2006-12-15
I doubt the ATI card is the explanation for the problem, it OUGHT to run okay with the generic radeon driver. Perhaps try the Alternate CD (with a text-based installer). Or perhaps the i386 version rather than the AMD64 version?

---

### Post by BlackSmith on 2006-12-15
Ok, Im downloading the 64bit text based version now..i would be pretty disappointed if the 64bit version didnt work on mine..i have the athlon 3200+ 64...anyways, would there be a significant difference if i do the 32bit on my 64bit cpu?

---

### Post by meng on 2006-12-15
I have the same CPU, and I run 32-bit, so that I don't have to fuss about applications that are not supported under 64-bit (e.g. acrobat reader).

---

### Post by BlackSmith on 2006-12-15
> **meng said:**
> I have the same CPU, and I run 32-bit, so that I don't have to fuss about applications that are not supported under 64-bit (e.g. acrobat reader).

Oh ok, well, my friend thinks it might be the VRAM in the video card.. its the 128mb 9800 pro. 

anything?

---

### Post by meng on 2006-12-15
> **BlackSmith said:**
> Oh ok, well, my friend thinks it might be the VRAM in the video card.. its the 128mb 9800 pro.
I'm not sure, does your friend think the VRAM is actually faulty, or just incompatible? Either way it's not something I'm familiar with.

---

### Post by five_star on 2006-12-15
Hi BlackSmith,

I have exactly the same problem with my Radeon 9800 Pro 128Mb I have yet to see any success either :(

---

### Post by meng on 2006-12-15
I guess I spoke too soon, eh? Sounds like it is the ATI card, although my own ATI card (Mobility Radeon 9000, very different of course) gave no problems. Whaddya know ... still you have the options of 32-bit and alternate install left to you.

---

### Post by five_star on 2006-12-15
After some muddling through the instructions I have managed to escape the black screen of death

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I followed the 6.10 section reasonably well, most of it worked apart from the end section.  there seems to be no gedit program in Kubuntu

oh well, just got to sort the resolution out now :)

---

