---
title: "Autoclean"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Nezing on 2007-06-17
All was well earlier today,but tonight,when I type in Terminal:

sudo apt-get autoclean

in order to clear "junk" off the system,the Terminal just says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

What now?

Silly me.And I thought Ubuntu was going to be easy.  :(

---

### Post by shae on 2007-06-17
Type the following in terminal
```
sudo dpkg --configure -a
```

---

### Post by steveneddy on 2007-06-17
Type this in terminal:

```
sudo dpkg --configure -a
```

Then

```
sudo apt-get autoclean
```

Dang - you beat me to it.

---

### Post by w4ett on 2007-06-17
> **Nezing said:**
> All was well earlier today,but tonight,when I type in Terminal:

sudo apt-get autoclean

in order to clear "junk" off the system,the Terminal just says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

What now?

Silly me.And I thought Ubuntu was going to be easy.  :(

Did you attempt to follow the instructions?  Not meaning to sound funny though...but in the terminal type:

sudo dpkg --configure -a

to correct the problem.

---

### Post by Nezing on 2007-06-17
Cheers guys.That did the trick.After "a few beers",my brain was a little fuzzed  :)


:guitar:

---

