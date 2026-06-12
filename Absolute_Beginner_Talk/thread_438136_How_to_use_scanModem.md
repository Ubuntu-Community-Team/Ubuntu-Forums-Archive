---
title: "How to use scanModem"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-05-09
I've loaded Ubuntu 7.04 yesterday and the program works wonderfully. I'm very happy with it.

I do have some quirks to work out. The first and foremost one which I direly need
help with, is that Ubuntu says it does not have drivers for most dial-up modems.

Assuming that Ubuntu does not have the drivers for my modem, then Ubuntu wants
me to find out the "chip set" of the modem. Ubuntu says, it needs that so I can then find
out what driver it needs. To find out the "chip set", Ubuntu recommended
I download a program called "scanModem"-- which I did download. They said
I could put it in my Windows 98, in the C:\temp folder. I did that. But then, Ubuntu
gave me around 4-5 lines of commands that they want me to type in in Ubuntu. I tried
writing them in in the "terminal" application, but it rejected the lines.
This is something I am entirely unfamiliar with, and I neither know what the command
lines mean, nor do I know how to use them.

Here are the command lines:

ls/mnt        (they say this line is to see the path to my Windows disk)
cp/mnt/msdos/temp/scanModem.gz.
gunzip scanModem.gz
chmod +x scanModem
sudo ./scabModem

Please let me know how to use all this. (That is, assuming Ubuntu in fact does not
have the driver for my modem.)

Also, I wanted to take the scanModem program and paste it into Ubuntu myself, but I could
not understand the pathway "mnt/msdos/temp". They said that the "."
at the end of that line is to put the file in the "current directory" 
-- but I do not know where that is either....

---

### Post by ewankho on 2007-05-10
It might be easier if you copy the file using nautilus or some other graphical file manager if you are not familiar with entering commands. Just copy scanModem.gz file to your home directory and then continue from step 3 (using the terminal). The first two instructions assumes you downloaded the file in Windows to directory c:\temp and it just wants you to copy that file to your linux directory.

---

### Post by PhutterMan on 2007-05-19
Where did you find scanModem?!

I've been looking for it to use on my machine but I always get a 403: Forbidden when I try to download it.

Maybe it's a waste, I'm only at here for two weeks, but I want to be able to go online (via dialup) on my ubuntu laptop instead of my parents' windows computer.  Anyway, I'm trying to find scanModem so I get the winmodem on this computer to work.

---

### Post by Bachstelze on 2007-05-19
[http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

---

### Post by PhutterMan on 2007-05-19
Did you try the link?  It gives me a 403.  I'm trying on a windows computer with IE7 with an internet connexion; still, I don't see why that would matter.  I definitely can't get it from that link, though, and I've tried several times.  I've also tried going up a level, and I see it there, but again, when I go to it, I get a 403: Forbidden.

---

### Post by Bachstelze on 2007-05-19
Yep, works fine here... I've uploaded it elsewhere, try that one :

[http://fkraiem.free.fr/scanModem.gz](http://fkraiem.free.fr/scanModem.gz)

---

### Post by edunagin on 2007-05-19
Sounds to me like you are using a Winmodem. They do not work on Linux. Unless that file is something that I never heard of. I think you gotta get a real modem (externel will be the best bet, and you should be able to get a used one cheap)

HTH.Peace............ed

---

### Post by Bachstelze on 2007-05-19
Some Winmodems can run in Linux, it requires some work but it can be done.

---

### Post by PhutterMan on 2007-05-19
Well, I get the same from that link.  I guess it's this computer then... thank you very much for that link, though.  I'll figure it out...must be the browser or something.  Sorry for the dumb question; thought something was wrong on their end.  I definitely have a softmodem, but I think it's not impossible to get it to work, though we shall see, and the same for the original poster.

---

### Post by Bachstelze on 2007-05-19
What if you try to just right click and save target as ? I could also email it to you if you want, it's very small...

---

### Post by PhutterMan on 2007-05-19
No luck with the save target as, either.  I don't know quite what to do about it, nor do I want to mess with anything on this computer, as far as I can help it, since it belongs to my parents (with whom I'm staying for a couple of weeks, hence the trying to get my laptop's modem to work) and they're pretty protective of it.

 I'd really appreciate it if you could email it to be, though I'm really sorry to cause you the trouble.  My address is nfutterman [at] berkeley [dot] edu.

Thank you so much!!

---

