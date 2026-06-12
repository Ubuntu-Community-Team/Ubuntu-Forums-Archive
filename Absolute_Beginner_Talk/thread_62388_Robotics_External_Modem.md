---
title: "Robotics External Modem"
date: 2005-09-04
forum: Absolute Beginner Talk
---

### Post by whythehellcantilogon on 2005-09-04
Hi, this may seem like a dumb question to some of you but I have no idea what I am doing. I tried installing my internal Conexant modem but finally realized that it isn't possible because of the Riptide drivers not working with the new kernel,  so I was at a garage sale and they had a  "3Com U.S. Robotics 56k Faxmodem V.90" the model number is 005689-03. This is a faxmodem for Macintosh.

My question is whether I can make this work my computer which isnt a mac? The cables it came with have what looks like a printer cable on the end that connects to the modem, and the other end looks like a keyboard cable but the little rectangle is replaced with 2 pins.

Sorry for my ignorance, any help would be greatly appreciated.

---

### Post by Kapre on 2005-09-04
[QUOTE=whythehellcantilogon]Hi, this may seem like a dumb question to some of you but I have no idea what I am doing. I tried installing my internal Conexant modem but finally realized that it isn't possible because of the Riptide drivers not working with the new kernel,  so I was at a garage sale and they had a  "3Com U.S. Robotics 56k Faxmodem V.90" the model number is 005689-03. This is a faxmodem for Macintosh.

My question is whether I can make this work my computer which isnt a mac? The cables it came with have what looks like a printer cable on the end that connects to the modem, and the other end looks like a keyboard cable but the little rectangle is replaced with 2 pins.

Sorry for my ignorance, any help would be greatly appreciated.[/QUOTE]
 whythehell - I dont think there would be a problem using this modem (as long as it is working). AFAIK, all modems are serial. The connector is different(I'm not familiar with it) but I am sure you you can buy a serial cable (the one that looks like a printer cable but has an old mouse type connector) so that you can hook it up to your computer's COM2.

K

---

### Post by trash on 2005-09-04
give me a couple of hours and I can tell you if it works.. i have both a mac USR modem and a pc(x86) cable. I was told by a windows guy that it would not work on a windows system so we'll see soon if linux can do it :)

back soon.

---

### Post by trash on 2005-09-04
i said a couple of hours because I thought i would have trouble finding the modem, i love organized chaos :)

worked like a charm... the cable is about $8. canadian, the one i got is a 8-9 pin rectangular serial.

good luck:)

---

### Post by whythehellcantilogon on 2005-09-04
Ok, I happened to have one of those cables in a huge box of stuff in my basement. After I configured it I tried to connect with wvdial, it dials and sounds alright but when it tries to log me in it gets errors

Login:
--> Looks like a login pronpt.
--> Sending: guitarfool1999
eillas830
Password:
--> Looks like a password prompt.
--> Sending: (password)
** Bad Password

The password I entered is defenitely right.
It tries this again then starts something called pppd and eventually closes altogether. I also tried using pppconfig but I think that has the same problem, although i cant be completely sure because it dosen't tell me what it is doing. 

Does anyone have any ideas what this could be caused by

---

### Post by trash on 2005-09-04
no idea sorry.
I tried this in breezy using the System->admin->networking and it worked first time

---

### Post by whythehellcantilogon on 2005-09-04
well.... I did some research and found out that it is because I am trying to use aol. this sucks because I haven't been able to find any good instructions on how to fix this problem yet.

---

### Post by whythehellcantilogon on 2005-09-05
I am so happy, after an entire weekend of reading and such I am finally on the internet with linux  :-)    \\:D/ 

thanks for the help you gave me (and everyone else whose posts I read)

I think i need to take a break and catch up on some of the homework that has been piling up. ](*,)

---

