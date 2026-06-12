---
title: "Help loading GRUB"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by Lopsicle on 2006-09-23
Hello....a couple of days ago I downloaded the KDE desktop because I wanted to compare it with Gnome, all was working fine until last night when I shut down, instead of the Gnome shutdown screen coming up, the KDE screen shutdown came up, this had never happened before ;) Anyway when I tried to to start up this morning I cant get into Grub.

I have searched the forums but cant find anything that will work, I am using the live cd at the moment, I dont want to reinstall if possible.

Thank you :)

---

### Post by bulldog on 2006-09-23
Well you must have changed something because adding the KDE desktop is not altering GRUB as far as I know.

But you can reinstall GRUB with your live cd if that's what you want to do.

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. 

Code:

sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)


Finally exit the grub shell
Code:

quit

---

### Post by Lopsicle on 2006-09-23
Hiya Bulldog, thanks for your reply, I tried it and this is what I got....

Uncompressing Linux...Ok,booting the kernel
[34,522756] Kernel panic-not syncing : VFS : Unable to mount root fs on unknown-block (0,0) [34,522839]

---

### Post by Lopsicle on 2006-09-23
:).......................

---

### Post by Lopsicle on 2006-09-23
Hello...........anyone, Please ;)

---

### Post by bulldog on 2006-09-23
Sorry,forgot the topic.

Well this is not as easy to say,but I haven't the slicest idea what to do at your kernel panic.

Do you have one kernel installed or do you have an older one to use instead?
Just to see if this one will do.

Looks like a bad kernel update or something like that.

---

### Post by Lopsicle on 2006-09-23
Hiya BD that's ok, no I just have one kernel installed, so you think I will need to reinstall? [-o<

---

### Post by bulldog on 2006-09-23
If you can't boot into it [not even the recovery mode?] I see no other option.

You can only do a repair when you are logged in and I'm not even sure if that will succeed,but when it won't boot..............:shock:

I shouldn't know a way,if there is one,to do the repair with the live cd.

You can experiment though,to learn a little.

---

### Post by Lopsicle on 2006-09-23
Thanks thats what Im trying now,if I cant see a way I will leave it until tomorrow to see if anyone else has any ideas.If not I will just have to spend all my Sunday reinstalling everything :(

---

### Post by nsleiman on 2006-12-28
> **bulldog said:**
> Well you must have changed something because adding the KDE desktop is not altering GRUB as far as I know.



Well i found out that kdm/KDE alters the menu.lst file in /boot/grub/ and adds to the kernel image to be loaded: splash quiet (something like this). and this caused me system hangs :( so i removed these options and now i can start/shutdown my system with no problems! i dont know really if this can harm my system in a way or another.. hope not :)

---

### Post by bulldog on 2006-12-28
> **nsleiman said:**
> Well i found out that kdm/KDE alters the menu.lst file in /boot/grub/ and adds to the kernel image to be loaded: splash quiet (something like this). and this caused me system hangs :( so i removed these options and now i can start/shutdown my system with no problems! i dont know really if this can harm my system in a way or another.. hope not :)

Well,tell us about it :D 
I have only gnome and I have the quiet splash items after my kernel lines.:cool: 
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash=vga=792
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot 
```

Think most of us have those.

---

