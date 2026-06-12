---
title: "modem help gzip"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Rasputen Bel Kuhr` on 2006-11-09
Okay i recently got edgy eft and downloaded scanModem.gz them trasferred it to ubuntu desktop and further followed the instructions for getting the modem to work as shown on the ubuntu website. This is what i did and my problem in terminal

$ cd ~/Desktop
$ gunzip scanModem.gz
$ chmod +x scanModem
$ ./scanModem
bash: ./scanModem: cannot execute binary file
$

what is wrong how do i get it to function?

---

### Post by Bachstelze on 2006-11-09
(sudo) chmod +x scanModem

---

### Post by Rasputen Bel Kuhr` on 2006-11-09
I now get the file to almost work but it tells me that /dev/modems does not exist doesn't create and won't let me why not HELP(another folder doesn't exist either)

Also does anyone have a good ubuntu tutorial

---

### Post by Jussi Kukkonen on 2006-11-09
HymnToLife, why would sudo be needed?

Rasputen Bel Kuhr`, the file is in a format that is not recognised. Two choices:
1. the file (shell script) begins with the line
#!/bin/some-program
and some-program doesn't exist.

2. The file is in a binary format the kernel doesn't recognize.


Open the file in gedit or another editor and (if it is readable) paste the first line here. If the file is not readable do 
```
file scanModem
```
in the same directory and paste the output here. Then we'll see what the error message was about.

---

### Post by Jussi Kukkonen on 2006-11-09
RBK, have you read the instructions? It does say *Ubuntu user: replace last command by "sudo ./scanModem"*. Try that and the dev nodes should be created. 

Before that, be sure that you know what is happening and that you trust the program 100% -- sudo runs things with superuser rights...

---

### Post by Rasputen Bel Kuhr` on 2006-11-09
Okay so now i've got the protgramme to work but it isn't allowed to create folders and for some reason neither am i so i try using the sudo command to no effect HELP

---

### Post by Jussi Kukkonen on 2006-11-09
> **Rasputen Bel Kuhr` said:**
> Okay so now i've got the protgramme to work but it isn't allowed to create folders and for some reason neither am i so i try using the sudo command to no effect HELP

Please give more details when you have problems. In this case, say what exactly isn't working (what the error message is), and how sudo isn't working (copy-paste the relevant commands and outputs from your terminal).

---

### Post by Rasputen Bel Kuhr` on 2006-11-09
khan@ZORG:~$ cd ~/Desktop
khan@ZORG:~/Desktop$ sudo ./scanModem
Password:
ls: /dev/modem: No such file or directory
ls: /dev/ttySL0: No such file or directory

This is the error and this is done directly after ubuntu 6.10 was installed so it's running on defaults

---

### Post by Jussi Kukkonen on 2006-11-09
> **Rasputen Bel Kuhr` said:**
> khan@ZORG:~$ cd ~/Desktop
khan@ZORG:~/Desktop$ sudo ./scanModem
Password:
ls: /dev/modem: No such file or directory
ls: /dev/ttySL0: No such file or directory

This is the error and this is done directly after ubuntu 6.10 was installed so it's running on defaults

Strange. I'm not a scanmodem expert, so I'll ask just to be sure: Did you check if it created the *Modem*-directory with the output files?

---

