---
title: "Wine Help"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by bedelc on 2007-03-25
Hi,

I am new to Ubuntu, but am beaing assisted by a friend who is not so new, He has recommended that I use WINE to open my Windows applications. 

I have attempted this, but keep encountering a problem. I followed a tutorial from the Psychocats website, but it still isnt working for me. When I double click on the executable file, I get a message that it cant display the program. 

Can anybody give me any advice on what I might be doing wrong, 

I have downloaded and installed WINE. I am running Dapper.

Please let me know if I need to provide more information. Again, thanks.

Parker

---

### Post by eljalill on 2007-03-25
Which programs are you trying to run?
And what version of wine do you have? (type wine --version in a terminal to find out)

---

### Post by zvacet on 2007-03-25
Did you run** winecfg**?
You can install program to work under wine in several ways.I´ll try to explain two for you and you pick one you like better.

First way

1.Download exe in any of your folders(maybe it is good idea to be folder maned programs or something like that but it is not imperative for installation,jusr for you to know where your exe-s are)
2. wine /home/yournickname/yourfolderofchoice/your_program_exe
Shortcut will be made on your desktop and just click on it

Second way

Download exe in any folder.Copy exe to .wine(hidden home folder)>C>program files
```
winefile
```
Go C>program files>your exe>double click

---

