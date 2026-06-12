---
title: "Dual boot 2 hard drives"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by RodneyW on 2007-03-18
Hello,

Sorry if question has been asked many times but almost all refer to dual booting on one hard drive. I have 2 physical hard drives, one with ubuntu, one with xp. I have ubuntu drive set up as the master ide drive so it boots unless I hit f8 to enter the boot menu and select other hard drive. I was wondering how I go about having it bring up a menu for me to select which drive I want to boot from without having to hit f8. I have a couple of users so I would like it to give me an option as to which OS I want to use . I have looked at grub but it only shows my ubuntu drive. What do I do?

---

### Post by bodhi.zazen on 2007-03-19
> **RodneyW said:**
> Hello,

Sorry if question has been asked many times but almost all refer to dual booting on one hard drive. I have 2 physical hard drives, one with ubuntu, one with xp. I have ubuntu drive set up as the master ide drive so it boots unless I hit f8 to enter the boot menu and select other hard drive. I was wondering how I go about having it bring up a menu for me to select which drive I want to boot from without having to hit f8. I have a couple of users so I would like it to give me an option as to which OS I want to use . I have looked at grub but it only shows my ubuntu drive. What do I do?

Add an entry in /boot/grub/menu.lst for windows ...

Something like this :

> title		Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1

From a terminal you can open menu.lst as root via any of the following :

```
gksudo gedit /boot/grub/menu.lst
sudo nano -B /boot/grub/menu.lst
sudo vim /boot/grub/menu.lst
```

Note that is a small "L" and not the number 1

---

### Post by RodneyW on 2007-03-19
Ok I've entered that string as it appears and now I get Windows XP to show up, hence the line title Windows XP, but when I try and load it I get device not recognized or words to that effect, and I still have to hit escape to get into grub, i want it to give me boot options without having to hit any key.

Obviously I'm pointing to wrong device somehow, but how do I look at my windows drive from within ubuntu, places, computer,   doesn't show it up? Thats how I tell which drive is which right?

---

### Post by RodneyW on 2007-03-19
I've deleted the line 'hiddenmenu' so I think that will give me the grub menu now without escape.
I just need clarification as to what the lines should say to get it to boot from other hard drive. Ubuntu hdd has root at hd(0,0) , so where would the other (win) drive be and how should it be expressed?

---

### Post by mahiyar on 2007-03-19
You might have to change your device.map file too, currently it might be showing a single line (hd0) /dev/hda, you can add a second line (hd1) /dev/hdb, hope this helps.

---

### Post by RodneyW on 2007-03-19
No sorry,  I cannot open those files, and I dont know what to open them with, im quite new, they are there though. 

I have this in my grub:


title      Windows XP
map (hd0,0)(hd1,0)
map(hd1,0)(hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader+1


I get error device string not found or something like that. Clearly it points to the wrong location or as you suggested it does not recognize the location. What do I do now? How do i tell if it is recognizing it or its pointing to wrong place?

---

### Post by confused57 on 2007-03-19
You need a space between chainloader and +1:

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1

Also, to see your partition tables, boot into Ubuntu, open a terminal, enter:

```
sudo fdisk -l
```
the -l is a small "L"

on my Dell, Windows is actually on (hd1,1), (hd1,0) is a Dell utility:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by RodneyW on 2007-03-19
Ok thanks. Still cant get it to work, Im sure its something basic that just isnt obvious to me as a linux newcomer. Here are my partitions:

:~$ sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4367    33014488+   7  HPFS/NTFS
/dev/hda2            4368       20673   123273360    7  HPFS/NTFS

Disk /dev/hdb: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1190     9558643+  83  Linux
/dev/hdb2            1191        1245      441787+   5  Extended
/dev/hdb5            1191        1245      441756   82  Linux swap / Solaris
rodney@rodney-desktop:~$ 


And here is the string im trying:

title      Windows XP
map (hd0,0)(hd1,0)
map(hd1,0)(hd0,0)
rootnoverify (hd1,1)
makeactive
chainloader +1



Ive tried rootnoverify (hd1,0)    aswell, still no luck.

---

### Post by confused57 on 2007-03-19
I think it's your spacing:

title Windows XP
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

or

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

Copy & paste the first one, if it doesn't work, then copy & paste the 2nd one in your /boot/grub/menu.lst.

---

### Post by RodneyW on 2007-03-19
Thankyou sir,

Problem is resolved. First of the two options you sent me worked. Your help is very much appreciated.

---

