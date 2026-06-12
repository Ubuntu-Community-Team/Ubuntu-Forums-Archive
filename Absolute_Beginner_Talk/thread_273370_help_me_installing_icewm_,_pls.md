---
title: "help me installing icewm , pls"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by ghostshadow189 on 2006-10-07
hi all ,
i installed icewm with "sudo apt-get install icewm iceconf iceme" . after that , i loged out and choosed icewm session . but unfornately , it didnt display anything , like toolbar , start menu , etc . it just displayed a blue desktop . i also tried ctrl+alt+esc and i saw window list , so that mean maybe i installed icewm successfully , but still there're some mistake ?
thanx for ur helps !

---

### Post by confused57 on 2006-10-07
Did you try right-clicking on the blue desktop?  There may be a 
drop-down menu...don't know for sure.

---

### Post by ghostshadow189 on 2006-10-07
yes , i tried but nothing happened

---

### Post by jordanmthomas on 2006-10-07
have you run iceconf yet?  Maybe that will set everything up for you.

---

### Post by catlett on 2006-10-07
The easiest way to get icewm is to install ubuntu lite. [http://www.ubuntulite.org/drupal/?q=node/1](http://www.ubuntulite.org/drupal/?q=node/1)
Make sure you have the universe repository enabled and then add the ubuntu lite repo.
```
sudo gedit /etc/apt/sources.list
```
Add this line to the bottom
```
deb http://blueeyedcreature.net/ubuntu ./
```
Save the file and close. Open a terminal and enter 
```
sudo apt-get update
```
```
sudo apt-get install ubuntu-lite-desktop
```
Reboot and select "icewm" from the sessions option.

---

