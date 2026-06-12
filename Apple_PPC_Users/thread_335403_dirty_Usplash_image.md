---
title: "dirty Usplash image"
date: 2007-01-10
forum: Apple PPC Users
---

### Post by el-sio on 2007-01-10
When I first booted on the liveCD, I saw the nice ubuntu splash image, but the progress bar would not advance and I had to restart the computer, so I booted with video=ofonly option and I could see the same graphic but in a dirty version with strange colors (Ubuntu logo is in grey levels and there are blue red and green pixels stains in place of the shadings of the original image). I still installed my system and changed the yaboot "append" line to get rid of the option "video=ofonly", but I still boot with this psychedelic image :(

I tried to get an alternate splash image using the howtos, but none of those seem to work (even the "minimalistic" one ;) )  and I only atually see something with the "Original" Usplash, but it is this dirty image...

I have a 12inch iBook that can display upto 1024x768 and no other graphic problems...

Do I have to "restore" the original splash image (by forcing reinstall) or is it a known problem of ibooks ?

Thank you !

---

### Post by zaerion on 2007-02-10
i had to use the video=ofonly option to install onto my ibook as well.  did you run the 'sudo ybin' command after you modified the yaboot.conf file?  that should change the boot options.  hope it helps.  ^^

---

