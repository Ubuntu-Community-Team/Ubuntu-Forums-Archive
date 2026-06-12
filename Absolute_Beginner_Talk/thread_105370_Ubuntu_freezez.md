---
title: "Ubuntu freezez"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by Enter on 2005-12-18
when i use firefox sometimes it freezez and the whole ubuntu freezez so i have to reboot is there a fix or is there a combination  on ubuntu like ctrl+alt+del :lol:

---

### Post by aysiu on 2005-12-18
A few questions:
1. *Only* when using Firefox?
2. Is it for particular websites... or just randomly?
3. Does this happen if you use another web browser?
4. Does control-alt-backspace work?
5. What about if you launch Firefox in safe mode?
Alt-F2 ```
firefox -safe-mode
```

---

### Post by Enter on 2005-12-18
it happens on this forum and once when trying download opera from opera.com
only happens when browsing with firefox
it happens time from time mostly when i get my mouce on drop down menu
havent tryed control-alt-backspace

---

### Post by doitashimashite on 2005-12-18
Strange... Ubuntu shoot not freezz..

Is it a complete lockup or does CTRL-ALT-F1 work? (in which case you can login and reboot by entering sudo reboot).

---

### Post by Enter on 2005-12-18
well it doesnt actually freeze i can move my mouse but thats it nothing is clickble

---

### Post by Enter on 2005-12-18
some one PLEASE help me this getting annoying whenevr it want to search i click the search link and 2 out 3 times it freezez

---

### Post by kaamos on 2005-12-18
When your machine has booted to the desktop, open a terminal and type```
dmesg > dmesglog.txt
```
Now you have a text file in your home directory. Open that and search for something suspicious (error, warning..). One thing you could also look for are DMA related errors ("DMA timeout"), since I had behaviour like this on a box that didn't support dma.

Hope this helps!

---

### Post by Enter on 2005-12-18
havent found any fatal or just errors with DMA:(

---

