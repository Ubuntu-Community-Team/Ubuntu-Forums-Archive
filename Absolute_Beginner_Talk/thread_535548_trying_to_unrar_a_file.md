---
title: "trying to unrar a file"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by blinkja on 2007-08-26
i installed unrar free version from synaptic package manager i am trying to find out how to open the files with unrar free 

couple things i tried 
right click rar file click properties > open with > there is no unrar free version just archive manager

can somebody point me to where can i get or open with unrar free ?

---

### Post by chrome307 on 2007-08-26
Archive manager extracts RAR files

---

### Post by nucinin on 2007-08-26
Archive manager will just extract any .rar files :popcorn:

---

### Post by kellemes on 2007-08-26
> **blinkja said:**
> i installed unrar free version from synaptic package manager i am trying to find out how to open the files with unrar free 

couple things i tried 
right click rar file click properties > open with > there is no unrar free version just archive manager

can somebody point me to where can i get or open with unrar free ?

unrar is a commandline tool, so use it from the terminal.
type "man unrar" for howto use it.

---

### Post by blinkja on 2007-08-26
no manual entry for unrar :sad:

---

### Post by blinkja on 2007-08-26
ok i got it 
i am newbie so i want a command line please somebody 

the files are in desktop.

thanks

---

### Post by Majorix on 2007-08-26
```
sudo apt-get install rar unrar
```

Then right click the rar file, and select Extract Here.

Do things the visual way, live longer :guitar:

---

### Post by KIAaze on 2007-08-26
Have you tried installing the non-free version?
Choose "unrar" instead of "unrar-free".

I have never tried unrar-free, but unrar has always worked for me.

---

### Post by blinkja on 2007-08-26
work fine 

thanks :)

---

### Post by blinkja on 2007-08-26
sorry i have to ask one more questions

i have K3b installed but it does not recognize .nrg files i search for nero in spm and there was nrg2iso i installed it now please how to extract? 


thanks again

---

### Post by blinkja on 2007-08-26
from the programmer website i type command line

./nrg2iso image.nrg image.iso

I get  **No such file**
trying to get it correctly from half an hour :sad:
and i did typed image name correctly 
please help
the file is in Desktop :)

---

### Post by blinkja on 2007-08-26
It seems that image.nrg is already an ISO 9660 image 

can a rename of .nrg file to .iso do the trick?
i dont want to waste DVD :)

---

### Post by KIAaze on 2007-08-26
If you are sure that it's already in ISO format it should work.

However, if it's a .nrg and not .iso, it probably won't, otherwise there wouldn't be a program to do such a conversion.

Are you sure you entered the command with the right filename and that you ran the command from the directory containing the .nrg?

---

### Post by blinkja on 2007-08-26
thanks for the reply
i rename to iso and open in k3b it did mdhchechsum :guitar:
and got something like

e21712f...................


and there are publisher, prepare id information

i think i am ready to go? 

just making sure.......

---

### Post by bluezdood on 2007-08-26
> **chrome307 said:**
> Archive manager extracts RAR files

Uh, since when?  It's not natively supported.  Not sure what sources you're reading but spouting off on something you know nothing about doesn't help.

---

### Post by Majorix on 2007-08-26
I believe it DOES extract .rar files. Thats how I have been doing it for months ;)

---

### Post by Delkster on 2007-08-26
> **bluezdood said:**
> Uh, since when?  It's not natively supported.  Not sure what sources you're reading but spouting off on something you know nothing about doesn't help.

I'd guess that it uses the command-line unrar tools for doing the actual work. In other words, yes, from a user interface point of view the archive manager does extract RAR archives as long as you have the an unrar command-line tool installed -- the unrar tools don't come with a separate graphical user interface.

---

