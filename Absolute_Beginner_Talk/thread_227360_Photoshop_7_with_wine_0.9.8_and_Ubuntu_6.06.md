---
title: "Photoshop 7 with wine 0.9.8 and Ubuntu 6.06"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by walterius on 2006-08-01
I managed to get PS7 installed, mainly by clicking on the defaults. But it won't load or run.

Chin Wong's excellent Manila Standard Today column (for today 08-01-06) says one must enter the following at a terminal:

WINEDLLOVERRIDES=wintab32=n wine "C:Program FilesAdobePhotoshop 7.0Photoshop.exe"

But no matter how I type it, whether exactly as shown above (i.e. as in his column), or with Windows spaces, and/or back-slashes, and/or forward slashes, I always get a file not found message.

Can anyone help?

I am using an upgrade version of PS7, so it needs to check for a previous version. It does, and it apparently finds it, because it then apparently successfully completes the install.

Previous posts do not address any part of this situation.

WIndows 2000, AMD Athlon 2000+, 512 MB RAM, 120 GB HDD, Ubuntu 6.06 LTS.

Thank you in advance. #-o 
Walterius

---

### Post by Iarwain ben-adar on 2006-08-01
> **walterius said:**
> 
WINEDLLOVERRIDES=wintab32=n wine "C:Program FilesAdobePhotoshop 7.0Photoshop.exe"

Hi,
Shouldn't the program path be with /'s ?

like this i'd think
> WINEDLLOVERRIDES=wintab32=n wine "C:/Program Files/Adobe/Photoshop 7.0/Photoshop.exe"


Iarwain

---

### Post by walterius on 2006-08-01
I tried that. :confused: Read the post for the various things I tried.:p

---

### Post by oolunchbox on 2006-08-02
I've managed to get Photoshop 7 running. It's been a pain and if someone could help a little it would be awesome.  I figured out that by CD-ing to the Program Files\Adobe\Photoshop 7.0 directory in the terminal and then running ```
WINEDLLOVERRIDES=wintab32=n wine Photoshop.exe
``` works perfectly.  My plea is that someone make a script to simplify the process.

EDIT: I just got it.

Creat a link to an application.
In the application tab where it says 'Command' put:
```
WINEDLLOVERRIDES=wintab32=n wine '/home/YOURCOMPUTER/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe'
```

As long as you installed to the default directory and change YOURCOMPUTER to the name of your personal computer it should work like a charm.

I've also attached a Photoshop icon in png format.

---

### Post by walterius on 2006-08-04
I'll try your tip. Sounds good. Thanks.

---

### Post by walterius on 2006-08-04
IT WORKS!!!!!!! THANK YOU!!!!!!!

(Of course, "it works" in Linux means "enough of it works to make it worthwhile, but parts of it that I use a lot don't work at all."

Still, I am grateful. That's one more small step towards not needing Windows.
=D>

---

### Post by cantormath on 2006-08-04
> **walterius said:**
> I managed to get PS7 installed, mainly by clicking on the defaults. But it won't load or run.

Chin Wong's excellent Manila Standard Today column (for today 08-01-06) says one must enter the following at a terminal:

WINEDLLOVERRIDES=wintab32=n wine "C:Program FilesAdobePhotoshop 7.0Photoshop.exe"

But no matter how I type it, whether exactly as shown above (i.e. as in his column), or with Windows spaces, and/or back-slashes, and/or forward slashes, I always get a file not found message.

Can anyone help?

I am using an upgrade version of PS7, so it needs to check for a previous version. It does, and it apparently finds it, because it then apparently successfully completes the install.

Previous posts do not address any part of this situation.

WIndows 2000, AMD Athlon 2000+, 512 MB RAM, 120 GB HDD, Ubuntu 6.06 LTS.

Thank you in advance. #-o 
Walterius

I got PS7 working well using crossover office.  Crossover configs your wine nicely.

---

### Post by mcgarry83 on 2006-10-15
DUDE oolunchbox, you are awesome!!! I have been trying for MONTHS to get this to work, always with stupid errors and crap. Who would have ever thought that simply CD'ing to the dir and running the exe there would fix everything. If you were a chick I would kiss you!!! Thanks again bro!

---

