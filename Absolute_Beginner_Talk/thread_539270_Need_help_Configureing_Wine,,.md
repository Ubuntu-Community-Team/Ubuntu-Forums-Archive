---
title: "Need help Configureing Wine,,"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by be_direct2002 on 2007-08-31
Hello major noob here, Im trying to use wine ,,, i have two programs at the moment id like to use,, 1 being Winamp, and the other a program called Piolet, which is a music downloader... it seems to have a problem it "instals" the program but i cant run it. and winamp says something about not haveing the font arial. please help

---

### Post by splintercellguy on 2007-08-31
f you run the apps from Terminal what output do you get? For the Arial issue, just install msttcorefonts and/or copy the arial.ttf to Wine's "C:\Windows\Fonts".

---

### Post by be_direct2002 on 2007-08-31
well it runs through the install for piolet , it says something about haveing a  problem with the piolet toolbar,, which i dont think should be inportent, and ill have to try again to see what else ...

---

### Post by be_direct2002 on 2007-08-31
appearently the "core fonts" are already instaled but i dont know where to locate them,,, to copy ,

---

### Post by splintercellguy on 2007-08-31
Google for arial.ttf or copy from a Windows install to ~/.wine/drive_c/windows/fonts.

---

### Post by be_direct2002 on 2007-08-31
ok ill give it a try

---

### Post by splintercellguy on 2007-08-31
And output of running the Wine apps in Terminal?

---

### Post by be_direct2002 on 2007-08-31
no luck i googled the arial.ttf but i cant seem to get it to the wine windows fonts

---

### Post by be_direct2002 on 2007-08-31
i did try to install winzip as a test and that worked just fine

---

### Post by TeaSwigger on 2007-08-31
Hello, 

Have you checked if this Piolet is known to run under WINE?

Beep Media Player and XMMS are both much like WinAmp classic and can even use WinAmp classic skins. They're available for free & easy installation from the respositories. One of them might do the job for ya?

Do you know where wine is installed? It's in your home folder: '.wine' - it's like a simulated windows disc in there and everything installs in it. You can browse into it if you have "show hidden files" selected. The dot, like in front of '.wine' is what hides a folder. If you browse in there you can find where the program is installed. From that you can figure out the command to start a WINE program. By trying that command in the terminal, it might list errors which might give clues what's wrong.

---

### Post by be_direct2002 on 2007-08-31
tried the piolet program again and got a box that said Xtreamlok alert

DLL loading problem
or
Bebugger detected
or
Integrity violated

hmmm ?

---

### Post by be_direct2002 on 2007-08-31
ran piolet again 

got a box that said 

Xtreamlok alert
 
Dll loading problem 
or
debugger detected 
or
interity violated

---

