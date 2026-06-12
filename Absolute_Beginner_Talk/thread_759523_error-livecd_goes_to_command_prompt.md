---
title: "error-livecd goes to command prompt"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by gilmey on 2008-04-19
hello all :)
im a real newbie here so plz have patience with me :)
all my life i used windows but i wanted to check to see if i can replace it to linux -cause im tired of hte blue screens and the viruses
from all i read i saw that ubuntu is a very popular distro and it has a live cd option so i decided to check it out- but i guess i ahve bad luck cause from the beggining i have a problem that i have no idea what it means-
i try to run ubuntu -the latest beta version  -it shous the ubuntu logo and it loads for a few seconds but then it goes to a command prompt  that says 
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands

any idea what is wrong?-i simply wanted to test ubuntu before even instaling it....

thnx in advance

---

### Post by bumanie on 2008-04-19
It is likely that there is a conflict of some kind, probably hardware. What are your computer specs?

---

### Post by nicedude on 2008-04-19
First I see you are talking about the beta version, since that didn't work you. Download the latest STABLE version 7.10 gutsy live CD - also make sure you download the correct 7.10 live for your processor ( 32bit or 64bit ). Although the 32bit will work on a 64bit system it won't work vice versa. I believe they recommend 512mb of ram for running the Live CD, so you might look at that factor too. 

With some computers the live CD will not load and for those there is the Alternate install CD which does not have a live option, It just comes up and you can select to install Ubuntu and away you go. You could post some more info about what brand & model computer you are trying this on as when people look at your problem it really helps them see what the real problem might be.

Good luck and please post your results of round two :-)

---

### Post by gilmey on 2008-04-19
ok i have a intel core 2 duo proccesor
2 gb of ram 
nvidia gefoce 8600 card
i have windows xp installed on my hard drive -but i dont think thats the problem cause im trying the livecd option
now i have a sata hard disk and not an ide one- i found a possible solution   : -Boot from your Live CD 
Don’t hit Return yet. First hit the F6 key to modify the command line parameters 
Replace “quiet splash” with “all_generic_ide irqpoll” 
Start booting 
what do u guys think?

when i get home ill check it -if it  doesnt work ill get the latest stable version

---

### Post by bumanie on 2008-04-19
Certainly your system won't have any problem running ubuntu. I'd check the cd for errors and do a md5 checksum to ensure the download came through clean. If that all comes up OK, try the alternate cd or wait one week for the final release of hardy.  I'm running hardy on a similar system (amd x2 4800+, 2g ram, 8600gt nvidia card) with no problems.

---

### Post by gilmey on 2008-04-20
ok - i  tried on my mothers computer and it worked without any problems so i knew that my cd isnt corrupted - so i tried replacing "quiet splash" with all_generic_ide_irqpoll - and it worked !!!!
any idea what can cause this??

---

