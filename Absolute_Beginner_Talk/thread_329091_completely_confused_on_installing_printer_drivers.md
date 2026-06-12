---
title: "completely confused on installing printer drivers"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by cashman3 on 2006-12-31
I am Trying to install printer drivers for a brother mfc-7220. I downloaded the driver and tryed to unpakage it but i only get this:  sudo dpkg -i brmfc7220lpr-2.0.0-1.i386.deb
dpkg: error processing brmfc7220lpr-2.0.0-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 brmfc7220lpr-2.0.0-1.i386.deb
Please pardon my ignorance any help is much appriecated though it may take me a minute to try

---

### Post by Sigudian on 2006-12-31
if your on 6.10 (not sure about 6.06) then you could just click on the file and have a graphical installation.

if you prefer terminal window, you must ensure that you "CD" to the directory correctly, if your unsure about how to do this, just put the .deb file in your home folder and run
```
sudo dpkg -i brmfc7220lpr-2.0.0-1.i386.deb
```
its of highest importance's that your file name is correct.

---

### Post by cashman3 on 2006-12-31
ok i have installed the driver by clicking on it but my printer model is not a choice when i go to add a printer i mean it finds the printer but it isnt an option on the second step

---

### Post by Sigudian on 2006-12-31
> **cashman3 said:**
> ok i have installed the driver by clicking on it but my printer model is not a choice when i go to add a printer i mean it finds the printer but it isnt an option on the second step

what model do you have?

---

### Post by cashman3 on 2006-12-31
Mfc-7220

---

### Post by Sigudian on 2006-12-31
try [this link]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html"). i herd this how-to should work for your model.

---

