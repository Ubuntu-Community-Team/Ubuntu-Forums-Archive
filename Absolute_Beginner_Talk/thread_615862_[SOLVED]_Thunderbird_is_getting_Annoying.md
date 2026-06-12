---
title: "[SOLVED] Thunderbird is getting Annoying"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by It_Was_Luck on 2007-11-17
Okay so I downloaded Mozilla Thunderbird from this method:

[https://help.ubuntu.com/community/ThunderbirdNewVersion#head-bf9c39b3c4100a7ab792839c6c5fd253bfd7b561](https://help.ubuntu.com/community/ThunderbirdNewVersion#head-bf9c39b3c4100a7ab792839c6c5fd253bfd7b561)

Except they didn't have the Thunderbird 2.0 for Gusty there at the time so I went ahead and used the on for Fiesty even though I was running Gusty. So it installed version 1.5, but then it autoupdated to 2.0.

Now the problem is everytime I open it and I get mail. my computer beeps and locks up the program, i then have to force quit, then I open it again and if I didn't receieve any mail I can check that one I recieved before it froze.

So my question is does anyone know how to fix that, or should I uninstall thunderbird, then reinstall it the new way. Also how would I uninstall it...

---

### Post by daimaru on 2007-11-17
why didn't you just 
```
sudo apt-get install thunderbird
```
works fine for me under gutsy
EDIT: just read the link you included and i guess you did just that :) but quite frankly this worked for me without any problems

---

### Post by bazzbc on 2007-11-17
If you open Synaptic package manager and search for thunderbird you can then select the option to completely remove.

Then open a terminal and apt-get install thunderbird.

This will install 2.0.0.6

---

### Post by rfruth on 2007-11-17
Tried a different profile luck ?

---

### Post by daimaru on 2007-11-17
uninstall your thunderbird 
```
sudo apt-get remove thunderbird
```
and then reinstall the gusy version

---

### Post by It_Was_Luck on 2007-11-27
Well I tried every method here... The synaptic complete removal, the terminal removal... And in the end when I reinstalled Thunderbird, all my setting were the same and everything and I had marked it for COMPLETE removal... 

So now even when I do a complete removal, and when I install the new one from the terminal I still get the same problem, ideas?

---

### Post by irish_flu on 2007-11-27
There's probably a profile folder being left behind.  Do you have any mail, data, addresses, etc you want to save?

If you DO NOT want to save anything, only want to "start fresh":

Open up your Home folder (under "places")

Go to "View" and select "Show Hidden Files"

Delete the folder called ".mozilla-thunderbird" (the other mozilla folder is for Firefox- leave that one alone).

Boom, your profile is gone.  Now you can install Thunderbird Fresh.  Hope it works!

PS, don't forget to go back to "view" and uncheck "show hidden files"; I dunno about you, but my home folder is too cluttered if that's turned on.

---

### Post by rfruth on 2007-11-27
I agree, get rid of your profile (.mozilla-thunderbird, back it up if necessary) else you can mark for removal (whatever) till your blue in the face ...

---

### Post by XVII on 2007-11-27
> **irish_flu said:**
> 
Go to "View" and select "Show Hidden Files"

Delete the folder called ".mozilla-thunderbird" (the other mozilla folder is for Firefox- leave that one alone).

Boom, your profile is gone.  Now you can install Thunderbird Fresh.  Hope it works!

This would be the way to go if you don't have anything important you need to save.

---

### Post by It_Was_Luck on 2007-11-27
It works now, thanks guys.

---

### Post by Dapman01 on 2007-11-27
what is so different about thunderbird anyway

---

