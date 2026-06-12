---
title: "fat32 external hdd corrupted. recovery help needed."
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by CaseyR on 2007-06-05
firstly, thanks to anybody who can shed some light on this situation.

this is my first post, but i've been using ubuntu for a few of months and have been lurking on the forums so bare with me please.

i have a western digital passport 100GB drive  (external usb) formated to fat32.  i was using it to migrate files from my friends xp box to vista.  the computer was turned off in the middle of the transfer (w/o safely removing) and now has a corrupted boot sector.  its readable on windows 98 after installing the driver, but is unreadable on any other OS.  unfortunately, i no longer have access to windows 98 because it is in a different city.

ive been using the testdisk application and feel like im right on the verge of recovering it, but it just doesnt happen.  i can even see the file names when testdisk lists them.  

i read that you can dump the information on the hdd onto another of equal or greater size or make a disc image, but i dont have another drive big enough.  is there a way to pick what information is dumped?

according to testdisk, my boot sector is ok but my backup boot sector is not.  maybe if i fix the backup, all would be ok?


sorry for the long post.  ive been working on this forever and it is really annoying.

---

### Post by smoker on 2007-06-05
hi, have you tried a chkdsk, eg, start, run, cmd, and type 'chkdsk /f /r d:' without the quotes, where d: is your usb drive?

also, wd have their own useful recovery product called, 'data lifeguard', you can download the version for your drive from here: [http://support.wdc.com/download/index.asp?cxml=n](http://support.wdc.com/download/index.asp?cxml=n)

> [is there a way to pick what information is dumped?
not sure about this, sorry,

best of luck

---

### Post by ruy_lopez on 2007-06-05
Try sleuthkit & autopsy:

[http://www.sleuthkit.org/](http://www.sleuthkit.org/)

---

### Post by CaseyR on 2007-06-05
thanks for the quick replies guys.

i guess i should mention that im using ubuntu and not windows anymore.  i did try the wd software when i had access to a windows machine.  all it told me was that i had corrupted sectors.  whatever recovery tool it had did not work.  i may try it again eventually if i cant get anything else working.

looks like sleuthkit is worth a try.  i'll get back to you and let ya know how it went.

in the mean time, does anybody else have any recommendations?  maybe something i missed with testdisk...

---

### Post by smoker on 2007-06-05
> **CaseyR said:**
> 
i guess i should mention that im using ubuntu and not windows anymore.  i did try the wd software when i had access to a windows machine...

hi, you can download a bootable dos version of the wd software, so doesn't matter what os you are using. the bootable version, along with many other hard drive diagnostic and repair tools are included in the ultimate boot CD, which is a large download, but is useful for emergencies, and of course, is free. more details and download can be found here: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

hope this helps:D

---

### Post by CaseyR on 2007-06-07
so ive messed around with the ubcd some, and ive tried the latest version of the wd diagnostic tool.  as soon as it starts to boot, i get the "starting caldera dos" message and then....nothing happens.  what am i doing wrong?  do i need to disable something or what?

thanks for your patience everyone!

---

