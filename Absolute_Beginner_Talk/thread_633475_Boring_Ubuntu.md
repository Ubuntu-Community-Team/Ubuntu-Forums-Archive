---
title: "Boring Ubuntu"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by defjam1234 on 2007-12-06
My ubuntu must not have some options applied to it because it is quite bland. I have found the visual settings menu but it wont let me apply them. is there anything else i can do or any way i can fix my visual settings?

---

### Post by philinux on 2007-12-06
If you got Gutsy then System>prefs>appearance is a start.

The website gnome-look.org  has some more eye candy too.

---

### Post by defjam1234 on 2007-12-06
im having a tough time figuring out how to get my downloads to take affect. do i need to do something with terminal?

---

### Post by tech9 on 2007-12-06
type this in the terminal

sudo apt-get update

sudo apt-get install compiz

then edit/config to your hearts content

That should spice things up :)

---

### Post by Swmmrman on 2007-12-06
Also go under system -> administartion.  Restricted device drivers.  And make sure you have a working interenet connection.  Gutsy will not enable all effects without the drivers.

---

### Post by defjam1234 on 2007-12-06
is the last post supposed to allow the visual effects to work because it still gives me the same error even after those steps. Secondly i downloaded an "icon theme" off of the above gnome site but i still cant choose it as my default

---

### Post by Swmmrman on 2007-12-06
Did it download the latest device driver.  I had to do that to kick up my visual effects.

---

### Post by defjam1234 on 2007-12-06
when i did the terminal steps something happened in terminal but nothing outside changed, and when i followed your steps it gave me ATI Radion graphics driver with a check beside it and an Intel Wireless network connection also with a check mark

---

### Post by Dark_X on 2007-12-06
You should install xgl.
```
sudo apt-get install xserver-xgl
```

---

### Post by Swmmrman on 2007-12-06
My only guess at this point is that the driver isint supporting The compiz.

---

### Post by defjam1234 on 2007-12-06
i still seem to have noob syndrom and cant figure out how to impliment the changes made (because terminal obviously did something) on my desktop

---

### Post by defjam1234 on 2007-12-06
Oh nvm i think i figured that part out... just one more question.....on a lot of screenshots i see there is a mac-like menu on the bottom of the screen, can this only be used if the visual effects are enabled or is it another download?

---

