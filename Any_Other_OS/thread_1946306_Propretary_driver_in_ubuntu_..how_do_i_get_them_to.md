---
title: "Propretary driver in ubuntu ..how do i get them to work in BT5"
date: 2012-03-24
forum: Any Other OS
---

### Post by WickedXXL on 2012-03-24
hi!

I have installed Ubuntu 11.10 without problems and it also gets my graphic drivers later throught this propretary driver setup..

but in bt5 it doesnt get my driver..how can i find out the driver in ubuntu and move it to bt5 ?

thanks for your help!

---

### Post by Rodney9 on 2012-03-24
More information is required to help you, what is a bt5 ?

Rodney

---

### Post by uRock on 2012-03-24
> **Rodney9 said:**
> More information is required to help you, what is a bt5 ?

Rodney

I thin he/she means Back|Track5. aka Moved to Other OS/Distro Talk.

---

### Post by Dlambert on 2012-03-24
Manually install, but isnt BT used only as a live disk? Why would you need graphics drivers? Or are you installing it? I think debian tails would be better suited for you

---

### Post by UltimateCat on 2012-03-24
Digging deep into the details of a particular graphics card, determining what type of memory a particular card uses is difficult:p

I had to uninstall the proprietary driver that Ubuntu uses for what ever the reason my graphics crashes while proprietary is in use- (bizarre)

In my case (trying to be of help by sharing) my system appeared to have fglrx installed but not configured to use it so I tried running
```
ati config -- initial

```
Rebooted and checked to see if Catalyst Control Center would start.

See that you have:
/etc/X11/xorg.conf
and /Xorg.con-back up120122162143 ( I copied this file and put it into the etc/X11?xorg.conf file and than the Catalyst Control Center started and I had my graphics working again.  I did it this way:
```
sudo cp /etc/X11/Xorg.conf-backup-120122162143/etc/X11/Xorg.config

```
Course your files and numbers will be different-
The member at Linux told me"It is a system file and you have to copy it as root user or with sudo"

Or; you can Research how to manually install ATI drivers.

Hope this helps....I tried with a sincere heart-

---

### Post by WickedXXL on 2012-03-25
I have an Toshiba Satelitte 660-233

Graphics adapter as shown in WIndows is Intel HD graphics..
I alreadyx tried Nvidia and ATI but they don`t work // they don`t recognize any devices..

yeah i am talking about backtrack 5 and iI have ainstalled it !

thanks for all ur answers!

---

### Post by MadsRC on 2012-03-28
BackTrack 5's kernel is heavily modified, so just because it works on Ubuntu doesn't mean it works on BackTrack. Had the problem myself with a GMA500 that I could get, somehow, to function on Ubuntu but not on BackTrack.

---

### Post by haqking on 2012-03-28
what card is it ?

I use a Nvidia GTX 580 with an installed Backtrack 4 and Backtrack 5

Also i have a ATI card in my old BT3 Laptop.

Drivers install the same generally, though not really needed for graphics purposes (but needed for CUDA obviously) as BT is a specialist tool and not meant for end user desktop everyday use.

If its Intel it is a common problem see here [http://www.backtrack-linux.org/forums/tags.php?tag=intel](http://www.backtrack-linux.org/forums/tags.php?tag=intel)

and any further questions are probably better in the BT forums.


Cheers

---

