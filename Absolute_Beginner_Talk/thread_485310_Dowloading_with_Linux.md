---
title: "Dowloading with Linux"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by ktown on 2007-06-26
I know this is a really simple question to experience Linux users, but as a newly converted Linux user, how do I open files I've downloaded that are in a .tgz format or other file types. Look forward to the answer. Thanks.

---

### Post by supersonicdarky on 2007-06-26
those files are archives, like .zip/.rar on windows. you should be able to open them with the archive manager **file-roller** by double clicking them. also, you can **right click > extract here**

---

### Post by natman on 2007-06-26
Hi
As a sort of noob, im pleased that i actually kinda know the answer,
 tar -x "filename"
 for more help see here[HTML]
http://www.computerhope.com/unix/utar.htm
[/HTML]
also try doing this in a terminal
[HTML]man tar[/HTML]

Hope that helps:

---

### Post by ktown on 2007-06-26
i figured they were archived because of the extract option i was given, however, whenever i do extract them i'm given a bunch of files (I'm so used to the XP easy single icon to click to install). which one is the installation program (i'm brand new to linux so i hope this makes sense)

---

### Post by GSF1200S on 2007-06-26
Depending on whats in the tarball (what a tar.gz is reffered to as), you may either have executable files or a bunch of source files. If its source files, then your probably trying to install something. This can get a little more complicated, although its not usually that hard, unless you have to hunt for dependencies. Let us know what youre trying to do with the tarball. :)

---

### Post by natman on 2007-06-26
can you tell me the name of the program that you need to install? or maybe list out the files in the folder.
If there is a file called "install.sh" thats problem the installer ( like exe ), or maybe there is a .BIN. Here what you need to do
If there is a install.sh ( while working in the current directory
[HTML]./install.sh[/HTML]
If there is a BIN
try (once again in the directory
[HTML]chmod +x  "filename.bin"
./filename.bin[/HTML]

---

### Post by supersonicdarky on 2007-06-26
if you downloaded a .tar.gz/.tgz/.tar.bz file, then its probably the source code. i suggest first getting thr hang of installing programs through the synaptic package manager or throught terminal with **apt-get**. or, if the site offers a .deb download, get that instead. you can install it by double clicking.

---

### Post by GSF1200S on 2007-06-26
> **ktown said:**
> i figured they were archived because of the extract option i was given, however, whenever i do extract them i'm given a bunch of files (I'm so used to the XP easy single icon to click to install). which one is the installation program (i'm brand new to linux so i hope this makes sense)

It appears youre trying to install something. Try this:

Move the tarball to your home folder, and click 'extract here.' Whatever the folder is named, pick an easy name thats easy for you to write/remember. Im going to use wifi as an example.

Ok, you have the folder called wifi sitting there. Open a terminal and type:

cd wifi

and hit enter. You are now under the folders directory. Then type each of these individually, waiting for each step to finish. If you have any problems or questions, report back:

./configure

sudo make

sudo make install

sudo make clean

It should be installed at this point. Good Luck!

---

### Post by ktown on 2007-06-26
i've been trying to get what i had on windows back, so i've downloaded Google Earth and Python so far. Coming from windows, i'm not used to seeing the code of the files. some of the file types in the python folder are .sh and .in. Any suggestions?

---

### Post by GSF1200S on 2007-06-26
> **supersonicdarky said:**
> if you downloaded a .tar.gz/.tgz/.tar.bz file, then its probably the source code. i suggest first getting thr hang of installing programs through the synaptic package manager or throught terminal with **apt-get**. or, if the site offers a .deb download, get that instead. you can install it by double clicking.

Haha, I got ahead of myself. Yeah, its a good idea to see if add/remove applicatations, synaptic, or apt-get has what youre looking for.

add/remove applications downloads preconfigured binaries and installs them for you.

synaptic is a graphic frontend for apt-get, which itself is a terminal way of getting programs. Instead of using:

sudo apt-get install programname

I highly recommend:

sudo aptitude install programname

Its better for when you choose to remove something :)

---

### Post by supersonicdarky on 2007-06-26
in terminal go to the folder that you extracted it to, type the command **ls -a** and paste the output here

---

### Post by GSF1200S on 2007-06-26
> **ktown said:**
> i've been trying to get what i had on windows back, so i've downloaded Google Earth and Python so far. Coming from windows, i'm not used to seeing the code of the files. some of the file types in the python folder are .sh and .in. Any suggestions?

You can get python by going to add/remove programs and searching for 'python.' Dont worry about a source install. Ive always meant to install google earth :) Give me 10-15 and ill explain how I did it. And dont worry, this stuff will be easy with the tiniest of practice.

---

### Post by ktown on 2007-06-26
i tried opening doing the terminal and ./configure, but how do i designate what folder i want it to go to. i mean obviously the folder with all of the extracted files in it, but how do i let the computer know where i want it to look?

---

### Post by natman on 2007-06-26
open a the terminal and
[HTML]cd "destination"[/HTML]
as an example try pulling the desktop up eg
[HTML]cd Desktop/ 
ls[/HTML]
And there are all the desktop files, heres a tip, if typing all the llong file names is hard, type the first few characters and hit"tab" and it will guess the file, so for the above, all i did was type "cd D" and press tab

---

### Post by supersonicdarky on 2007-06-26
where did you get google earth from? all i see is a.bin file on their website

[http://earth.google.com/tour/thanks-linux4.html](http://earth.google.com/tour/thanks-linux4.html)

to install .bin files: [http://cutlersoftware.com/ubuntuinstall/#installer](http://cutlersoftware.com/ubuntuinstall/#installer)

also since you dont seem to know how to use the terminal: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by ktown on 2007-06-26
hey i think i finallyyyyyyy got it. thanks a lot guys i know it was easy for yall but i'm not used to actually having control over my os. thanks!

---

### Post by GSF1200S on 2007-06-26
> **ktown said:**
> hey i think i finallyyyyyyy got it. thanks a lot guys i know it was easy for yall but i'm not used to actually having control over my os. thanks!


Cool, congrats on the install! Let us know if you have any more issues- it gets easier with practice.

---

