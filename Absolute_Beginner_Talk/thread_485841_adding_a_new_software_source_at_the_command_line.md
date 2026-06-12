---
title: "adding a new software source at the command line"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by broth420 on 2007-06-27
I am trying to install SlimServer on a LAMP install.  I have run into  snag (and as you can guess, I am pretty new to Ubuntu)
How do I do this...

[I]To install the latest testing release (Slimserver 6.5.3) update your /etc/apt/sources.list to include: 

deb [http://debian.slimdevices.com](http://debian.slimdevices.com) testing main[/I]

---

### Post by Inxsible on 2007-06-27
GUI way :
System -> Administration -> Software Sources. ( Or is it System -> Preferences -> Software Sources :-k , I can never rbr )
 
Navigate to the Third Party tab and add the source there.
 
 
CLI way:
```
gksudo gedit /etc/apt/sources.list
```
At the bottom of the file add the line that you have.  i.e. *deb *[_[COLOR=#bd5900]http://debian.slimdevices.com[/COLOR]_]("http://debian.slimdevices.com/")* testing main  *
 
Save, exit and then do
 
```
sudo aptitude update
```

---

### Post by Seisen on 2007-06-27
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
```
```
sudo vim /etc/apt/sourcesl.list
```

That will open your source  list and then you  can add it.

If you don't know how to use vim there is what you need to do.

```
shift + I 
``` lets your write in the file
```
:w
``` will save the file
```
:q
``` will close out vim

afterwards all you to do after adding that to your source list is

```
sudo apt-get update
sudo apt-get upgrade
``` or aptitude whichever one you use.

---

### Post by Papi-KB7VGW on 2007-06-27
gksudo gedit /etc/apt/sources.list

I would save a copy as bkup before I make any changes  Hope this helps:D

must be too slow a typist

---

### Post by az on 2007-06-27
[QUOTE=Seisen;2922463```
sudo vim /etc/apt/sourcesl.list
```

That will open your source  list and then you  can add it.

If you don't know how to use vim there is what you need to do.
.[/QUOTE]

Or just use nano to edit a text file

sudo nano /etc/apt/sources.list

CTRL-O to save CTRL-X to exit.

---

### Post by lunarcloud on 2007-06-27
use nano, it feels like a simple grafical text editor in that the commands are right there for you to see, and it acts sanely. vim sometimes acts weird.

---

