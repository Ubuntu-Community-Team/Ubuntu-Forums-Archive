---
title: "One more question"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-01-30
now i have managed to get my easycam package to work, is there a way i can get this to remain permanent. i.e. easycam seems to compile and install the spca driver for my webcam but next time i log in it doesnt work and i have to go to command, type export CC=/usr/bin/gcc-3.4 then run the easycam package again. although this is no great chore is there a way of either automating it on login or simply making it a permanent fixture?

---

### Post by lreyes6 on 2006-01-30
maybe with a file in /etc/init.d/ that execute the line of code u have to type every reboot...

it goes like this
[LIST=1]
[*]first you create the file let's say 'camera' on the /etc/init.d
```
 sudo gedit /etc/init.d/camera
```
[*] then you put your code inside the file... save it and exit gedit
[*] then you have to make the file ejecutable like this ```
 sudo chmod +x /etc/init.d/camera 
```(sorry if i said something wrong in engles but is my second language) 
[*] and u have to add the file to the boot of ur ubuntu like this ```
 sudo update-rc.d camera defaults 99 
``` in this case 99 is the order of the process to be executed at the boot 
[/LIST]

hope this helps.. :-D

---

### Post by DiscoKiller on 2006-01-31
Thankyou very much, you have been a great help. I should be able to get this right. Your english is alot better than my second and third languages btw :D

DK

---

