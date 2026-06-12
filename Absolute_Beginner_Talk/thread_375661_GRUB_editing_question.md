---
title: "GRUB editing question"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-03-04
I had a question/idea about grub.  Could I go into my menu.lst and put the comment(#) before the old linux kernel entries so they won't appear in the menu, but will be easy to restore to my menu?  Also to edit menu.lst I would:```
cd /boot/grub
sudo(gksudo?) gedit menu.lst
``` Right?

---

### Post by SmiLey497 on 2007-03-04
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by kindafunnylookin on 2007-03-04
```
sudo /boot/grub/menu.lst
```
should do it for ya.

---

### Post by Matt1632 on 2007-03-04
Ok, but will commenting the entries work? Or will it mess up my grub.  On that same note, can I fix my menu.lst from the live CD if I mess it up?  Also, I read that you should use gksudo for this kind of stuff, does it matter in this case?

---

### Post by mfichifichi on 2007-03-04
what about uncommenting the 'howmany' field? I've never bothered, but surely somebody has it set...

---

### Post by SmiLey497 on 2007-03-04
> **Matt1632 said:**
> Ok, but will commenting the entries work? Or will it mess up my grub.  On that same note, can I fix my menu.lst from the live CD if I mess it up?  Also, I read that you should use gksudo for this kind of stuff, does it matter in this case?

just delete the entries you don't want

from a live cd you need to mount your drive, 

so in the terminal

(run ```
sudo fdisk -l 
``` to find out what your ext3 partition is)

```

cd /media/

```
```

sudo mkdir mydrive

```
```
sudo mount /dev/sda? mydrive
```  
replace sda? with whatever your linux drive is
```
gksudo gedit /media/mydrive/boot/grub/menu.lst 
```

if gedit doesn't work use nano so it would be ```
sudo nano /media/mydrive/boot/grub/menu.lst
```

when you want to exit and save in nano press Ctrl X

---

### Post by rsambuca on 2007-03-04
Any time you are using a graphical interface (such as gedit), you should use gksudo.  It just so happens that sudo will still work in this particular case, but as a matter of practice you should use gksudo.

---

### Post by kindafunnylookin on 2007-03-04
> **rsambuca said:**
> Any time you are using a graphical interface (such as gedit), you should use gksudo.  It just so happens that sudo will still work in this particular case, but as a matter of practice you should use gksudo.
thank you for that.
P

---

### Post by taurus on 2007-03-04
> **SmiLey497 said:**
> just delete the entries you don't want

from a live cd you need to mount your drive, 

so in the terminal
```

cd /media/

```
```

mkdir mydrive

```
```
sudo mount /dev/sda? mydrive
```  (run ```
sudo fdisk -l 
``` to find out what your ext3 partition is)

```
cd /media/mydrive 
```

```
sudo gedit /boot/grub/menu.lst
```


if gedit doesn't work use nano so it would be ```
sudo nano /boot/grub/menu.lst
```

when you want to exti and save in nano press Ctrl X

There are so many problems with this I don't even know where to begin.

---

### Post by SmiLey497 on 2007-03-04
> **taurus said:**
> There are so many problems with this I don't even know where to begin.

well he should run sudo fdisk -l before he starts t, but everything i wrote worked for me when i had to do it

---

### Post by rsambuca on 2007-03-04
This will work.  [[COLOR="Red"]Instructions[/COLOR]]("http://www.ubuntuforums.org/showpost.php?p=2227328&postcount=2")

---

### Post by taurus on 2007-03-04
> **SmiLey497 said:**
> well he should run sudo fdisk -l before he starts t, but everything i wrote worked for me when i had to do it

1.  It should be 

```
sudo mkdir mydrive
```
2.  Should use gksudo if you want to use gedit.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

3.  And this command will open a wrong file to edit.
```
sudo gedit /boot/grub/menu.lst
```
It will open the one on the LiveCD, not the harddrive.  It should have been

```
gksudo gedit **/media/mydrive**/boot/grub/menu.lst
```

4.  ```
sudo nano **/media/mydrive**/boot/grub/menu.lst
```

---

### Post by SmiLey497 on 2007-03-04
> **taurus said:**
> 1.  It should be 

```
sudo mkdir mydrive
```
2.  Should use gksudo if you want to use gedit.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

3.  And this command will open a wrong file to edit.
```
sudo gedit /boot/grub/menu.lst
```
It will open the one on the LiveCD, not the harddrive.  It should have been

```
gksudo gedit **/media/mydrive**/boot/grub/menu.lst
```

4.  ```
sudo nano **/media/mydrive**/boot/grub/menu.lst
```

1. Forgot to write sudo for that my bad

3. if you saw i wrote cd /media/mydrive so it will open the one in in drive

4. same as 3

---

### Post by taurus on 2007-03-04
> **SmiLey497 said:**
> 
3. if you saw i wrote cd /media/mydrive so it will open the one in in drive

4. same as 3

Actually, it doesn't matter if you "cd /media/mydrive" first because that command will not work.

```
sudo gedit /boot/grub/menu.lst
```
It should be

```
gksudo gedit boot/grub/menu.lst
```

---

### Post by rsambuca on 2007-03-04
I know everyone is trying to help out here, but honestly, SmiLey497, if you are going to give people instructions you should make sure they are accurate.

---

### Post by SmiLey497 on 2007-03-04
> **taurus said:**
> Actually, it doesn't matter if you "cd /media/mydrive" first because that command will not work.

```
sudo gedit /boot/grub/menu.lst
```
It should be

```
gksudo gedit boot/grub/menu.lst
```

worked for me

---

### Post by SmiLey497 on 2007-03-04
> **rsambuca said:**
> I know everyone is trying to help out here, but honestly, SmiLey497, if you are going to give people instructions you should make sure they are accurate.

i did it from memory, sorry it wasn't perfect enough for you, im only human

---

### Post by taurus on 2007-03-04
> **SmiLey497 said:**
> worked for me

Okay, it is then.

---

### Post by SmiLey497 on 2007-03-04
> **taurus said:**
> Okay, it is then.

edited my post with some of your corrections so it be alot easier to understand;)

---

### Post by keithweddell on 2007-03-04
So, if Matt1632 is still around -

Yes, you can comment out menu entries - although you could also just delete the ones you don't want.

Yes, if you mess up and can't boot, you can boot from a livecd to fix your menu.lst.


Keith

---

### Post by Matt1632 on 2007-03-04
Thanks, I think I'll just comment it out, it's only one entry and I don't see a reason to remove it at this point.  Just incase something glitches up in the new version of a kernel.

---

