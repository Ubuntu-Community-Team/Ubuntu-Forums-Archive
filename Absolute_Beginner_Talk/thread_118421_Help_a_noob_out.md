---
title: "Help a noob out"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by FirePheonix on 2006-01-17
:confused: Ok Im stuck Ive installed ubuntu for the first time ever all has gone well up until the boot loader installation. Ive been scouring this site and others for help but nothing usable has come to me **I DONT WANT TO INSTALL GRUB TO HD0 I WANT TO MAKE A FLOPPY BOOT DISK** and this is where im stuck! the installer is asking where i want the bootloader to go and Im just not really sure what to tell it. how do I tell it to make a floppy boot disk? 

any and all suggestions would be welcome

---

### Post by thekiller on 2006-01-17
[QUOTE=FirePheonix]:confused: Ok Im stuck Ive installed ubuntu for the first time ever all has gone well up until the boot loader installation. Ive been scouring this site and others for help but nothing usable has come to me **I DONT WANT TO INSTALL GRUB TO HD0 I WANT TO MAKE A FLOPPY BOOT DISK** and this is where im stuck! the installer is asking where i want the bootloader to go and Im just not really sure what to tell it. how do I tell it to make a floppy boot disk? 

any and all suggestions would be welcome[/QUOTE]

I wonder why you dont want to install grub to hd0 ? According to me its safe in case you are wondering if it wont recognize your windows partition. And I guess after you proceed some steps in the installation after grub installation, there should be something saying "make a boot disk" or something similar to that. Dont exactly remember from the top of my head what it was.

---

### Post by FirePheonix on 2006-01-17
I dont want grub as I plan to use the windows boot or at least try to set it!!
>>I want to experiment a bit<<
anyway I cant get past the grub installation Im at a total impass I cant go forward and i cant go back lol all i need is the correct commands to give for it to make the floppy boot disk I tried typing /dev/fd0 as well as a few other thinfs so far all have failed and gone back to the grub install.

---

### Post by dueY on 2006-01-17
What's wrong with installing GRUB and editing the menu.lst to have Windows as your default (if you don't want to hit the down arrow a few times)

---

### Post by FirePheonix on 2006-01-17
**I Dont want grub I want to experiment with windows that is all **I might install Grub (wich btw doant detect my other 2 operating systems) and then delete it tho im not sure if that can be done

---

### Post by mental_noise on 2006-01-17
i am a newbie myself so i am not sure if this is correct. :)
but as far as i remember when i installed the 5.04 to my PC, you could specify where you want to install the boot loader. the default (i think) is:

```
/dev/hd0
```

i think you can change this to:

```
/dev/floppy
```

or

```
/dev/fd0
```

just try it out and see for yourself ... and by all means, correct me if i am wrong. ;)

---

### Post by Koybe on 2006-01-17
Yuo can then install grub on your /boot partition/ When it ask just anwser the partition needed : /dev/hda6 (for ecample).
But then you won't be able to loaad linux when you boot on hda (linux disk). So you need to add a entry to you windows boot.ini to get on the grub menu from there.

With the dd command you can make a image of you first secteur containting grub informations. Then save it in a file named linux.bin (for example) and put in in your c:.

Then you cna edit your boot.ini to indicate this file for booting linux. I can't remember the exact command but I've already explained it [here](http://www.ubuntuforums.org/showthread.php?p=481544#post481544).

Good luck.

---

### Post by FirePheonix on 2006-01-17
[QUOTE=Koybe]Yuo can then install grub on your /boot partition/ When it ask just anwser the partition needed : /dev/hda6 (for ecample).
But then you won't be able to loaad linux when you boot on hda (linux disk). So you need to add a entry to you windows boot.ini to get on the grub menu from there.

With the dd command you can make a image of you first secteur containting grub informations. Then save it in a file named linux.bin (for example) and put in in your c:.

Then you cna edit your boot.ini to indicate this file for booting linux. I can't remember the exact command but I've already explained it [here](http://www.ubuntuforums.org/showthread.php?p=481544#post481544).

Good luck.[/QUOTE]
thanks this is along thew lines of what I was planning to do Its not being able to boot linux that worries me

---

