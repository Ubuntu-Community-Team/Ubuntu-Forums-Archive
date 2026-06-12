---
title: "how to change the boot sequence in GRUB?"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by zexoc on 2005-11-28
at the moment the GRUB boot options are as follows:

*Ubuntu
*Ubuntu (Recovery mode)
*memtest
other operating systems:
*MS Windows XP

with Ubuntu the first option being selected and booted if nothing gets selected.

I would like to change the boot sequence so that Windows XP is the default highlighted operating system, that gets booted if nothing is selected.

---

### Post by Gustav on 2005-11-28
Set the default falue to 3 in the file /boot/grub/menu.lst

Open the file
```
sudo gedit /boot/grub/menu.lst
```
You'll see the line
```
default 0
```
change it to 
```
default 3
```

---

### Post by aysiu on 2005-11-28
Open up a terminal:
Applications > Accessories > Terminal

Type in ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` Find the part that says ```
default 0
``` and change it to ```
default 4
``` Then save (control-x), confirm (y), and exit (Enter)

P.S. If you're using Hoary, the terminal is in Applications > System Tools > Terminal
And the number should be 4. The other operating systems entry counts as an item, believe it or not.

---

### Post by zexoc on 2005-12-02
I did the sudo nano /boot/grub/menu.lst and there was no text to edit, so I couldnt change the default 0 to 4. 

Any other suggestions?

---

### Post by BobSongs on 2005-12-02
[QUOTE=zexoc]I did the sudo nano /boot/grub/menu.lst and there was no text to edit, so I couldnt change the default 0 to 4. 

Any other suggestions?[/QUOTE]

Yeah, replace the code with:
```
sudo gedit /boot/grub/menu.lst
```
I just tried it. Had enough text to choke a horse.

Bob

---

### Post by ukiechris on 2005-12-02
Why 4??? I am trying to figure this out and this confuses me. What does 4 stand for/indicate/mean???

---

### Post by juicybananahead on 2005-12-02
[QUOTE=ukiechris]Why 4??? I am trying to figure this out and this confuses me. What does 4 stand for/indicate/mean???[/QUOTE]
Like aysiu said,
[QUOTE=aysiu]And the number should be 4. The other operating systems entry counts as an item, believe it or not.[/QUOTE]
If zexoc's menu.lst file contains the following lines...

*Ubuntu
*Ubuntu (Recovery mode)
*memtest
other operating systems:
*MS Windows XP

...then *Ubuntu is the first entry (number 0) and *MS Windows XP is the fifth entry (number 4). Alles klar?

---

