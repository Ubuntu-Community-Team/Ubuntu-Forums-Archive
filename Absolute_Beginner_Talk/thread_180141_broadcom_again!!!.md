---
title: "broadcom again!!!"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by redbuller on 2006-05-21
im having the same problem as a lot of others it seems. i`ve installed dapper and it works and looks great. only thing is the wireless. i`ve looked through posts related to this issue and fwcutter is mentioned but when i follow instructions it says e:couldnt find package bcm43xx-fwcutter. any help would be greatly appreciated. im a total noob just in case you havnt noticed lol. thanks

---

### Post by cvmostert on 2006-05-21
have you tried to have a look at ndiswrapper? then you only need the windows drivers to install the wireless card, i also have a broadcom 4306 and ndiswrapper works vir me... i have had bcm43xx working for me ... but ndiswrapper works best.

thats just my opinion.

have a look to see what modules you have installed.
sudo lsmod

---

### Post by massivevoid on 2006-05-21
ndiswrapper works for me also and I have the 4318. The links in my sig will get you started.

And if you try the newest version of ndiswrapper/Windows Broadcom driver and it doesn't work, try the next oldest one until it does. 

I'm using ndiswrapper 1.13 and an older Windows driver.

---

### Post by redbuller on 2006-05-21
ok i`ve dowloaded it but cant get it working with any of the code. i have it on my desktop is that right?

---

