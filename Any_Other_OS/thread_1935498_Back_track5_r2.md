---
title: "Back track5 r2"
date: 2012-03-04
forum: Any Other OS
---

### Post by Fr3ak12 on 2012-03-04
hi there every1 i was told to post here. 
i have a problem with installing drivers for my nano usb ew7811..
i followed a post on here yet it dont work!! cant file the location of file even if is on the desktop!!! please i need this wireless usb to work!!

Fr3ak

---

### Post by mastablasta on 2012-03-04
what does "don't work" mean? which post you followed? you can't install the drivers because why? did you make the file executable?

---

### Post by oldos2er on 2012-03-04
Moved to Other OS/Distro Talk.

---

### Post by Fr3ak12 on 2012-03-05
> **mastablasta said:**
> what does "don't work" mean? which post you followed? you can't install the drivers because why? did you make the file executable?

Thanks for your reply.. i am a COMPLETE amateur at this..:confused::confused::confused:
then i say it dont work i mean it comes with errors sayin "file location cannot be found or file is missing.."
how do you make it a executable??

this is what i tryed to follow [http://ubuntuforums.org/showthread.php?t=1590873](http://ubuntuforums.org/showthread.php?t=1590873)

Please assist thanks

---

### Post by mastablasta on 2012-03-07
> **Fr3ak12 said:**
> then i say it dont work i mean it comes with errors sayin "file location cannot be found or file is missing.."

 
ah so you are trying to compile the drivers.
 
make sure you have all necessary compiling tools (build essential, linux headers).
 
then make sure to follow the instructions correctly. and when you extract the file go to it (for exmaple with nautilus) and then right click and select open terminal here.
 
or you can use the cd command in temrinal to get to the correct destination. 
 
either way the message you received is there because:
1. you are running your make command in the wrong directory
2. you didn't extract the file to propper level of extraction required to compile it
3. you misspelled the file name
 
also as mentioned in the linked thread once you get it working you will always need to compile after kernel updates. have you tried searching for a PPA for these drivers?

---

### Post by chili555 on 2012-03-07
> 2. you didn't extract the file to propper level of extraction required to compile itThat's probably the case. Please re-read the instructions. There are two extractions needed:> Right-click and select [COLOR="Red"]'Extract here.'[/COLOR] A folder will be created named rtl8192CU... Open it and open the folder called 'driver.' There is a file in there called rtl8192CU... Right-click and select [COLOR="Red"]'Extract here.'[/COLOR] Then also notice the cd command goes down ***three*** levels:> cd Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726Is that what you typed?

---

### Post by Fr3ak12 on 2012-03-07
hey thanks for all replys.. it seems to be working all i did was follow this video
[http://www.youtube.com/watch?v=gcjfm11dr4s](http://www.youtube.com/watch?v=gcjfm11dr4s)

when i typed the
"apt-get install ark"
it worked the wireless device poped up on my pc...

But the laptop still dont work..

---

