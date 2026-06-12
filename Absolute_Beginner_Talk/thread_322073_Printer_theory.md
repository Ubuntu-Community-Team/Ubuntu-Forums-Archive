---
title: "Printer theory"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Tarnic on 2006-12-19
OK, I was thinking about this... 

I run mainly a windows network... and my system that is hooked up to the printer directly has no drivers for linux.... it is a dell a960. well i was thinking.... would it be possible to run some little app in the background on the windows system that could communicate to the linux system and accept incoming print requests? 

I dont know if there is a program that can do this already.... but can someone tell me if there is one?

---

### Post by dbbolton on 2006-12-19
samba or cups

---

### Post by vivin_west on 2006-12-19
Go to system>>administration>>printing
Open the window
Printer>>add printer
choose network printer
select windows printer(SMB)
go through the steps and you will get your printer working

---

### Post by Tarnic on 2006-12-19
> **vivin_west said:**
> Go to system>>administration>>printing
Open the window
Printer>>add printer
choose network printer
select windows printer(SMB)
go through the steps and you will get your printer working

OK smart guy... find me some drivers for a Dell a960.... none exist

---

### Post by vivin_west on 2006-12-19
ubuntuforums.org/showthread.php?t=246009 - 71k

Read this may be it will help.
Good luck!

---

### Post by vivin_west on 2006-12-20
I also suggest you install printconf from synaptic. No always necessary but will help you.

---

### Post by Tarnic on 2006-12-20
I tried to set the printer as RAW. It seemed like it was going to work... but when I got to the system... all that i saw was this...
[IMG]http://img501.imageshack.us/img501/1796/cvxcvrl8.png[/IMG]
It gets to 100%, but it takes 4x as long as it would normally, and on the printer lcd it says "printing", but there is no printing going on... So I now have no clue to what is going on with my printer setup.

---

### Post by vivin_west on 2006-12-20
Did you install printconf?

---

### Post by Tarnic on 2006-12-20
> **vivin_west said:**
> Did you install printconf?

Yes, but when i try to run it all i get is > " * Restarting Common Unix Printing System: cupsd                         [ ok ] 
If printconf was unable to install all of your printers, please visit
[http://www.linuxprinting.org/](http://www.linuxprinting.org/) for printer information and support from fellow
users."

I give up on it for tonight... I need some friggin' sleep. I will play with it tomorrow, and let you know if i am successful with anything

---

