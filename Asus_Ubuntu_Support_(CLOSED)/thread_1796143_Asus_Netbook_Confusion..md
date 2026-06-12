---
title: "Asus Netbook Confusion."
date: 2011-07-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ColeFournier on 2011-07-03
I recently installed Ubuntu onto my sisters laptop after having problems validating an old copy of windows XP, and was amazed at how simple and awesome it seemed to be. She loved it, and i decided to reformat my netbook to run Ubuntu as well.

All seemed well at first, untill trying to install ANYTHING. 

-when entering any search items into the software center, it searches infinitely for hours without returning any information.

- I looked online and learned i could download all the programs i wanted from the Terminal, but any and all programs I attempt to download or install are returned with a variety of errors, and do not install (So far I have tried skype, flash, and a variety of other very frequently used programs, none of which have installed onto my sytem.) 

Im really quite frustrated and could really use some help.

Thanks.

---

### Post by snowpine on 2011-07-03
Welcome to the forums Cole!

Which model ASUS netbook do you have? 
Which Ubuntu release did you install?
Are you connected to the 'net?

---

### Post by ColeFournier on 2011-07-04
Im using an Acer Aspire One 532h-2807 netbook, or at least thats the information on the bottom of the computer.


Connected to the internet, and downloaded 11.04 Im pretty sure. Whatever Natty Narwhal was up 3 days ago from the Ubuntu website.
The problem isnt that the programs arnt downloading from Terminal, they seem to begin to download, and even complete the download. Its the actual installation that is resulting in the error I believe.

---

### Post by snowpine on 2011-07-04
Since you are familiar with the Terminal, can you try the following commands and copy & paste the output here (you can tag it as "code" to make it easier to read):

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

