---
title: "crontab executes only two of three commands"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by dant on 2006-07-12
Using current versions of ubuntu and Opera I am attempting to set up random tag lines for my email.  Here's what has happened so far --

After a bit of trial & error, flipping through various books and consulting online sources, I've come up with the following entry for my crontab:

# m h  dom mon dow   command
*/10 * * * *  /home/dant/crontab_scripts/mail_taglines

The file mail_taglines looks like this:

cd /home/dant/.opera//mail; cp signature1.txt signature2.txt; fortune >> /home/dant/.opera//mail/signature2.txt

signature1.txt provides my name, preceeded and followed by two line feeds. This file then overwrites signature2.txt, which then has the output of fortune appended.

I've tested the script from the terminal, both from /home/dant and from /home/dant/.opera//mail. It works both places, no problems, but when run by crontab the last section ( fortune >> /home/dant/.opera//mail/signature2.txt ) does not process -- the fortune is not appended to the signature2.txt file.

Any thoughts (and all words of wisdom) are appreciated.

---

### Post by mikeym on 2006-07-12
crontab seems to operate with a reduced PATH try entering the full one. You can get this with 'whereis fortune'.

---

### Post by mazirian on 2006-07-12
It' sprobably in /usr/games/fortune whihc is probably not part of your $PATH.  You could either add it to your $PATH, or preferably do what was mentioned above.  A slightly better bash script might be:

```

#!/bin/bash
NAME="Your Name HERE"
SIG="--\n$NAME\n$(/path/to/fortune)"
echo -e $SIG > $HOME/path/to/signaturefile.txt

```

That will automatically overwrite anything in the signature file without going through all that copying and so forth.

---

### Post by dant on 2006-07-13
Two excellent suggestions!  Many thanks to mikeym and mazirian!!

I now have the following entry in crontab:

*/05 * * * *  /home/dant/crontab_scripts/mail_taglines


The file mail_taglines contains this:

#!/bin/bash
NAME="Dan Wilterding"
SIG="\n\n$NAME\n\n$(/usr/games/fortune)"
echo -e $SIG > $HOME/.opera//mail/signature2.txt


Having found it necessary to modify the file containing fortunes it was also necessary to either create a new dat file or put up with some incomplete fortunes.  To create a new dat file was easy; run the following command from whereever your fortunes file is located:

strfile -r fortunes fortunes.dat


That's it!  Simple, once you know how.

Thanks again for the help,

Dan

---

