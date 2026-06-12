---
title: "Disc usage question"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Cchhrriiss on 2008-02-25
I have a 280 gb partition that ubuntu is on 208gb of that are used according to Gparted

this was a problem as i couldn't log into gnome until  i deleted some stuff.

My question is as i look at my files i should have a lot more space available!!
My home folder which has all of my media is only totaling out at 46.1Gb

I have checked my trash bin and nothing is in there and tried to see if there were any hidden files and nothing...

Other than going through every dir. in the file system does anyone have any clue why this discrepancy would be happening or where this phantom data is???

Thanx!

---

### Post by glennric on 2008-02-25
Try going into various directories and typing
```
du -sh
```
This will tell you how much is in the directory.
Try it in your home directory first.  So type "cd ~", then the above.

---

### Post by Sam Lars on 2008-02-25
You can use the Disk Usage Analyzer in Applications > Accessories...

---

### Post by mkoehler on 2008-02-25
Also, if you know when this problem began to occur and a file that you modified recently before it happened, you can search for newer / newly modified files with the following commands:

```
sudo find /home/mike/Desktop -cnewer <filename>
```

---

### Post by Cchhrriiss on 2008-02-25
Well i rebooted my system and now it won't boot up...great

I had been running into errors during the splash screen and it would give an error can't rem now but pressing alt+ctrl+del would allow it to boot all the way after the error

now it says the partition has been booted 22 time without being checked and after it checks it all it says something about a missing or duplicated block...more than i feel like messing with tonight

thanx for the help so far...I will try posting another thread tomorrow to see how difficult fixing this error will be  (with more info of course)

maybe time for the old re install   made it a couple of months this time :)

---

