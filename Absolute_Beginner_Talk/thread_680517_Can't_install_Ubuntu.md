---
title: "Can't install Ubuntu"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by cooltrigger on 2008-01-28
hi guys, i am totally new to linux and have problems in installing ubuntu. i have downloaded the iso package from the website and have burned the ISO properly with infra recorder to a CD. when i boot from the CD and click install then the ubuntu indicator start to move but after arround 30 seconds i am left with a shell window with blinking cursour. i have tried to burn it several times again with the lowest speed possible but it always ends with that.  i also have to add when i try to open the CD in windows then i cannot see any contents on the CD but its full with datas when i check it (700mb) i am currently downloading the DVD format with 4.2 gb via torrent because i am suspecting a corrupt file.
what are you guys suggestion. anyone had same troubles?
please help me because i want the get rid of my stupid shitty windows ASAP.

---

### Post by Faud on 2008-01-28
If you are sure that you burned it correctly and checked the discs for errors per the instructiosn you could try installing it in safe graphics mode

---

### Post by cooltrigger on 2008-01-28
how to install it in graphics safe mode and why do you suggest that?

---

### Post by Ub1476 on 2008-01-28
You can select safe graphic mode on the CD menu. I think he suggest that because you can't come in to a GUI, so safe-graphics it is:)

---

### Post by bodhi.zazen on 2008-01-28
And does the md5sum of the iso check out ?

How about the CD ?

---

### Post by Mochabuntu on 2008-01-28
hi cooltrigger,

i had the same trouble trying to install Ubuntu from BOTH CD and DVD. It would get to the point of installing then just flash the cursor for a while, never getting anywhere. Having d/l both as a torrent, I'm pretty sure it wasn't a corrupt file issue, I use a laptop, and Ubuntu, or at least my copies (all 6 mind you, 2 from Canonical no less) had the same deal. I finally moved the PXE (or network boot) to last in the boot sequence and that fixed my probs.
Don't know if it will help you, but perhaps changing your boot sequence could help?

---

### Post by cooltrigger on 2008-01-28
hi mochabuntu, that sounds like my issue. but did you also have the same problem that you couldnt see any contents on the CD in windows?
by the way i already disabled all other boot devices in my BIOS and now there is only CD ROM left but still i have this problem. by the way, i want to say thanks to all of you. its amazing how fast i get reply and help from all of you in this forum. i have still to work for 1 hour. then i will head home and continue my installation war. :-) i will try to do it in installation mode as suggested and come back to you guys if it fails.

---

### Post by Mochabuntu on 2008-01-28
no probs cooltrigger

actually, the fact you can't see the disc contents in windows leads me to believe there is a disc problem.

have you tried burning with a different program? i've never heard of infra-recorder before. have you tried CDBurnerXP? Or maybe ISOBurn?

hope this helps

---

