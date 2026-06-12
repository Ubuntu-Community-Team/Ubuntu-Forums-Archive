---
title: "how to kill a program"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by sthapit on 2007-05-22
is there an ubuntu (feisty) equivalent of cont+alt+delete?  i've had firefox freeze on me twice now (i couldn't even open the terminal)  and i didn't know what to do so i had to hard boot!

---

### Post by Martin on 2007-05-22
If Alt F2 (pressed together) works you can type 'xkill' and click the resulting skull and crossbones icon in the offending prog and it will be gone. Ctrl-Alt-Backspace will kill and restart the X-Window server without having to take down the whole PC which is a little less drastic than killing the whole machine.

---

### Post by wormser on 2007-05-22
I do it by the command line.

This command displays running processes and is piped into grep to just display results with firefox in them.
```
ps aux | grep firefox
```

>  ps aux | grep firefox
1000      3686  0.0  0.0   2880   748 pts/0    R+   20:42   0:00 grep firefox
1000     12137  2.5  4.1 196140 85920 ?        Sl   17:27   5:03 /usr/lib/firefox/firefox-bin

The kill command stops a process.
```
kill pidnumber
```

The pid number is the second number listed in the quote.  In this case it is 12137.  This number changes and will not be the same every time.

---

### Post by sthapit on 2007-05-23
thanks!  i was able to try all 3 techniques.  

as a sidenote, i pressed cntrl+alt+F2 instead of alt+F2 and it kicked me out of the graphical screen and into a giant terminal with a login screen.  i wasn't able to get back to the "normal" gui ubuntu so I had to do another hard boot.  is there a way to get back without hard booting?  and what IS cntrl+alt+F2 anyway?

---

### Post by byenary on 2007-05-23
or 
pkill firefox

---

### Post by Viskovitz on 2007-05-23
In Linux you have a number of available terminals, called TTYs. That's in case you just want to work from the *real* command line. Probably you have 1 to 6 enabled. 7 is for X, the graphical environment. With Control+Alt+FX you can go from one to another. Try 1 to 7 and you will see them :)

So, whenever that happens to you again, just ctrl+alt+F7!!!

Cheers

---

### Post by Viskovitz on 2007-05-23
Just for reference, you can also:

```
killall firefox-bin
```

Although pkill looks simpler, you don't have to know the real name of the binary.

---

