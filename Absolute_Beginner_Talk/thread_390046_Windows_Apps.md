---
title: "Windows Apps"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by RealG187 on 2007-03-21
What is the best way to run Windows apps?

I know of Wine which is free, but that has limitations, is there a "perfect solution" that is preferably free [or cheap, and I cant use a credit card either... :( ]

Is wine the only free one?

---

### Post by charles.g.moore on 2007-03-21
If you are not going to do any gaming you can use VMWare [http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)
As far as perfect I don't know, free...yes
I use VMWare server with XP and FedoraCore5 and have had no problems (I have'nt fired up Windows in about 2 months, no need for it)

---

### Post by lamalex on 2007-03-21
crossover office is damn good, its about 40 USD, i don't know if you need a credit card or can mail a check. theres a 30 day trial if you want to at least test it

---

### Post by RealG187 on 2007-03-22
> **charles.g.moore said:**
> If you are not going to do any gaming you can use VMWare [http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)
As far as perfect I don't know, free...yes
I use VMWare server with XP and FedoraCore5 and have had no problems (I have'nt fired up Windows in about 2 months, no need for it)

I have a Pentium III, 677 MHz, will that be in my way?

---

### Post by RDUBBALO on 2007-03-22
Check out [http://www.winehq.org/]("http://www.winehq.org/") there they have a list of available programs that will work. Also you can go to X-Chat and talk to someone from winehq and ask some questions for more info on it

---

### Post by RealG187 on 2007-03-22
A little off topic, but Is there an easier way other than the terminal, can I make shortcuts to my Windows Apps and put them on my desktop?

---

### Post by anaconda on 2007-03-22
> **RealG187 said:**
> A little off topic, but Is there an easier way other than the terminal, can I make shortcuts to my Windows Apps and put them on my desktop?

you can do that easily with wine (once you get the program working..)
just right-click on the desktop, select create launcher and and the correct command to the "command" place.. eg. wine /home/me/file.exe

---

### Post by RealG187 on 2007-03-22
> **anaconda said:**
> you can do that easily with wine (once you get the program working..)
just right-click on the desktop, select create launcher and and the correct command to the "command" place.. eg. wine /home/me/file.exe

By /home/me/file.exe do you mean" wine /home/me/file.exe" or "/home/me/wine file.exe", or does i t know what to do? Cuz when I double click or right click it doesn't work....

---

### Post by anaconda on 2007-03-23
I meant "wine /home/me/file.exe" without the quotes.. which is wine and the path to the file you want to run using wine.

works with me.. so it should work with you too..

ofcource you will need a file file.exe in directory /home/me

---

### Post by MrKlean on 2007-03-23
I would use virtualbox... install windows 2000 or xp...and run what I need in a vm 9virtual machine).  You might find there are lots of replacements for windows... contrary to what windows users say !   I found everything I needed to run my business in Ubuntu ; )  And VirtualBox is lots faster than VMWare ; )

---

### Post by RealG187 on 2007-03-23
> **anaconda said:**
> 

ofcource you will need a file file.exe in directory /home/me
Or couldn't I just change the path to the folder I have?

Also, I hear that if I type in "Sudo Wine " [with a space], it will let me drag and drop the EXE I wish to run...

---

