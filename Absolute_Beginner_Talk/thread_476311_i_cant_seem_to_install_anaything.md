---
title: "i cant seem to install anaything"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by TrevorRS on 2007-06-17
hi, this is my first post and i am new to ubuntu i have used other distros before a long time ago but ubuntu seems to be the best desktop at the minute!

now to the problem i have downloaded sevral games designed for linux ie enemy territory but when i try to install i get an error

'gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.'

and i got the file from file shack

i have also tried a few other games designed for linux and had problems what am i doing wrong?

Cheers

Trevor

---

### Post by PaulFr on 2007-06-17
gedit is an editor - I dont think  you wish to edit the game's binary :-)

Perhaps you can open a terminal and check whether the downloaded file that you are clicking on, has execute permissions turned on. You may have to do **chmod +x <filename>** to make it executable, then run it.

---

### Post by Ozeuss on 2007-06-17
i haven't really tried to install any games on linux (well, except frozen bubble, i think :)), maybe you should look into specific howto. 
anyways, it seems that you are trying to open a binary file with gedit. if you trust the file origin, you simply have to dbclick it and run it (or give it execution permission).

---

### Post by TrevorRS on 2007-06-17
hmm... but i have been able to install limewire no problems...

when i double click on all the games i have downloaded it still comes up with this error

'archive type not supported'

and where exactly do i input all the comands i keep seeing?

Cheers

Trevor

---

### Post by zvacet on 2007-06-17
[https://help.ubuntu.com/community/InstallingRunPackage]("https://help.ubuntu.com/community/InstallingRunPackage")

---

### Post by TrevorRS on 2007-06-17
> **zvacet said:**
> [https://help.ubuntu.com/community/InstallingRunPackage]("https://help.ubuntu.com/community/InstallingRunPackage")

thank you very much :D

Trevor

---

### Post by TrevorRS on 2007-06-17
hmm... now i do not have permission to write to any directory on my hard drive to install the game! :(

how do i fix this?

sorry for all the questions i feel like a right noob!

Trevor

---

### Post by avik on 2007-06-17
> hmm... now i do not have permission to write to any directory on my hard drive to install the game!

Make sure you're preceding the commands with sudo, and when it asks for your password, enter your user password.  Nothing will show up as you type; that's normal.

---

### Post by TrevorRS on 2007-06-17
where do i put the commands in?

excuse the noob

---

### Post by sumitc on 2007-06-17
open applications->accessories->terminal.
when you run a command that requires root permission,precede the command by sudo and enter the password....then u gain superuser powers and r able to run commands that require root privileges.
 Sumit

---

### Post by RomeReactor on 2007-06-17
Hi. The commands are entered into the terminal (Applications-->Accessories-->Terminal). Also, don't worry about your questions; we are/were all new to Linux at some point, so ask away! ;)

---

