---
title: "3gp converter for Ubuntu?"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by asakurax on 2007-08-17
my sister has a "Sony Ericsson" cellphone, and she wants me to transfer videos to her cellphone. the problem is that the software she got with the cell phone is not Linux compatible

any suggestions?

thanks

---

### Post by Steveway on 2007-08-17
Did you try mencoder?
Check the manpage to get instructions for it.
man mencoder

---

### Post by tukuyomi on 2007-08-17
ffmpeg from [Medibuntu]("http://medibuntu.sos-sts.com/") repository can do that :)
```

ffmpeg -i videodump.avi -b bitrate -ac audiochannels -ab audiobitrate videoout.3gp

```
*bitrate* is video bitrate
*audiochannels* is a value: 1 (mono), 2 (stereo)
*audiobitrate* is audio bitrate

---

### Post by stooshbunutu on 2008-03-11
use mobile media converter ([http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm))

---

### Post by tospig on 2008-03-29
I seem to be having a bit of trouble installing MMC, and was wonding if you could help;

I've installed wine (sudo apt-get install wine)
then navigated to the folder with the .exe in it and used 'wine Mobile Media Converter' but nothing happens, it says 'Module not found'

What am I doing wrong?

---

### Post by diablo75 on 2008-03-29
All I had to do to get MMC to run was double click on it...

---

### Post by tospig on 2008-03-29
had you installed wine?

either way, that doesn't work for me

---

### Post by diablo75 on 2008-03-29
Yes, I have wine.  How did you install wine on your system?

You might try right-clicking on the file to see if a "Run with Wine" is available, or perhaps a "Run with other..." so you can select wine from a list of applications.  Perhaps exe files are associated correctly yet...

---

### Post by tospig on 2008-03-29
sudo apt-get isntall wine

---

### Post by tospig on 2008-03-29
yeah I can see the 'run with wine' and have tried it, but nothing happens

---

### Post by stooshbunutu on 2008-03-31
> **tospig said:**
> I seem to be having a bit of trouble installing MMC, and was wonding if you could help;

I've installed wine (sudo apt-get install wine)
then navigated to the folder with the .exe in it and used 'wine Mobile Media Converter' but nothing happens, it says 'Module not found'

What am I doing wrong?

You don't need wine, you just download the package, extract it, and double click on the mobile media converter file.

Make sure though you have the specially compiled version of ffmpeg that came with it in the download in the same directory as the main file, i believe this is causing the module not found error

---

