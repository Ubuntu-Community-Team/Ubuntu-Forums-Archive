---
title: "probelm booting up..."
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Hranj on 2007-08-20
im having a problem booting up my ubuntu computer. i recently tried to change the boot screen but it didnt work and ive been asked to choose the resolution or hit space bar and proceed without a boot screen. ive been hitting space bar and everything has been working fine for me until now.

i tried booting up this morning and my computer has been stuck on one part for over 6 hours now so im guessing its not gonna just work. after the computer sets up all my hdds it goes and looks for usb hubs. after that it says

```
Done
Begin: Waiting for root file system. . .
```

and it doesnt proceed from there. how can i fix this?

---

### Post by Hranj on 2007-08-20
after waiting a long time it finally came up with this message

```
ALERT! /dev/disk/by-uuid/12f64f0b-b0zd-462f-bb5c-5c9dcc49e202 Does not exist. Dropping into a shell!
```

after that it loads the shell but i have no idea what to do. help?

---

### Post by mikeyphi on 2007-08-20
Try booting from the second Grub option -recovery mode

If you get similar problems it might be that you've got a disk failure

Use a Live CD to check your system.

---

### Post by Hranj on 2007-08-20
i used the second grub mode last night just messing around and i got the same message. so im gonna try booting with the live cd now. i guess there is a disk repair tool on that or something? ive never had to do this before.

---

### Post by mikeyphi on 2007-08-20
> **Hranj said:**
> i used the second grub mode last night just messing around and i got the same message. so im gonna try booting with the live cd now. i guess there is a disk repair tool on that or something? ive never had to do this before.

Find out where ubuntu is (eg /dev/hda1) and the run fsck   (eg fsck/dev/hda1)

---

### Post by Hranj on 2007-08-20
ahhh, i hate sounding like a newbie but how do i find out where ubuntu is. i booted off the live cd and im running ubuntu but both my drives are listed as volumes and i dont know "where ubuntu is"

---

### Post by Hranj on 2007-08-20
ok so i found the drive and ran fsck /dev/sda1

i get this message
```
WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? 

```

im gonna hit yes and hope for the best i guess.

---

### Post by Hranj on 2007-08-20
decided not to hit yes. i chose no and then unmounted the drive and ran fsck again. i got this...

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda1: clean, 189533/1196032 files, 1819840/2389660 blocks

```

so from the looks of it its saying that my drive is fine even though its not. whats my next move?

---

### Post by yogo on 2007-08-20
try using the Super Grub Disk, easily burnt to an iso . See if you can load Ubuntu from it.

I doubt you have problems with your HD, most likely your problems come from playing around with your boot screen.

---

### Post by mikeyphi on 2007-08-20
[QUOTE=so from the looks of it its saying that my drive is fine even though its not. whats my next move?[/QUOTE]

Try a normal Boot again!

If you still have problems and you want some info about Grub - start here: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Hranj on 2007-08-20
ok, so ive got another problem. the only cd burner in the house is in the broken machine running a live cd. so i cant burn an iso of super grub disk. is there any way that i can repair it manually? that grub page is giving me a real head ache and i have no idea what its talking about.

---

### Post by mikeyphi on 2007-08-20
You could wait for someone else to come up with an idea
OR you could rescue your data (if any) and reinstall from the Live CD

---

### Post by Hranj on 2007-08-20
are you positive the the super grub disk will do the trick? if so ill just go to a friends and burn it to a disk if it comes down to that. i cant just wipe my drive and reinstall. there is too much stuff on there to rescue and save.

---

### Post by Hranj on 2007-08-20
ok so i downloaded that super grub disk but im having trouble running the fix part. i go into the english menu and then into the gnu/linux. after that i go to the repair section and select the drive to repair, but after i do that all it does is restart. i dont know how im supposed to select that drive for repair because i dont see any options that select it. anyone know what do to?

---

### Post by Hranj on 2007-08-20
ok, ive tried everything i and the internet can think of. im backing everything up and im gonna do a clean install on it. if anyone has any other suggestions as to what to do, please PM me ASAP. thanks for the help everyone, these forums are a godsend.

---

