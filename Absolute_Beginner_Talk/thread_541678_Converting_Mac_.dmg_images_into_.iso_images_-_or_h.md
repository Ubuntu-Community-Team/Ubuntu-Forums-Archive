---
title: "Converting Mac .dmg images into .iso images - or how else to open a .dmg file???"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-09-03
I have mac ".dmg" files how can I access them?

searching I found one is supposed to convert them into an .iso file

so i went here and followed instructions

[http://www.arsgeek.com/?p=905](http://www.arsgeek.com/?p=905)

I have AceoneISO2 installed (which works as I tested other PC iso files on it)

when doing the Arsgeek script it gives me (PropertyList is corrupted)

but it still generates an .iso file

so trying to mount the iso file which was converted from .dmg in AcetoneISO2, but nothing happening

can someone please help

thanks

=========================================
=========================================
Arsgeek says:

I recently came across a handy script that allows you to convert a Mac OSX or Apple&#8217;s iPod (iPod firmware generated images) to standard .iso files.

You&#8217;ll need to have perl installed. Also, you may need to add an additional dependency in the form of a perl zlib module. So, here&#8217;s how to install it:

    sudo apt-get install libcompress-zlib-perl

    cd /usr/bin

    sudo wget [http://www.blinkenlights.ch/gnupod/dmg2iso.pl](http://www.blinkenlights.ch/gnupod/dmg2iso.pl)

Now, in my Ubuntu install I had to make one change to the dmg2iso.pl script.

    sudo gedit dmg2iso.pl

At the very top you should see a line that says &#8216;#!/usr/local/bin/perl&#8216;. This tells the script where to find perl. On my installation, perl is located in &#8216;/usr/bin/perl&#8216;. So change that line if you need to.

Now let&#8217;s make it excecutable.

    sudo chmod 777 dmg2iso.pl

Back to your home directory now.

    cd

If you have a .dmg file in your home directory (or any directory) called bloodspell.dmg, and you want to convert it to a .iso file you can type:

    dmg2iso.pl bloodspell.dmg bloodspell.iso

The script will take care of the rest.
=========================================
=========================================

---

### Post by meindian523 on 2007-09-03
Did you change anything in the script or follow the instructions letter by letter including the change Arsgeek made in the script?

---

### Post by MozartlovesUbun2 on 2007-09-03
> **meindian523 said:**
> Did you change anything in the script or follow the instructions letter by letter including the change Arsgeek made in the script?

yes did change script as Arsgeek mentioned:

(At the very top you should see a line that says ‘#!/usr/local/bin/perl‘. This tells the script where to find perl. On my installation, perl is located in ‘/usr/bin/perl‘. So change that line if you need to.)

---

### Post by meindian523 on 2007-09-03
Should not change exactly as any tutorial says.Arsgeek mentioned "on **my** Ubuntu installation,it's here,--PATH--"

Find where your perl is by

```
which perl
```

then change the first line of the script accordingly....

for example:my which perl gives:
```

easwarh@l1nuxr0cks:~$ which perl
/usr/bin/perl
easwarh@l1nuxr0cks:~$ 
```

eh??

---

### Post by MozartlovesUbun2 on 2007-09-03
> **meindian523 said:**
> Should not change exactly as any tutorial says.Arsgeek mentioned "on **my** Ubuntu installation,it's here,--PATH--"

Find where your perl is by

```
which perl
```

then change the first line of the script accordingly....

for example:my which perl gives:
```

easwarh@l1nuxr0cks:~$ which perl
/usr/bin/perl
easwarh@l1nuxr0cks:~$ 
```

eh??

yup i did check

my path is the same

/usr/bin/perl

---

### Post by meindian523 on 2007-09-04
> **MozartlovesUbun2 said:**
> 
Now, in my Ubuntu install I had to make one change to the dmg2iso.pl script.

    sudo gedit dmg2iso.pl

At the very top you should see a line that says ‘#!/usr/local/bin/perl‘. This tells the script where to find perl. On my installation, perl is located in ‘/usr/bin/perl‘. So change that line if you need to.
Sice your which perl gave /usr/bin/perl and not /usr/local/bin/perl,it means that the first line should be #!/usr/bin/perl and NOT #!/usr/local/bin/perl.Got it??

---

### Post by bulletxt on 2007-09-05
Just a quick note:

AcetoneISO2 is able to mount true *.DMG mac files!  

opent the program, go up under the voice utilities and then Mac OS --> Mount.


You should be able to mount it. I have never tested it but give it a try!

---

### Post by MozartlovesUbun2 on 2007-09-07
> **bulletxt said:**
> Just a quick note:

AcetoneISO2 is able to mount true *.DMG mac files!  

opent the program, go up under the voice utilities and then Mac OS --> Mount.


You should be able to mount it. I have never tested it but give it a try!

ok i did try it out mount directly inside AcetoneISO2

didn't work!

---

### Post by bulletxt on 2007-09-08
Lol

I forgot to tell you, please first check if it is a true dmg hfs file system.

open a terminal and type "file nameimage.dmg"

if it says it is data then AcetoneISO2 won't mount it at it is pure binary data.
If it says something like HFS file system then there must be some bug in AcetoneISO2

let me know ;)

---

