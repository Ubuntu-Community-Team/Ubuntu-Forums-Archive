---
title: "Installed grub/ ubuntu 7.10 cant find vista"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by illy on 2007-08-28
Hi everyone,

(Warning ABSOLUTE newbie here.) can barely use command line and still struggling a bit.

Having lots of fun with linux (and plenty of beginner headaches :) )

Anyway that aside I am having trouble accessing my vista partition in grub. it shows the generic ubuntu and the other 2 standard options for linux. for the other OS category it has vista/foghorn bootloader. when i aaccess this vista starts then i get ERROR in big red letters across the screen and cannot recover.dat. When i enter ubuntu I can see the Vista OS partition is there (have usd oem recovery disk so pretty sure its working). 

How do I find out the vista hda designation and then how do i add that to grub? I have had a look on the forums for about an hour but can't find anything on the first part of my question. Thanks for your time, thoughts and patience in advance.

cheers,
          Illy

---

### Post by reset3x on 2007-08-28
Hint: always defrag your windows partiton before installing Ubuntu.... You need to edit your /boot/grub/menu.lst..


```
man grub]
```

```
man grub menu.istl 
```

---

### Post by reset3x on 2007-08-28
Hint: always defrag your windows partiton before installing Ubuntu.... You need to edit your /boot/grub/menu.lst..


```
man grub]
```

```
man grub menu.list 
```

---

### Post by reset3x on 2007-08-28
Hint: always defrag your windows partiton before installing Ubuntu.... You need to edit your /boot/grub/menu.lst..


```
man grub [
```

```
man grub menu.list 
```

---

### Post by reset3x on 2007-08-28
Hint: always defrag your windows partiton before installing Ubuntu.... You need to edit your /boot/grub/menu.lst..


```
man grub[
```

```
man grub menu.list 
```

---

### Post by reset3x on 2007-08-28
Hint: always defrag your windows partiton before installing Ubuntu.... You need to edit your /boot/grub/menu.lst..


```
man grub
```

```
man grub menu.list 
```

---

### Post by cawill on 2007-08-28
> How do I find out the vista hda designation?
You can run gparted to find that out, to run press ALT + F2 and type 'gksudo gparted', if its not installed in terminal run 'sudo apt-get install gparted'. In gparted you can see each partition and there hda designation, is your vista partition (ntfs partition) to have the same hda designation than in grub? (you can view grub by opening /boot/grub/menu.lst)

Can I ask why you installed 7.10 instead of 7.04 which is the current stable release?

---

### Post by illy on 2007-08-28
Hi Thanks for your replies,

First off the reason i installed 7.10 was that 7.04 is currently having a lot if hardware issues with the asus f3sv. after trying 3 different distros i was advised that 7.10 in text install mode would work and it has. Will try your suggestions and let you know how it works out.

Cheers,
            Illy

---

### Post by illy on 2007-08-28
Hi have checked the drive designation with gparted

the designation of the data is ntfs (for vista)

and found that

the loader that is in grub is '/dev/sda1' longhorn/vista loader

the main vista partition is '/dev/sda2' it says it is a 'boot' partition. Don't know where grub is located partition wise

so i guess all i have to do now is add that to grub how do i do that?

Once again thanks for your help.

Cheers,
           Illy

---

### Post by SunnyRabbiera on 2007-08-28
this is a known problem from what I have heard, but I have no solutions as I dumped my windows ages ago

---

### Post by illy on 2007-08-28
If it wasn't for the gaming side of things i would boot M$ entirely. Once i actually got linux loaded up it has virtually everything i needed straight off the cuff. Openoffice, music, messaging and plenty more. despite the learning curve i certainly think that it is worth it.

Cheers, 
            Illy

---

### Post by cawill on 2007-08-29
> **illy said:**
> Hi have checked the drive designation with gparted

the designation of the data is ntfs (for vista)

and found that

the loader that is in grub is '/dev/sda1' longhorn/vista loader

the main vista partition is '/dev/sda2' it says it is a 'boot' partition. Don't know where grub is located partition wise

so i guess all i have to do now is add that to grub how do i do that?


Yes you do, you can test it when the grub menu loads up, highlight the vista boot option and press 'e' in grub, then edit the partition it boots on to '1,2' or something like that and see if vista boots.

---

### Post by illy on 2007-08-29
cawill you are my hero! :KS

after playing with the numbers 0,1 seemed to work. vista went through its booting for the first time thing. then went to the blue teal screen with the cursor indicating loading. after a while the screen goes black and the computer restarts.

the asus f3sv only comes with recovery discs so i am not sure how to get windows working again. 

Thanks for your help

From, 
          Illy

---

### Post by cawill on 2007-08-29
When you installed ubuntu, did you overright your old xp partition (if you had one) or any other vista partitions?

---

### Post by illy on 2007-08-29
No i believe i  placed it in the second partition on the hard drive {the non Vista OS one}

---

### Post by illy on 2007-08-29
So does anyone have any idea on how i might get the dual boot to work.
 Thanks again for your help

Cheers,
                 Illy

---

### Post by illy on 2007-08-30
I think at the moment ubuntu is just too much hassle for me. I have tried over the last month to get it to work, have read a book or five and on top of that read plenty of forums for insight and advice. 

So for now i think ubuntu and i will part ways until i build up the resolve and find the time to try again. {looks like in a couple of weeks}

Once again Thanks to everyone for your help.

Cheers,
             Illy

---

