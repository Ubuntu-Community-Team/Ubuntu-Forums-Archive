---
title: "Replacing Vid card"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by darco on 2007-10-13
I am running GG RC on my old system. I currently have installed  an ATI Rage XL PCI card.  I happen to come across in my junk box an ATI AGP card but I cant identify the model. I installed it but I cant get to the desktop but I can get to the xorg file. What do I need to change to get GG to recognize  this card?

thxs
darco

---

### Post by schorsch on 2007-10-13
Please try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
in a terminal window.l

---

### Post by darco on 2007-10-13
Im such a noob, i KNEW that!!!...I ran it but it still detects my original card. Says soemthing about dual cards.....
thxs

---

### Post by schorsch on 2007-10-13
You should try to remove the PCI Card first.

---

### Post by darco on 2007-10-13
> **schorsch said:**
> You should try to remove the PCI Card first.

Heh, Im not that much of a noob :)

After running the above command, I was able to log into my desktop fine. I am now running an ATI Radeon 7500 that I completly forgot about!........Desktop effects now enabled.
I guess I need to run the flgrx drivers since under screen and graphics it still shows it under a rage pro card but under HW info it shows it properly...

thxs
darco

---

### Post by schorsch on 2007-10-13
Uhm, sorry, I am not able to help you any longer as I do not use Gutsy ....yet .... but perhaps ... in a week or so ... I prefer to you stable software and not beta ....

---

