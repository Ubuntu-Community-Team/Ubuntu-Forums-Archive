---
title: "Another ATI drivers thread..."
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by aj5string on 2007-09-18
HI...

I put the new drivers on my machine last night.  Turned it on this morning and it wont go into ubuntu, i get a load of text etc, and it says there is an error (something about gui).

Is there something quick and easy i can do?  Rollback or something similar?

Cheers. Aj.

---

### Post by overdrank on 2007-09-18
> **aj5string said:**
> HI...

I put the new drivers on my machine last night.  Turned it on this morning and it wont go into ubuntu, i get a load of text etc, and it says there is an error (something about gui).

Is there something quick and easy i can do?  Rollback or something similar?

Cheers. Aj.

Hi you can try and reconfigure your xorg. Use the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Answer a few questions and then reboot. ```
sudo shutdown -r now
``` Hopefully this will get you to the GUI good luck!

---

### Post by misfitpierce on 2007-09-18
I usually just erase the xorg when something goes wrong and then itll load using mesa junk. From that point I reload the backup of my xorg with gui.

sudo rm -r /etc/X11/xorg.conf

That erases then enter startx and waalaaa

---

### Post by aj5string on 2007-09-18
> **overdrank said:**
> Hi you can try and reconfigure your xorg. Use the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Answer a few questions and then reboot. ```
sudo shutdown -r now
``` Hopefully this will get you to the GUI good luck!

Cool...

i did that and im back in!

I chose the vesa drivers (they were highlighted already) - is that the best choice?  I know i didnt install the ATI ones properly and will try again at some point, but i dont really use ubuntu for games so its not the end of the world....  

CHeers. Alex.

---

### Post by Kowalski_GT-R on 2007-09-18
yep, Vesa is ok.

my Ubuntu screwed big time too with ATI drivers. I guess I can wait for Gutsy Gibbon.... 
ciao,

Andre

---

