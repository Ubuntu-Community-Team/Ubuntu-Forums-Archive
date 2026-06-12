---
title: "Password Problem"
date: 2005-06-03
forum: Absolute Beginner Talk
---

### Post by spednik on 2005-06-03
Ok, i decided to change my password, by going into the k menu (i use KDE) and doing it the normal way. I entered my new password, that i wanted to change it to, and press enter. it said "this password is more than 8 characters, that may be bad for some systems" or something to that effect. so it gave me 2 options, use the new password, or stay with the old one. so i decided to stay with the old one, and pressed enter. 

So heres the problem, it didnt work, and now neither password works. the new or old ones both wont work. I only managed to log into my machine again, because i set the thing to automatically start KDE without a password prompt. 

So i went back into the control pannel, to try and change my password to something else, to get rid of all that junk, but to change a password, you need the one you are using now, so i am stuck in a password loop of doom, unable to use the old one, or change to a new one. 

So, i can use basic things, but i cant do much more than that. I tried rebooting, but thats about all i can think off. anybody else have any ideas? 

Thanks in advance.

---

### Post by GrumpySimon on 2005-06-03
Try opening up a terminal, and entering this:
```

passwd

```

It should ask you for your password - try both the new one, and the old one.

If that doesn't work, then you'll probably need to boot in to single user mode and reset from there. This is off the top of my head, so there may be some errors.

1) Reboot, wait for the GRUB boot menu to pop up (it's the one with the boot options).
2) Choose the menu item you want to boot using the arrow keys
3) Press 'e' (edit)
4) Press the "end" button on your keyboard
5) Type in ", single" (without the quotes)
6) Hit enter, and then press b (for boot)
7) Type: passwd <username>
8) Enter new password.

--Simon

---

### Post by spednik on 2005-06-03
Yeah, the terminal idea didnt work, as it didnt allow either password. 

I tried the thig with the grub, which was fine untill where you said to hit end, it brought me to a menu thing with  some options to edit, which one do i pick? 

Anyone else have any other ideas? 

Thanks again

---

### Post by GrumpySimon on 2005-06-03
[QUOTE=spednik]Yeah, the terminal idea didnt work, as it didnt allow either password. 

I tried the thig with the grub, which was fine untill where you said to hit end, it brought me to a menu thing with  some options to edit, which one do i pick? 

Anyone else have any other ideas? 

Thanks again[/QUOTE]
 Edit the one that normally boots up (although it doesn't really matter as long as you can get a terminal up).

---

### Post by spednik on 2005-06-03
Hey! it worked!!! 

Thanks so much!!


Everyone one these forums seems so brilliant, it makes me feel so stupid. 


Thanks again.

---

### Post by GrumpySimon on 2005-06-03
Ok, I've done some playing with my machine.

Try this:
1) Reboot, wait for the GRUB boot menu to pop up (it's the one with the boot options).
2) Choose the "recovery" option. 
3) Press 'e' (edit) and you'll see something like this:
```

title Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
initrd /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

```

4) Find the line that ends in "single" and mentions "kernel".
5) add this after 'single':
```

 init=/bin/bash

```

So the line now looks something like:
```

kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single init=/bin/bash

```

6) Hit enter, and then press b (for boot)
7) wait until it's loaded
[color=black]8[/color]) Type: passwd <username>
Enter new password.
9) type "halt", and when that's done, restart.

Edit: Nevermind then :)

--Simon

---

### Post by GrumpySimon on 2005-06-03
And while I'm at it, another way is to boot with a live cd.

1) Boot up with a live CD
2) Open terminal
3) Mount the passworded partition. I'll use /mnt
```

mount /dev/hda2 /mnt

```
change hda2 to match your install - it could be /dev/hda1 or 3, 4, 5 ... etc.
4) Change the root to /mnt
```

chroot /mnt

```
5) Change password
```

passwd <username>

```
6) reboot

--Simon

---

