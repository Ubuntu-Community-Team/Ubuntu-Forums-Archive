---
title: "Help installing program through Wine"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by ImThatNerd on 2008-02-23
I downloaded a program, photoshop. And I extracted the .rar to get the folder with all the files in it and .exe

I copied that whole folder over to my 'name' drive. So for me it was dragging it all over to 'ryan'

I was just curious what the command is to install it? I did this earlier, but forgot how and lost source that taught me how to.


I tried: wine photoshop/setup.exe but it didn't work. Does caps matter?

---

### Post by SpiderGorilla on 2008-02-23
If you've got an MSI installer, you need to open up terminal, navigate to the folder where you have the MSI file and then type:

wine msiexec nameofyourinstallfile.msi

If it's an EXE, you need to right-click the EXE and choose "Open with Wine Windows Emulator"

That should get it going.

---

### Post by nsimeone2000 on 2008-02-23
Caps matter.

---

### Post by ImThatNerd on 2008-02-23
> **SpiderGorilla said:**
> If you've got an MSI installer, you need to open up terminal, navigate to the folder where you have the MSI file and then type:

wine msiexec nameofyourinstallfile.msi

If it's an EXE, you need to right-click the EXE and choose "Open with Wine Windows Emulator"

That should get it going.

I right clicked the .exe and hit open with wine and got some errors:

.\AutoPlay\main.ini

MAIN_FILE_VERSION

PRODUCT_REGISTERY_PARENT

PRODUCT_REGISTERY_Key

these were pop up errors.

---

