---
title: "Cannot login to my system!"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by nir78 on 2006-07-08
I used this guide [http://www.ubuntuforums.org/showthread.php?t=208855]("http://www.ubuntuforums.org/showthread.php?t=208855") in order to use the gfxboot. Followed the steps one by one (execpt for the last part where I used my hd1,0 instead of the one noted).
Right following it I rebooted my computer and got a screen with the header "GNU GRUB version 0.97 ...."
and a command line starting with grub>
anything I tried I was not able to login to my system...

Someone ??

10x,

Nir

---

### Post by nir78 on 2006-07-08
I managed to enter my filesystem using the live CD and found out that my menu.lst file contain only one line: "gfxmenu /boot/grub/message.suse".

I guess this is the issue... any idea how can I recreate the file ??

10x
Nir

---

### Post by someusernoob on 2006-07-08
Didnt you backup this file before you "messed" with it? 

To restore Grub you could read this first:
[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by catlett on 2006-07-08
you can boot from that grub< line. If your root paretition is hd1,0 then enter this

grub< ```
root (hd1,0)
```
grub<  ```
chainloader +1
```
grub<  ```
boot
```
If everything is healthy then you will boot
If you get an error, post. If you don't and get in, post the output of this ```
sudo gedit /boot/grub/menu.lst
```

---

### Post by nir78 on 2006-07-08
> **someusernoob said:**
> Didnt you backup this file before you "messed" with it? 

To restore Grub you could read this first:
[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

I did no backup as there was no special warning in the tree...
guess someone should pay their attention to it!

---

### Post by nir78 on 2006-07-08
> **catlett said:**
> you can boot from that grub< line. If your root paretition is hd1,0 then enter this
grub< root (hd1,0)
grub< chainloader +1
grub< boot
If everything is healthy then you will boot
If you get an error, post.

after the chainloader +1 I got the message "Invalid or unsupported executable format" I have no idea what does it mean...

> **catlett said:**
>  If you don't and get in, post the output of this ```
sudo gedit /boot/grub/menu.lst
```

As for the menu.lst it have only one line in it:
```
gfxmenu /boot/grub/message.suse
```

Nir

---

### Post by nir78 on 2006-07-08
I managed to re-create the menu.lst by myself...
everything seems to work fine...

tnx everybody,
Nir

---

### Post by catlett on 2006-07-08
[COLOR="Red"]EDIT[/COLOR] Glad you got in. Disregard my post I didn't see yours when I started the reply





Let's do one thing first.
enter these commands at the grub< prompt

grub< ```
find /boot/grub/stage1


```
Whatever the outcome if this put in this next line (i.e. if it says (hd1,o) then put that where I have the questionh marks)

grub< ```
root (hd?,?)
```

grub< ```
setup (hd0)
```
This will reinstall grub. It will put grub on the mbr of the first hard drive with the "setup (hd0)" command. If you don't want grub on the masters mbr then you can put it wherever you want by changing (hd0) to whatever place you want. It will only boot from hd0 unless you are going to use some other bootloder to get to that partition.

Run this command ans grub should reinstall and have a menu on your next reboot.

If you get into ubuntu, go to the terminal and enter ```
sudo update-grub 
```This updates the grub menu. Hopefully it will add any entries it missed the first time,

---

### Post by wsonar on 2008-01-17
> **catlett said:**
> you can boot from that grub< line. If your root paretition is hd1,0 then enter this

grub< ```
root (hd1,0)
```
grub<  ```
chainloader +1
```
grub<  ```
boot
```
If everything is healthy then you will boot
If you get an error, post. If you don't and get in, post the output of this ```
sudo gedit /boot/grub/menu.lst
```

I tried root (hd0,1)  then went to next grub prompt no errors and typed chainloader +1 and recieved error13: Invalid or unsupported executable format

any help greatly apreciated

---

### Post by wsonar on 2008-01-17
> **catlett said:**
> [COLOR="Red"]EDIT[/COLOR] Glad you got in. Disregard my post I didn't see yours when I started the reply





Let's do one thing first.
enter these commands at the grub< prompt

grub< ```
find /boot/grub/stage1


```
Whatever the outcome if this put in this next line (i.e. if it says (hd1,o) then put that where I have the questionh marks)

grub< ```
root (hd?,?)
```

grub< ```
setup (hd0)
```
This will reinstall grub. It will put grub on the mbr of the first hard drive with the "setup (hd0)" command. If you don't want grub on the masters mbr then you can put it wherever you want by changing (hd0) to whatever place you want. It will only boot from hd0 unless you are going to use some other bootloder to get to that partition.

Run this command ans grub should reinstall and have a menu on your next reboot.

If you get into ubuntu, go to the terminal and enter ```
sudo update-grub 
```This updates the grub menu. Hopefully it will add any entries it missed the first time,


I don't get any error's when running these commands when I reboot I'm back to the grub promt I tried to run boot after running setup and got error:8 Kernal must be loaded before booting

any help appreciated

---

### Post by wsonar on 2008-01-17
> **catlett said:**
> you can boot from that grub< line. If your root paretition is hd1,0 then enter this

grub< ```
root (hd1,0)
```
grub<  ```
chainloader +1
```
grub<  ```
boot
```
If everything is healthy then you will boot
If you get an error, post. If you don't and get in, post the output of this ```
sudo gedit /boot/grub/menu.lst
```


ok command worked but boot just took me back to the grub prompt

---

