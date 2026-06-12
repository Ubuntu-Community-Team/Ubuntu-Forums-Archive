---
title: "Screen shift to the right"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by eklypze on 2006-04-05
Hello everyone.
I noticed that each time I go onto Ubuntu, my screen is shifted a bit to the right. I currently Dual-boot with Windows XP and the screen is perfectly fine on there. Is there any way I can shift my Ubuntu screen to the right permanently? It gets sort of annoying to have no scroll bar. :mad: 

Thanks a lot. :)

---

### Post by dermotti on 2006-04-05
I had that issue. running **sudo dpkg-reconfigure xserver-xorg** fixed mine. Its a refresh rate issue.... If that doesnt work you may have to manually match your refresh rates in your xorg.conf to match windows. Or make windows match linux...

---

### Post by catlett on 2006-04-05
I don't know if there is a software solution but there is a hardware solution. Use the controls on your monitor(physically on your monitor). There are controls to shift your screen up,down,left,right. That will definately move your screen to the left. Is there a software solution? I don't know. But at least you can do it manually and have a scroll bar until you find a solution.

---

### Post by dermotti on 2006-04-05
Problem is, if you manually adjust it and fix it in linux, it will be screwed up once you log back into windows. At least thats what happend to me.

---

### Post by tarsier on 2006-04-05
I used to have this problem too.  The way it resolved itself for me is by installing the Nvidia drivers.  After I did that I didn't have to use my monitor controls to move the screen to the left or right depending on if I was in Windows or not.

---

### Post by eklypze on 2006-04-05
Thank you guys for your inputs. I have tried the *sudo dpkg-reconfigure xserver-xorg* but no success. My refresh rate is currently 75Hz which is max for my monitor. Also, how can you install nVidia drivers on Linux?

---

### Post by Mustard on 2006-04-05
I would look over this thread, as it has some instructions on resolving this problem towards the end of the first post.

[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

For nvidia drivers you can try either of these links..

Ubuntu Wiki
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia) 

Ubuntu Forums
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

---

### Post by dermotti on 2006-04-05
download **nvidia-glx**

---

### Post by eklypze on 2006-04-05
Thank you, I found a way to shift my screen and now it looks great. :)

---

