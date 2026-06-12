---
title: "Odd behaviour..."
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by aj5string on 2007-09-19
I tried to open some programs today, but nothing happens.  it seems to be mostly games in the menu, also Open office.  I click on them and sometimes it thinks a bit, ither times nothing happens.

Firefox, evolution, gaim and other stuff is fine.

Any ideas?

Alex.

---

### Post by quixotic-cynic on 2007-09-19
Which programs? You could try running them in a terminal by typing their name and then see if any errors are displayed. E.g. typing oowriter may launch open office writer.

---

### Post by aj5string on 2007-09-19
Cheers for the reply...

I tried running Open office writer from the terminal as suggested (cos its one of the programmes that wouldnt open) and got this in the terminal;

> alex@alex-desktop:~$ oowriter
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

** (process:6390): WARNING **: Unknown error forking main binary / abnormal early exit ...
alex@alex-desktop:~$ 

Does that mean anything?

Cheers. Aj

---

### Post by GavinZac on 2007-09-19
your x (dislay) session appears corrupted somehow. i cant give any technical explanations (i would probably be described as a beginner too) but i would suggest saving your open work and hitting ctrl+alt+backspace to restart X and see if it has any positive effect.

---

### Post by Ant_Merlin on 2007-09-19
> alex@alex-desktop:~$ oowriter
Xlib: extension "XFree86-DRI" missing on display ":0.0".
Xlib: extension "XFree86-DRI" missing on display ":0.0".

** (process:6390): WARNING **: Unknown error forking main binary / abnormal early exit ...
alex@alex-desktop:~$ 

Hi what drivers/ graphics card have you got, this message indicates that they are not setup, installed correctly for you card.

---

### Post by aj5string on 2007-09-19
When should i press control-alt-delete?

Cheers.

---

### Post by aj5string on 2007-09-19
> **Ant_Merlin said:**
> Hi what drivers/ graphics card have you got, this message indicates that they are not setup, installed correctly for you card.

Well... i've got a ATI card.  It was all good, until i tried to install the new ATI drivers - then my machine wouldnt boot (i guess i did something wrong) anyway, im now using the vesa (?) drivers.  I guess a driver/graphics card issue would make sense (it fits in time wise with stuff stopping working).

How can i chang to some drivers that will work/set up the drivers i need?

Cheers. Aj.

---

### Post by Ant_Merlin on 2007-09-19
> Well... i've got a ATI card. It was all good, until i tried to install the new ATI drivers - then my machine wouldnt boot (i guess i did something wrong) anyway, im now using the vesa (?) drivers. I guess a driver/graphics card issue would make sense (it fits in time wise with stuff stopping working).

How can i chang to some drivers that will work/set up the drivers i ne

I have an ATI X1650 and am running restricted drivers ok with compiz-fusion.

First of all you need to reistall ati drivers.

open a terminal and type:

> sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=xv

this will reistall ATI drivers ok.

If when you type sudo aticonfig --initial and it doesnt save file the use sudo aticonfig --initial --force.

let me know if it works.

---

### Post by aj5string on 2007-09-20
> **Ant_Merlin said:**
> I have an ATI X1650 and am running restricted drivers ok with compiz-fusion.

First of all you need to reistall ati drivers.

open a terminal and type:



this will reistall ATI drivers ok.

If when you type sudo aticonfig --initial and it doesnt save file the use sudo aticonfig --initial --force.

let me know if it works.

Do i just copy and paste that into terminal, or do i need to enter each line seperatley?

Also, do i need to un-install/disable enything first?  And do i need to download anything else?

Cheers again. Alex.

---

### Post by misfitpierce on 2007-09-20
If you need to reinstall the ATI drivers can be done so easilly with a little program script known as envy.

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu11_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu11_all.deb)

---

### Post by quixotic-cynic on 2007-09-20
> **aj5string said:**
> Do i just copy and paste that into terminal, or do i need to enter each line seperatley?

1) It is best to do each line seperately.

you may want to use *sudo apt-get upgrade* instead of *sudo apt-get dist-upgrade* as the latter is a little extreme - unless you know what it does and do want to upgrade ubuntu to the next version (eg dapper to edgy etc).

2) *If* you cannot get the closed-source ones to work then you could use the open ati drivers that are installed by default (rather than having to resort to vesa). If you do this it would probably be a good idea to remove the closed drivers with *sudo aptitude remove xorg-driver-fglrx* (or apt-remove instead of aptitude). However, I would try the other method first.

3) When you asked about ctrl+alt+del ... the poster who suggested it actually said ctrl+alt+backspace (which, whilst near delete & simmilar in function, has a different result under Ubuntu). It will just restart the X Windows environment (so, either dump you to a prompt where you have to type startx or manage to restart on it's own). It was a fair suggestion but I think your problem is a little more entrenched.

---

