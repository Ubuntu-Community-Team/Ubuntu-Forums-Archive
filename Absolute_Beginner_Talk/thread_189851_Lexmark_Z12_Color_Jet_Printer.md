---
title: "Lexmark Z12 Color Jet Printer"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by Aurdal on 2006-06-05
Does anyone know how I can get the Linux drivers for this printer?

---

### Post by oyvindaa on 2006-06-05
Try one of these:

[www.linuxprinting.org](www.linuxprinting.org)

[www.turboprint.info](www.turboprint.info)

---

### Post by xXx 0wn3d xXx on 2006-06-05
Look at [ this howto ](http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printers) to get it working. Even though the drivers are for a z600 printer, those drivers work with almost all Lexmark printers.

---

### Post by brownrl on 2006-06-06
I have this printer as well and I have not been able to get it to work using the two methods on here for the z600 or z35.

Dapper 6.06's bilt-in z12 driver doesn't go either.

the Z12 just simply has some different sort of protocol on the USB port that only is possible with the Windows or Mac Driver.

---

### Post by brownrl on 2006-06-06
OMG I got it to work finally,

unfortunately, i did so much stuff that I can't say for sure what made it work. None the less, I have it on the parallel port now and using the built-in z12 driver.

Make sure to turn bi-directional on and to set the color mode to black and white. Black and White is the only setting that it will work with.

I know that I tried this before and it didn't work. However, I have done so much screwing around with cups maybe now I have cleared out what was wrong.

Man now I am going invoice people!!! Arrggg!!!

---

### Post by Pawel on 2006-06-29
Hi!
I also have the same problem.

On older versions of UBUNTU - printer works. Since i got dapper - i have problems with printing on linux :(.

The printer is connected through the USB (it's recognize by the gnome-printing system but when i try to print sth: it says: "Printer fault").

Best regards
Pawe&#322;
 If i find the solution - i will write :)

---

