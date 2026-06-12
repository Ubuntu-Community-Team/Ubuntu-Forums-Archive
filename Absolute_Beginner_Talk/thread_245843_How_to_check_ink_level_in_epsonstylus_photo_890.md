---
title: "How to check ink level in epsonstylus photo 890"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by BlueLava on 2006-08-28
Can someone help me out here please.
Ive got an epson stylus photo 890 printer and would like to know if there is a way that I can check the ink level.
It would also be great if there is an easy way to do double sided printing.

---

### Post by pbaehr on 2006-08-28
Since Epson doesn't provide Linux drivers for their printers the ink level checking may be something that is difficult to get.

As far as double sided printing goes, define "easy." The 890 doesn't have an automatic duplex feature, so the only way to create a double sided print is to print one side, reload the printer and print the second side. You pretty much need to treat it as two seperate print jobs, anyway. Is there something specific you are looking for to make it easier? Also, most word processing programs give you an option to print only even or odd pages so if you're looking to print a multipage document you'd want to select even first and then print the odd pages. You'll need to reverse the order on the first batch because the inkjet printers reverse collate the pages on each pass.

---

### Post by BlueLava on 2006-08-28
Hi pbaehr,
Thats how Im doing it now, before I upgraded to ubuntu from windowsme I just had to click the 'double sided print button' in options, thats what I mean by easy!

---

### Post by BlueLava on 2006-08-29
Hi! Can someone help me.
I read somewhere about someone recommending a programme called Turboprint to check ink levels (I cant remember where I saw it). 
Does anyone know anything about turboprint and if it will work in ubuntu, if so where can I get it & how do I install it?

---

### Post by ferebee on 2006-08-29
If you search for epson in Synaptic, there are two possibilities
for monitoring ink levels and such, mtink and escputil. I use escputil with my stylus 440 and it works well. Escputil is a commandline utility, whereas mtink is a gui application.

---

### Post by BlueLava on 2006-08-29
I have installed mtink from synaptic and restarted my computer, but I cant find it anywhere.
Could you tell me how to access it please.

---

### Post by pbaehr on 2006-08-29
Only a guess since I don't have it installed, but try opening a terminal window (Applications -> Accessories -> Terminal) and typing "mtink" without the quotes.

---

### Post by BlueLava on 2006-08-29
I typed in mtink into the terminal & a box came up which said: No access to printer device file. Please make sure that mtink has enough right for accessing the device files. Refere also to documentation.
I installed mtink-doc from synaptic, then typed in terminal mtink-doc & got message: bash: mtink-doc: command not found
Please help!

---

### Post by steve.horsley on 2006-08-29
There is a package called mtink in the repos that I have used to check the ink levels, and to perform head-cleaning.

---

### Post by BlueLava on 2006-08-29
I got this message after marking mtink for installation and clicking on apply:
Warning! Mtink requires special permissions for the device file associated with the printer. You should check your permission to see if users that could run mtink should also access this file. If you have got a normal Debian installation, this group should be lp.
Is this the reason why it doesnt work?

---

### Post by ferebee on 2006-08-29
Try > sudo mtinkin the terminal.
You'll be asked for your password and then a few basic questions to set it up.

Also in terminal try typing > man mtink to view documentation about the program.

---

### Post by coolclassic on 2006-08-29
Turboprint is here:

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

---

### Post by BlueLava on 2006-08-29
Thanks ferebee, I tried the code & it works just fine now.
I would still like to try turboprint though, see what its like. I followed your link coolclassic & right clicked: turboprint-1.94-4.i386.rpm Then: save as, Its now on my desktop and I cant open it. I typed the code sugested into the terminal (sudo apt-get install libgtk1.2) then tried again but it still wont open.
any ideas?

---

### Post by coolclassic on 2006-08-29
You will need the tar file   turboprint-1.94-4.tgz

Save the file in your home directory or where you chose. In a shell cd to the directory you have saved the file and enter the following:

tar -xzf turboprint-1.94-4.tgz 
 cd turboprint-1.94-4
 ./setup 
 UBUNTU: 
 sudo ./setup

---

### Post by msak007 on 2006-08-29
I know you're an Ubuntu user, but just to give you options there's also [this]("http://http://www.kde-look.org/content/show.php?content=20634") SuperKaramba theme (it also works with HP). I looked but unfortunately couldn't find anything similar for gDesklets.

---

### Post by BlueLava on 2006-08-30
I have saved the tar file turboprint-1.94-4.tgz on my desktop.
I dont know what this means: In a shell cd to the directory you have saved the file.
I am very new to this, is there anywhere I could learn the basics!

---

### Post by coolclassic on 2006-08-30
Open up a shell (this could be called terminal programme,bash,xterm.console)

This allows you to type commands.

When in the shell:
cd Desktop
tar -xzf turboprint-1.94-4.tgz 
 cd turboprint-1.94-4
 sudo ./setup

Type each line separately

---

### Post by BlueLava on 2006-08-30
Thanks coolclassic,
Got it working now.

---

### Post by coolclassic on 2006-08-30
No problem glad to help.
Here a web sight that offers info with Linux commands.
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by hakre on 2006-08-30
> **ferebee said:**
> If you search for epson in Synaptic, there are two possibilities
for monitoring ink levels and such, mtink and escputil. I use escputil with my stylus 440 and it works well. Escputil is a commandline utility, whereas mtink is a gui application.

I know the epson stylus color 640 quite well and can tell that epson cheats with ink levels. It's just a timer and it does not depend in any way on the real ink level that is inside the catouche.

---

### Post by ron999 on 2006-09-12
Hi
Can anyone tell me how to set up a menu shortcut for mtink, using Ubuntu 6.06 Dapper?

---

