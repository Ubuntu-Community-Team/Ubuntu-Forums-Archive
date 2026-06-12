---
title: "Another pair of questions, one is really dumb lol"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by Epyon on 2005-08-03
well, i just installed it onto my desktop, and its my only OS on it now.

can you guys give me that link like you did before, something that gave me info for installing stuff. and 
so my two questions: well when i installed it i had that bar in the top of the screen. well i tried to move it down, and in the process i accidentally let go.... so now i have this bar on the right screen, and its HUGE! the damn thing takes up 20% of my screen, any help?

other question is how do i reconfigure my monitor options? i had the same problem on my Fedora install. my LCD doesnt work by default so i had to manually input the H and the V coordinates, i cant find the place to do this in Ubuntu so far, any help telling me where it is?

Alright, thanks guys, i really want this to be my main OS.

---

### Post by Epyon on 2005-08-03
oh, and another thing, i cant seem to find where the option is in firefox to change my homepage.

---

### Post by bored2k on 2005-08-03
[QUOTE=Epyon]oh, and another thing, i cant seem to find where the option is in firefox to change my homepage.[/QUOTE]
 Upper panel - Edit - Preferences - General - Home Page

---

### Post by aysiu on 2005-08-03
Screen resolution:

[http://ubuntuforums.org/archive/index.php/t-25481.html](http://ubuntuforums.org/archive/index.php/t-25481.html)

Firefox homepage:

Edit > Preferences > General

---

### Post by bored2k on 2005-08-03
[QUOTE=Epyon]well, i just installed it onto my desktop, and its my only OS on it now.

can you guys give me that link like you did before, something that gave me info for installing stuff. and 
so my two questions: well when i installed it i had that bar in the top of the screen. well i tried to move it down, and in the process i accidentally let go.... so now i have this bar on the right screen, and its HUGE! the damn thing takes up 20% of my screen, any help?

other question is how do i reconfigure my monitor options? i had the same problem on my Fedora install. my LCD doesnt work by default so i had to manually input the H and the V coordinates, i cant find the place to do this in Ubuntu so far, any help telling me where it is?

Alright, thanks guys, i really want this to be my main OS.[/QUOTE]
 1. [http://ubuntuguide.org/](http://ubuntuguide.org/)
2. On the bar, right click - Properties - Size - press down until you see fit. After that, simply drag the panel to wherever you want.
3. Execute the commands in Terminal mode (Applications -> System Tools -> Terminal):
```
sudo dpkg-reconfigure xserver-xorg
```Restart afterwards.

---

### Post by Epyon on 2005-08-03
oh man, after i did this

sudo dpkg-reconfigure xserver-xorg

everytime i start it up, it wont go auto to GUI, i have to type startx to get the gui back, up. is there anyway to fix this?

---

### Post by Epyon on 2005-08-03
and its also werid, when ubuntu is up and running, on my CRT monitor and i change it to my LCD, it works fine, but then when the computer is off, and i start it up again with the LCD plugged in, it doesnt work
i havent changed that option the rate refreshs yet...

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=Epyon]oh man, after i did this

sudo dpkg-reconfigure xserver-xorg

everytime i start it up, it wont go auto to GUI, i have to type startx to get the gui back, up. is there anyway to fix this?[/QUOTE]


Did you reboot?

hmmm....try this command:

sudo gdm

(we'll try to help you succeed)

---

### Post by Epyon on 2005-08-04
yea i tried sudo gdm, and what happened was some werid message involing GTK or something.....oh well i just reinstalled the entire Thing again lol. im trying whatever it takes to learn this damn thing through.

but i still dont understand how that when the System is up and running fine, and i switch the cables to the LCD monitor it works fine, but when i start up the machine with the LCD plugged in, it gives me a black screen, with the numbers.

numbers are out of range H 31.3 V 59.4 CLock 78Mhz 720x400

i couldnt seem to find where i put those numbers into...

---

