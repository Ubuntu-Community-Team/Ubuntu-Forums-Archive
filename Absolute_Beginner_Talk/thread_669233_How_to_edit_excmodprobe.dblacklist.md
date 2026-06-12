---
title: "How to edit /exc/modprobe.d/blacklist"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Mightygringo on 2008-01-16
how can i edit the blacklist in terminal cuz i cant change it back from the mistakes i made with text editor,i added these two lines extra
123456
exit

can someone give me the commands to delete these two lines out of blacklist?

---

### Post by bumanie on 2008-01-16
How did you do this in the first instance if you don't know how to change it back again?
Please be sure you know what to change **_before_** doing anything.
You will need to go to terminal and type
gksudo gedit /exc/modprobe.d/blacklist 
this will open the gedit list and allow you to change things and then save. 
Be careful!!
PS: As the post below shows the file is etc not exc as you put originally (a typo I guess)

---

### Post by justleen on 2008-01-16
vi /etc/modprobe.d/blacklist


move the cursor to the line you wosh to delete and then press the"d" key twice.

once their removed, press ESC, enter a ":" and then "wq" followed by an ENTER

if you make a mistake, press ESC, enter a ":" and then "q!" followed by an ENTER

---

### Post by Mightygringo on 2008-01-16
thanks guys i was trying to get my wi-fi working and i just copied and pasted the commands and added two words that should not have been 

Thank You very much

---

