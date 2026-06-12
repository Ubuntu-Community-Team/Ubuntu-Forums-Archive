---
title: "GRUB Editor?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-02-10
I am pretty new to Ubuntu but I installed 6.10 on a computer that also running Windows XP Pro.  I mainly use Windows XP, and I was wondering if there was a way to change the default in GRUB.  Right now, it will boot to Ubuntu unless you change it to Windows XP; I would rather it be the other way around.  Is there any way to do this?

Thanks

---

### Post by rsambuca on 2007-02-10
Actually, it is very easily done.  I will need to see the output of your menu.lst to give you the exact instructions.

Please give us the output from 

cat /boot/grub/menu.lst

---

### Post by Maestro23 on 2007-02-10
You can go edit the /boot/grub/menu.lst

Open it up in a text editor. Ex: 

sudo nano -B /boot/grub/menu.lst 

(-B) makes a backup copy before you edit the file.

Make your changes, Save and Exit.

---

### Post by mdknaebel on 2007-02-10
Hmmmm... I am very new to Linux (Sorry) I don't really even know where to begin...

More detail?

Thanks

---

### Post by rsambuca on 2007-02-10
No problem.  You will need to open up a terminal (Main Menu -> Accessories -> Terminal)

At the prompt, type in```
gksudo gedit /boot/grub/menu.lst
```
the text editor will open the file in a new window.

copy and paste the contents into this thread so I can tell you exactly what to change.

---

### Post by ucsdrake on 2007-02-10
check out the wiki for the full guide ... ill just give you the terminal codes to start

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```

find 
```
...
default 0 
....
```

replace with 

```
default X
```

x being whatever number xp is in the order at the startup

Edit: the link for the wiki is [here](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s05.html)

---

### Post by mdknaebel on 2007-02-10
Ok, I think I can handle this now

Thanks

---

### Post by carverj on 2007-02-10
Just noticed I have no menu.list file. I am attempting to edit the grub menu to say vista instead of XP.

---

### Post by rsambuca on 2007-02-10
It is menu.lst

not menu.list

---

### Post by carverj on 2007-02-10
Yeah, sorry typo, that's what I meant to say... menu.list
It must exist somewhere if I use it to login... ha, funny. where did it go I wonder?

---

### Post by rsambuca on 2007-02-10
I guarantee you have one.  Just do a search for menu.lst on your drive

---

### Post by raul_ on 2007-02-10
> **carverj said:**
> Yeah, sorry typo, that's what I meant to say... **menu.list**
It must exist somewhere if I use it to login... ha, funny. where did it go I wonder?

it's LST not list

---

### Post by Maestro23 on 2007-02-10
> **raul_ said:**
> it's LST not list

lowercase... just so he knows.;)

---

### Post by rsambuca on 2007-02-10
Hey carverj, I find it ironic that a guy with "How to restore grub" in his signature line doesn't know where his menu.lst is:lol:

---

### Post by Tomosaur on 2007-02-10
Eyes gravitate towards the link in my sig!

---

### Post by nickoli_02 on 2007-02-10
```
sudo gedit /boot/grub/menu.lst
```

The top you'll see a bunch of commented lines with options explaining what each thing does. Near the bottom there are the actual menu entries. What you're interested in is the "default" line in each entry. "default 0" is the first bootable OS. You want windows to be this. Make sure you change Ubuntu to another, don't leave it as default 0 as well or I'd imagine there would be a conflict (or grub will just pick the first default 0 it sees, that being ubuntu).

---

### Post by rsambuca on 2007-02-10
nickoli_02 - actually, correct usage would be gksudo rather than sudo in this case, although both technically will work.

---

### Post by Maestro23 on 2007-02-10
> **rsambuca said:**
> Hey carverj, I find it ironic that a guy with "How to restore grub" in his signature line doesn't know where his menu.lst is:lol:

DOH!..;)

---

### Post by nickoli_02 on 2007-02-10
Oh really? I don't actually know what the difference between sudo and gksudo is... I think it's time to find out :P

---

