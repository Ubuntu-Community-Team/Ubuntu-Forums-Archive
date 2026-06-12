---
title: "And the terminal command..."
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by lsweet on 2007-08-10
So I'm setting up Wine, got it installed, configured, etc.  I assume it works.

Then I followed through a couple guides to get World of Warcraft running -- but I changed a few steps.  I'm dual booting off a Vista machine and instead of copying files off a CD/DVD I figured I'd navigate to my NTFS partition and just run wine from there.

But... it doesn't like the spaces in the directory names, Program Files for example doesn't seem to register.  Any ideas on how I can get around that?  I'd have to have to rename all those folders ('cuz I'm super lazy).

---

### Post by bodhi.zazen on 2007-08-10
use " "

wine "/media/windows/Program Files/..."

or tab completion :

wine /media/windows/Progr<tab> ...

or "escape" the white space with a \ :

wine /media/windows/Program\ Files/ ...

---

### Post by nhandler on 2007-08-10
The easiest way would be to use the auto completion feature. Start typing "Program" and hit tab. You should see it fill in the "Files" part.

The second option is to manually escape the space. To do this, enter "Program\ Files".

Edit: Bodhi.zazen beat me to it.

---

### Post by lsweet on 2007-08-10
Awesome.  Thanks for the quick response.

---

