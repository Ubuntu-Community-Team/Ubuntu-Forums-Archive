---
title: "Ubuntu 6.06 and Firefox 2"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by tknee on 2007-01-20
Hi

I saw on the FIrefox site a version 2.0 for linux i686 but I have no upgrade options on my current installation (Firefox 1.5 on Ubuntu 6.06. I downloaded the firefox tar and decompress it but I dont know how to insatll it and the readme said nothing.

Can we install Firefox 2 on Ubuntu 6.06? And if so, how?

Thanks a million

---

### Post by Iarwain ben-adar on 2007-01-20
Hiya,

Welcome :wink:

Try this:
```
./configure
make
sudo make install
```

Do this when you are in the folder that you decompressed, in the terminal.
(if you don't know how to get a terminal, press Alt-F2, and type "terminal", withouth "")

When you type in ./configure,
you will see alot of info scrolling down. Don't worry :D

When it stops, see what is the last line it printed. If it is something about "checking for .. " and then says "no" as answer, do a ```
sudo apt-cache search XYZ
``` where XYZ stands for the thing configure was checking for.
Do this untill you get no more "checking for ..." stops. If it stops nicely (no more errors), proceed with the second command.
And as last, the third command.


This should get you going,
if in doubt,
ask :wink:


Iarwain

---

### Post by housam on 2007-01-20
Read [this thread ]("http://www.ubuntuforums.org/showthread.php?t=327163&highlight=install+firefox+2")it may help answering your questions.

---

### Post by srunni on 2007-01-20
Check out [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) for a script written by aysiu that will install Firefox 2.0 for you. Much easier than manually compiling the Mozilla tarball.

---

### Post by pissedoffdude on 2007-01-20
> **tknee said:**
> Hi

I saw on the FIrefox site a version 2.0 for linux i686 but I have no upgrade options on my current installation (Firefox 1.5 on Ubuntu 6.06. I downloaded the firefox tar and decompress it but I dont know how to insatll it and the readme said nothing.

Can we install Firefox 2 on Ubuntu 6.06? And if so, how?

Thanks a million

There should be an executable file called firefox or firefox.bin in it.  Just extract it to the location u want it and run the executable.  If you want u can create a launcher and have it appear in applications>internet.

---

### Post by tknee on 2007-01-20
Well guys, All I have to say is WOW!

This place rocks.

:guitar:

---

### Post by housam on 2007-01-20
I've done it with [this guide ]("https://help.ubuntu.com/community/FirefoxNewVersion")and it runs fine.
Good luck

---

