---
title: "Need help with the Wine aplication"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Andenium on 2006-06-11
ok ok so listen i need help downloading and installing the Wine aplication cuz i play a lot of warcraft3 and i also need help installing the Warcraft game any1 could help me i would apreciate it

---

### Post by Andenium on 2006-06-11
ok i just dld the wine thing and have it in my desktop how do i install it help plz!!!!

---

### Post by FredSambo on 2006-06-11
[click here for great justice.](http://www.ubuntuforums.org/showthread.php?t=149585)

---

### Post by Beej on 2006-06-11
I don't know about the game you want to play, but wine can be installed from the terminal. Programs>Accessories>terminal.

type

sudo apt-get install wine

you will then need to set wine up.

winecfg from the terminal should bring up the configuration window. You will need to auto detect your drives (drives tab autodetect). I assume the game you want to install come s on cd? If so make a note of the drive letter.

Choose the version of windows you wish to emulate in the applications tab. Click apply and close.

On my machine the cdrom is drive E. To run the setup file try

wine E:/path/tofile/setup.exe

good luck

---

### Post by Andenium on 2006-06-11
how do i know wich is my drive?
it only says CD-ROM/DVD-ROM DRIVE
and when i run the wine thing it doesnt detect them, only the drives a appear or mayb some of them are the drives i just dont know wich of them are they Oo?

---

### Post by Beej on 2006-06-12
Could you post a screenshot of your winecfg drives tab? 

Don't know whether I'll be able to help but I'll do what I can.

---

### Post by maddbaron on 2006-06-12
can u help me also?

i downloaded it and tried running winecfg and got this i couldnt go to my windows program files for some reason when i did it came back with no folders so i dragged the program into a ubuntu folder(is that a way to get it to work?)

but i have no idea what to do.

here is the attachment of where i am stuck.

---

### Post by ignorance on 2006-06-12
when you have the winecfg screen open you need to click on the tab drives. Now you can click on autodetect and wine is gonna find your cd drives but i wouldnt click on autodetect cuz i did it one time and it placed my home dir between it and my system failed to restart after that. so now you just click on add and then browse for your cd drives. you can find them undert media if im correct. now you can put the game cd in it and search the .exe file to install the game or program and chose open with wine windows emulator and then you should get a the screen to install the program or game like in windows.
i hope this can help you a bit with your problem

---

