---
title: "Installing/Using Wine"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by The AlGorenator on 2007-03-16
i've installed wine from the add/remove program folder but for some reason, i can neither see it in any menu, nor [obviously] use it. helps please!

---

### Post by eljalill on 2007-03-16
Whyt happens if yu open a terminal and type 
winecfg
? 
Wnother window should open then...
if it doesn't, is there an error message?

---

### Post by The AlGorenator on 2007-03-16
wine: creating configuration directory '/home/james/.wine'...
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
Failed to open the service control manager.
fixme:ole:ITypeInfo_fnRelease destroy child objects


it comes up with that, and opens wine configuration, so apparently it's installed, but i still can't use it.

---

### Post by steven8 on 2007-03-16
You don't 'see' wine as an installed program.  This threw me off when I first tried it as well.  It is available through the terminal, or via right-click.

winecfg, gives you a program to configure different aspects of wine for programs you have installed.

winefile, gives you a windows like browser to find the programs you ahve installed or want to run.

However, all that being said, wine doesn't seem to like your video card.  What kind of card do you have?

---

### Post by The AlGorenator on 2007-03-16
it's an ATI M22 [Radeon Mobility M300]

---

### Post by eljalill on 2007-03-16
If you want to istall a programm with wine,
you download the windows installaion file (.exe or so).
Then you navigate to that file in the terminal.
Once you are in the right folder you type
```
 wine YourProgram.exe 
``` or whatever the installation file is called.
It should then install.

Same, if you have the program installed,
you open it through 
```
wine YOUR PROGRAM
```
once you are in the right folder. Otherwise you can also just ive the full path instead of YOUR PROGRAM. 

Does that work?

---

### Post by The AlGorenator on 2007-03-16
sorry, uber noob question, how do i navigate to the folder in the terminal?

---

### Post by eljalill on 2007-03-16
:) no worries: there are no stupid questions...
You open a terminal.
You will see seomthing like ```
user@computer:  
```
you are now in your home directory. (same as when you have nautilus, the GUI file browser open and are looking at your home folder)
cd means change directory. with this command you can navigate into any other directory.
```
 cd .. 
``` will bring you one level up.
so
```
 cd ONEOFYOURFOLDERS 
```
will bring into that folder. of course you can type a longer path at a time, if you want to.
if you are not so sure about the exact name of a folder use cd and start typing the name, then hit the tab-key . In case it is already clear , the chell will complete the name.

OK? Anything unclear?

---

### Post by The AlGorenator on 2007-03-16
You explained really well, good work. Thanks also, i got it going, however, half way through the install, it randomly aborted. I think it was because i didn't change the directory to one on my linux disk

thanks much.

---

### Post by eljalill on 2007-03-16
Happy to help.
Some general remarks, that might be useful: 
man cd   or man AnyOtherCommand opens the manual for this command. You leave the manual again through typing "q".
And 
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
list all kinds of commands that are useful to know. (Just a note: "bash" is the name of the terminal shell you are usuall operating in).

Best of luck furtheron!

---

### Post by The AlGorenator on 2007-03-16
oh! i forgot, with wine, can i run windows programs off my windows partition whilst booted in linux?

---

### Post by eljalill on 2007-03-16
As far as I know, you cannot. The programs need to be setup with wine in ubuntu, so that they can run in wine with ubuntu. 
I haven't really found a better explanation, I just know, it is not recommended / does not work....

---

