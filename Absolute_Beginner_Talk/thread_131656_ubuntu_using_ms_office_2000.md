---
title: "ubuntu using ms office 2000"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by regiemon on 2006-02-16
i already installed office 2000 to ubuntu. but dont know how to run it?

how do run ms office 2000?

---

### Post by Madpilot on 2006-02-16
You'd have to use Wine, or CrossoverOffice, or something like that. It won't run natively in Ubuntu.

OpenOffice is installed by default in Ubuntu, though - **Application menu --> Office --> (various OOo bits) Writer/Calc/etc**

---

### Post by nalmeth on 2006-02-16
How did you install it? I think office needs CrossoverOffice by codeweavers, and if you've done it that way, I think you will have a cxoffice directory in your home folder.

OpenOffice is the open alternative. For a simpler but able writer try abiword.

---

### Post by az on 2006-02-16
Office 2000 is proprietary software.  Free-libre software is all about software not being someone else's property.  It's your computer.  Your computer is useless without software.  You should have the freedom to know what your computer is doing as well as the freedom to improve the software yourself.  

Would you buy a car with the hood welded shut?

---

### Post by Qrk on 2006-02-16
Windows .exe files are treated like documents, you "open" them with the wine program.

---

### Post by regiemon on 2006-02-16
i also already installed wine

i tried going to terminal
then type
wine winword.exe
but the error said cannot found "winword.exe"

---

### Post by Madpilot on 2006-02-16
[QUOTE=regiemon]i also already installed wine

i tried going to terminal
then type
wine winword.exe
but the error said cannot found "winword.exe"[/QUOTE]

You've probably got to provide a path to winword.exe, or something like that

"wine /somedirectory/winword.exe" - or run the MSO setup exe first with wine. 

Frankly, it just seems far easier to learn OpenOffice...

---

### Post by regiemon on 2006-02-16
my winword location is /home/.wine/drive_c/program files/microsoft office/office/

but if i type it 
wine /home/.wine/drive_c/program files/microsoft office/office/winword.exe
still could not recognize the location.

well,i still like ms office because i'm having a hard time in using openoffice

how do you do the mso setup?

---

### Post by Qrk on 2006-02-16
cd to the directory first, then use wine:

```
cd "/home/.wine/drive_c/program files/microsoft office/office/"
wine winword.exe
```

But its easier for you to use nautilus to get to the directory, right click on "winword.exe" and select "open with custom applications" and find "wine windows emulator" in the list.

Edit: You need to place the path in quotes because it has spaces.

---

### Post by regiemon on 2006-02-16
ok now i can now use ms office!

thank you very much for your help!
thank you.

---

### Post by regiemon on 2006-02-17
btw how do i create a shortcut to the desktop?

---

### Post by Qrk on 2006-02-17
I'm not sure if this is the best way to do it or not. But I would open up gedit (Applications -->Accessories-->Text Editor) and make a text file, paste this into it. Don't forget to add your username if needed.

```

#! /bin/bash
cd "/home/.wine/drive_c/program files/microsoft office/office/"
wine winword.exe

```

and save it to your desktop as something nice, like "Word". Right click on the new file, and select properties, then permissions. Give yourself "execute" permissions. 

Now you can double click the file and select "Run" to run the winword program. You can change the icon, or do anything you like with it.


If you (like me) don't like an icon cluttering up your desktop, save it to your home folder. (or any other one, really, your choice) Right click on your panel, and add as a custom application launcher, the command

/path/to/Word


(This isn't the typical way to make a shortcut, you would normally got to right-click, "create launcher", but I don't know how to make a launcher use a bash script)

Edit: You can use the same technique to make a menu entry (using the menu editor) and a desktop launcher. I recommend using the first way to make your desktop launcher, because then you won't accidentally delete the file.

---

