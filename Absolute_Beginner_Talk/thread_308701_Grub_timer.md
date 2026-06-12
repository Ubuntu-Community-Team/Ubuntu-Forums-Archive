---
title: "Grub timer"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-11-28
How can i reset the grub timer from counting from 10 to 0

I want to dicide myself if i want to atart from ubuntu or from windows

How can i do that?

---

### Post by eriefisher on 2006-11-28
If you set it to zero, you will boot into the first OS on the list.

---

### Post by turbojugend_gr on 2006-11-28
in a terminal type "sudo gedit /boot/grub/menu.lst",there you have to delete* a line saying "timeout 10". this way GRUB will be waiting for you to choose.

*you can comment that line too, use this symbol **#** before the "timeout 10", the way most other lines are, and this way it won't be readed.

---

### Post by SoggyCornflake on 2006-11-28
Grub settings are stored in the grub.conf file.  If you want to make changes to these settings you can use your favorite text editor as root.


```
sudo edit /boot/grub/grub.conf
```  (I'm pretty sure that's where the grub.conf file is located, but I'm at work with my windoze machine.)

You can change the time, OS options, and default OS without too much trouble.  (It goes without saying, but do be careful, or you may have a hard time booting up what you want.)

---

### Post by turbojugend_gr on 2006-11-28
> **SoggyCornflake said:**
> Grub settings are stored in the grub.conf file.  If you want to make changes to these settings you can use your favorite text editor as root.


```
sudo edit /boot/grub/grub.conf
```  (I'm pretty sure that's where the grub.conf file is located, but I'm at work with my windoze machine.)

You can change the time, OS options, and default OS without too much trouble.  (It goes without saying, but do be careful, or you may have a hard time booting up what you want.)

that's not gonna help, it's a wrong file name plus an wrong command, ;). It is safer to use the text file.

---

### Post by Tomosaur on 2006-11-28
Setting it to 0 is probably not a great idea, since it'll just jump straight to whatever's the default.

```

gksudo gedit /boot/grub/menu.lst

```

That is the command you will need to enter to edit the grub config. You can disable the timeout completely, or set it to whatever.

Alternatively, take a peek at my sig :)

---

### Post by fasoulas on 2006-11-28
Thank u all for replying 

It worked!!!

Now how can i remove the stupid sound that sounds like drums when the login screen comes up???

---

### Post by turbojugend_gr on 2006-11-28
Are you greek?

Edit: You should search these forums ,I 've seen some thread dealing with it.

---

