---
title: "ubuntu 6.06.1 wont boot on my hp pavilion desktop"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by wilrecar77 on 2006-09-10
it wont boot. i have set my  bios boot priority with cd-rom at top.i think i may have burnt the cd wrong so ill say how i did it if you can correct me. i downloaded xubuntu and set cdburnerxp pro to bootable disk and write speed 1x. then i let it write(no problems burning) and restarted the comp. it boots into windows. im thinking if i take windows off it will be forced to boot from cd, but if theres another way ill do the other way

---

### Post by meng on 2006-09-10
You should not be burning a "bootable CD". Just burn the ISO as-is, and it will boot itself.

---

### Post by wilrecar77 on 2006-09-10
note:did what you said,still doesnt work. should i be doing something with a md5 or something?

---

### Post by meng on 2006-09-10
Does the computer do exactly the same thing as with the burned-bootable disk? First thing I would do is check the contents of your freshly burned CD while you are still in Windows. What you want to make sure is that there is a complete filesystem there, and not just a single .iso file (some users mistakenly do this). If there is a filesystem, then it is conceivable that your download was corrupted. As you said, checking the md5sum is the thing to do. You can download a program for Windows called md5summer, and use this to verify the .iso file. It will spit out a (hexadecimal I think) number that you can check against the official md5sum available from the same download page.

---

### Post by wilrecar77 on 2006-09-10
ill be doing that. all it shows on the cd is a single iso file. whick line on the md5 thingy? also dont make it to complicatd if this step fails cause im only 10. also would the fact that the cd drive that works is the expansion slot cause the original cdrom drive got fried somehow make it hard to boot?

---

### Post by meng on 2006-09-10
Okay perhaps what I have done is mislead you (unintentionally). You need to burn FROM the image/ISO file to the CD, sort of like extracting from a ZIP file. Your CD burning program should be able to do this, there should be an option to "burn from image". You do not need to choose a bootable option though.
EDIT: after a series of false starts, you start to appreciate that buying a few CDRWs is not a bad investment. I still find them useful, and I consider myself fairly experienced!

---

### Post by wilrecar77 on 2006-09-10
i cannot get to the exact xubuntu file. i can only get to the cd with it on it and the md5sum's dont match. i cannot get to the exact file because it on the desktop and is not listed as a file checkable. i have written it correctly. it shows up with a screen and i choose to burn iso/image. i set it to 4x and let it burn. i have burnt 2 cds, one using the joilet thingamabob and one using iso level 1. neither work. im about to give up for now and just format drive c by going into the caldera DR-DOS on my comp then try. also this is kinda a project for AIG that i was supposed to do over the summer that i didnt do so if this fails i can just put together something else.EDIT: no worries about the cd-r's my mom bough them and doesnt care if i waste to much

---

### Post by meng on 2006-09-10
Sorry to hear it isn't working out. Perhaps you'll have an opportunity to try it out at some future date.

---

### Post by wilrecar77 on 2006-09-10
thanks for the help.

---

