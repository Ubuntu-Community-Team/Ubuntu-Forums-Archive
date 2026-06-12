---
title: "grub editor"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Pevichaey5 on 2008-03-23
hey

i installed the hardy beta on my ubuntu 7.10 system as a dual boot, but forgot that my bios is broken and can't use the keyboard until the os is fully loaded

i can't for the life of me figure out how to change grub so it will boot into 7.10 by default rather than 8.04

any help

cheers

---

### Post by ikonia on 2008-03-23
easy one this

change /boot/grub/menu.lst  on the /boot partition that grub is using

( if you've tried to dual boot and not used a seperate shared partition you'll have 2 /boot's - one for 7.10 one for 8.04 - make sure your editing the one that grub is using - probably the last installed.)

change the "default 0" line to be default $n where N is the number of menu options your ubuntu install is

eg;


(0)  ubuntu 7.10
      kernel /boot/blah blah

(1) ubuntu 7.10 - safe mode
     kernel /boot/blah blah single

(2) ubuntu 8.04
    kernel /boot/blah blah 


if you wanted ubuntu 8.04  then default would be 2

You may want to consider consolodating your 7.10 and 8.04 boot partitions onto a shared one to make manging kernel updates easier.

---

### Post by Pevichaey5 on 2008-03-23
thanks for the help, except not finished yet lol

i can't save changes to the grub menu as i'm not root, but i can't open gedit as root from terminal

toby@ubuntu154:~$ su
Password: 
root@ubuntu154:/home/toby# gedit /boot/grub/menu.lst

(gedit:25511): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: No such file or directory
Could not create per-user gnome configuration directory `/home/root/.gnome2/': No such file or directory
root@ubuntu154:/home/toby#

what can i do here?

cheers

---

### Post by ikonia on 2008-03-23
it looks like your doing a few things wrong here

1.) why are you using "su"  sudo is the correct command. If you don't know what your doing stop trying to be root.

2.) by not using the "-" after su your keeping your initial environment, which is causing you the permissions problem

you want to "gksudo nano /boot/grub/menu.lst"

or 

sudo vi /boot/grub/menu.lst

again - just to warn you make sure its the menu.lst on the boot partition that grub is using.

---

### Post by Pevichaey5 on 2008-03-23
ok

how do i edit the text using vi? i have never used it be, i have always used gedit

cheers

---

### Post by Pevichaey5 on 2008-03-23
nevermind bout that, google gived me answers lol

you been a great help

cheers

---

### Post by Taino on 2008-03-23
If you prefer Gedit it does work too. :)

```

sudo gedit /boot/grub/menu.lst

```

:popcorn:

---

### Post by Pevichaey5 on 2008-03-23
> **Taino said:**
> If you prefer Gedit it does work too. :)

```

sudo gedit /boot/grub/menu.lst

```

:popcorn:

sorry no it doesn't

```

toby@ubuntu154:~$ sudo gedit /boot/grub/menu.lst

(gedit:26817): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: No such file or directory
Could not create per-user gnome configuration directory `/home/root/.gnome2/': No such file or directory
toby@ubuntu154:~$ 

```

---

### Post by Taino on 2008-03-23
thats interesting :) well try.

```

sudo gedit /boot/grub/menu.lst

or

gksudo gedit /boot/grub/menu.lst

```

both work for me in the same way,
its more fun not being restricted to standards. :p

:popcorn:

---

### Post by ikonia on 2008-03-23
sudo is not the correct way to launch graphical apps, gksudo is

thats why gedit is borking in your example.

---

### Post by Pevichaey5 on 2008-03-23
i used vi in the end to fix my grub problem

all workin now so don't worry bout it

cheers

---

