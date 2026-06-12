---
title: "GRUB defaults and permissions"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by smudje on 2006-09-04
Hi all, sorry if this has been asked before and sorry if i sound really dumb. I want to get windows to be my default os to boot. However when trying to change GRUB it says i dont have the correct permissions. When checked i dont but it won't let me change the tick boxes to be able to write to the file, any help appreciated. Thanks 
Again sorry if i sound really dumb, Ace when it comes to windows, newbie when it comes to linux

---

### Post by Iarwain ben-adar on 2006-09-04
Hi, no problem mate :D

Just type in this
```
sudo gedit /boot/grub/menu.lst (if you have Ubuntu)
kdesu kate /boot/grub/menu.lst (if you have Kubuntu)
```

That should do the trick.

Btw, welcome to the forums ;)


Iarwain

---

### Post by elpuerco on 2006-09-04
at the prompt prefix your command with sudo kate <file name> and it will ask for your password and away you go

---

### Post by elpuerco on 2006-09-04
Also......make a backup of the grub file first!

---

### Post by smudje on 2006-09-04
thanks guys, that seemed to work, but why dont i have those permissions automatically ? Or is it because its a system file ? Oh and thankyou for the welcome, im sure i'm going to be here a lot !

---

### Post by smudje on 2006-09-04
> **elpuerco said:**
> Also......make a backup of the grub file first!

Oooops too late

---

### Post by bluefrog on 2006-09-04
you need to be super user to edit such a file.

open applications / accessories / terminal
in the console write
sudo gedit /boot/grub/menu.lst
and hit <enter> on your keyboard.

From now on be careful to what you write.
You need to change default 0 to the number corresponding to windows.

the section numbering starts at 0. in your case I believe you need default 4.
save the file, you're done.

WARNING. when you will be updating your linux kernel, the numbering will change, you will need to edit the file again

James

---

### Post by Iarwain ben-adar on 2006-09-04
Lol :D

You don't have those permissions, because it's a system file (meaning: messing with the system without you knowing what you do is a bit dangerous)

That's why you don't have rights (i think) :D


Iarwain

---

### Post by smudje on 2006-09-04
> **bluefrog said:**
> you need to be super user to edit such a file.

open applications / accessories / terminal
in the console write
sudo gedit /boot/grub/menu.lst
and hit <enter> on your keyboard.

From now on be careful to what you write.
You need to change default 0 to the number corresponding to windows.

the section numbering starts at 0. in your case I believe you need default 4.
save the file, you're done.

WARNING. when you will be updating your linux kernel, the numbering will change, you will need to edit the file again

James


I assume its no 4 bacause i miss out "the other operating" note as it is only a note, because i counted down to 5 ?

---

### Post by smudje on 2006-09-04
> **bluefrog said:**
> you need to be super user to edit such a file.

open applications / accessories / terminal
in the console write
sudo gedit /boot/grub/menu.lst
and hit <enter> on your keyboard.

From now on be careful to what you write.
You need to change default 0 to the number corresponding to windows.

the section numbering starts at 0. in your case I believe you need default 4.
save the file, you're done.

WARNING. when you will be updating your linux kernel, the numbering will change, you will need to edit the file again

James


I assume its no 4 bacause i miss out "the other operating system" ?

---

### Post by Iarwain ben-adar on 2006-09-04
If you're not shure, post your menu.lst ;)


Iarwain

---

### Post by bluefrog on 2006-09-04
might be 5 in that case if there is no # in front of other operating system.

Anyway try. at the worst it won't start windows automatically and you will use the arrows to select the right one and you will be good for another sudo gedit ... operation

James

---

### Post by smudje on 2006-09-04
sthanks guys, so far i've only altered the defaultboot, which as by now is gonna be ubuntu, so when ive stopped playing with this os, i'll return that to false and set windows as my default , although saying that im getting very very keen on ubuntu, trying to find faults at the minute and failing. :)

---

### Post by Iarwain ben-adar on 2006-09-05
Just a tad of advice,

make shure you know how to make a backup via command line, and how to restore  it :D
These things can make your life alot easier ;)


Iarwain

---

### Post by elpuerco on 2006-09-05
Also, the fact that you are altering a file that can ultimately stop your system from working....

DO ensure you make a backup

DO research what it is you are trying to do before you do it

To modify things that you are not sure about is dangerous!!

Time invested researching will save much pain later :D

---

### Post by Iarwain ben-adar on 2006-09-05
Or when you don't research, and face the problem,
you can learn alot if you try to repair your system :D (that's what always happens to me :) )


Iarwain

---

### Post by Xanthus on 2006-09-05
Grub starts counting at 0, I know this much but I'm very new and I'm having the exact same problem, I tried these solutions but when I paste "sudo gedit /boot/grub/menu.lst" into the prompt I get a password box then a line that says "sudo: gedit: command not found".  I'm using Xubuntu, I again know nothing so help would be greatly appreciated.

---

### Post by Xanthus on 2006-09-05
OK, hopefully I'm not a complete idiot but, that was even dumb of me when I don't know what I'm doing at all.  So, I installed the gedit package and I retryed the command, it seems to have worked though it through up a bunch of error messages, I've yet to reboot but I think it worked.  If it doesn't I'm sure you'll hear from me.

---

### Post by Iarwain ben-adar on 2006-09-06
Hi Xanthus,

you can just type
```
sudo nano /boot/grub/menu.lst
```

and edit the file like that :D


Iarwain

---

### Post by hartunnoo on 2006-10-22
why ubuntu does not come with boot setup interface. It makes life easier.

---

