---
title: "Extracting .bin Archives"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by ChrisBC on 2007-02-11
Hi folks,

I'm feeling very stupid at the moment, because even after I managed to get Edgy up and running on my system, installed everything I needed, migrated all my data from XP, and got ATI's big desktop running flawlessly, I can't figure out how in the hell to extract files from a .bin archive.  Archive Manager won't read them, and they're not executable.  What program should I be looking at here?  Thanks for your time.

Chris

---

### Post by taurus on 2007-02-11
Applications -> Accessories -> Terminal (and make sure you are in the right directory where the file is)
```
chmod 755 filename.bin
./filename.bin
-or-
sudo ./filename.bin
```

---

### Post by the_nomad on 2007-02-11
here's a link that might help you [http://monkeyblog.org/ubuntu/installing.html#installer](http://monkeyblog.org/ubuntu/installing.html#installer)
good luck,
me.

---

### Post by nickoli_02 on 2007-02-11
.bin files aren't archives, they are (normally) binary executables.

---

### Post by ChrisBC on 2007-02-12
Perhaps this stems from my long-time suffering under Windows, but I was under the impression that a .bin file was an image of a cd.  I used to download them all the time... there would be a .bin and a .cue so you could mount the file using daemon tools or alcohol 120%.  You could also extract files directly from the .bin if you didn't want to mount the image.

I'm afraid those suggestions didn't work.  I got the error ```
./junglestrike.bin: 1: Syntax error: "(" unexpected
```

I have downloaded a number of Sega Genesis games, and an emulator, but all the games are in .bin format.

---

### Post by tbroderick on 2007-02-12
You need to run the emulator then load the rom. Follow these directions to install gens;

[http://ubuntuforums.org/showthread.php?t=166980](http://ubuntuforums.org/showthread.php?t=166980)

---

### Post by ChrisBC on 2007-02-12
Wow.  Sorry to waste all your folks' time.  It's working fine, and I feel slightly dumber now that that's figured out.  Thanks for all the quick responses.  These forums were invaluable in bringing me into the Ubuntu fold.

---

### Post by rzrgenesys187 on 2007-10-06
> **ChrisBC said:**
> Wow.  Sorry to waste all your folks' time.  It's working fine, and I feel slightly dumber now that that's figured out.  Thanks for all the quick responses.  These forums were invaluable in bringing me into the Ubuntu fold.

If it makes you feel better i was in the same predicament as you :)

---

### Post by anna611 on 2007-10-10
Nowhere on the internet is explained in which directory it is the best to install the bin-file.

Java for example has also such a file, but i know that's installed with apt in /etc/lib/

Please advise me

---

