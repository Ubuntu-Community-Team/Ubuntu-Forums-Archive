---
title: "pclinuxos ubuntu and windows"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by kman14 on 2007-06-03
just looking for a little help.

i have ubuntu on a separate hard drive from windows - no problems there.
i have just installed pclinuxos on the hard drive that has windows - again no problems.

the problem is that when i turn on my computer it only gives me the option to load windows or pclinuxos not ubuntu (on the other disk).

i tried changing the boot order in bios, but that just gives me an error.

i sure it is something simple i am just not sure what? 

any help would be great.

thanks.

---

### Post by hyper_ch on 2007-06-03
Do you have grub installed as boot loader?

---

### Post by kman14 on 2007-06-04
i have grub installed for ubuntu.
i not sure what it is for pclinuxos.
it seems to be graphical, but i still only use the up/down arrows to select the what i want.

thanks.

---

### Post by confused57 on 2007-06-04
You should be able to add an entry to your PCLinuxOS grub menu to boot Ubuntu, using configfile:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by pappapump on 2007-06-04
That PC-Linux OS is pretty snappy.
I tried it along with Free-spire and liked both, but freespire pretty much limits overall deb installs.

---

### Post by kman14 on 2007-06-04
confused thanks for the quick reply.

can i just check the following with you?

[B]title        Ubuntu Edgy Eft
savedefault
configfile   (hd0,5)/boot/grub/menu.lst[/B]

with the config file - do i just type the above into the terminal but with the changes for my system?

title Ubuntu Feisty Fawn
savedefault
configfile (hdb,0)boot/grub/menu.1st

i'm using feisty
it's on my second hard drive (hdb)
there's no partition (0) - it uses the whole disk.

would that be right?

thanks.

---

### Post by confused57 on 2007-06-04
Your configfile entry should be:
```
title Ubuntu Feisty Fawn
savedefault
configfile (hd1,0)/boot/grub/menu.lst
```

menu.lst is short for menu.list

edited, left out the / before boot.

---

### Post by kman14 on 2007-06-04
confused, i cut and pasted what you wrote into konsole and this is what i got:

[karl@localhost ~]$ title Ubuntu Feisty Fawn
bash: title: command not found
[karl@localhost ~]$ savedefault
bash: savedefault: command not found
[karl@localhost ~]$ configfile (hd1,0)/boot/grub/menu.lst
bash: syntax error near unexpected token `hd1,0'
[karl@localhost ~]$

do you know what i'm doing wrong?

thanks.

---

### Post by D!mon on 2007-06-04
You need to put these lines at the end of your menu.lst file and after next reboot you will have a boot option called 'Ubuntu Feisty Fawn' (name from title)
and after you select it you will be taken to the Ubuntus' grub menu

---

### Post by kman14 on 2007-06-04
well it's pretty obvious why i'm posting in the "Absolute beginner talk" section.

D!mon - how do i get into the menu.lst file?

thanks for the help so far guys.

---

### Post by D!mon on 2007-06-04
It's placed at the /boot/grub directory. You need to be a root to edit this file, so if you re using ubuntu press Alt-F2 and type gksudo gedit /boot/grub/menu.lst and then enter your password. If you use another distribution you will possibly need to use 'su root' command to become root before editing the file

---

### Post by confused57 on 2007-06-04
Sorry, I didn't explain how to edit your menu.lst & add the Feisty entry...open a Konsole in PCLinuxOS:
```
su
cd /boot/grub
kwrite menu.lst
```

then add the entry to the very end of your menu.lst...quit & save...

Added:  If kwrite doesn't open your menu.lst, you can try nano:
```
nano menu.lst
```
you probably can't scroll, but you can page down, add the Feisty entry...ctrl+x, y, enter...to save

---

### Post by kman14 on 2007-06-04
thank you guys
i'm at work now and.....well was in bed last night (i'm in australia), i'll give this a try as soon as i get home.

cheers.

---

### Post by smoker on 2007-06-04
this command:
sudo gedit /boot/grub/menu.lst

sorry ignore: didn't read page two!

---

### Post by kman14 on 2007-06-05
well, i'm typing this from within ubuntu - so thank you guys for the help.

confused57, what you said worked perfectly.

again - big thanks.

cheers.

---

