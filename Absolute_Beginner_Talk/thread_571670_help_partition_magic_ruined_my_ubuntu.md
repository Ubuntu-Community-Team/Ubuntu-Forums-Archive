---
title: "help: partition magic ruined my ubuntu"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-10-09
Hi all.

i´ll try to explain this the best i can:


had ubuntu and windows xp in dual boot. Tried to steal some free space from windows to give to my root partition, but in the middle of the operation, partition magic gave an error. When restarting, grub wasn´t starting (error 15, file not found).
One thing i noticed, is that the partition where root was with ext3 extension, now is with ext2 and it´s not recognized.
Can anyone help solve this?

---

### Post by skymera on 2007-10-09
ok reinstall Grub and try to boot.

EXT3 is sometimes noted down as EXT2.

did for me in partition magic.

---

### Post by Pulka on 2007-10-09
how can i reinstall grub?

---

### Post by skymera on 2007-10-09
easy :)

pop in the live CD as a start :D

ok for this example im going to use Drive 1 and Partition 2
you do for whatever you installed your ubuntu on

open terminal:

```
 grub

root (hd0,1) 

setup (hd0)


```

thats it

---

### Post by Pulka on 2007-10-09
i tried that before.
mine is hda 4, but when i do root (hd0,4) it says that the drive cannot be used

---

### Post by Olli on 2007-10-09
> **Pulka said:**
> i tried that before.
mine is hda 4, but when i do root (hd0,4) it says that the drive cannot be used

Doesn't partition 4 correpond to (hd0,3)?

---

### Post by Pulka on 2007-10-09
> **Olli said:**
> Doesn't partition 4 correpond to (hd0,3)?


root (hd0,3) - filesystem type unknown. partition type 0x83

setup (hd0) - cannot mount selected partition

---

### Post by skymera on 2007-10-09
ok so its defo hard drive 1?

and partition 4?

hmmm

ok in terminal grub type:

find /boot/grub/stage1

it will give all availibe partiitons.

make sure all disk are unmounted. to be safe

---

### Post by Pulka on 2007-10-09
> **skymera said:**
> ok so its defo hard drive 1?

and partition 4?

hmmm

ok in terminal grub type:

find /boot/grub/stage1

it will give all availibe partiitons.

make sure all disk are unmounted. to be safe


find /boot/grub/stage1 - no such file or directory

---

### Post by skymera on 2007-10-09
o.

i thhink you have a dead ubuntu my friend, i think its gone :(

i say reinstall using Gutsy :wink:

see what other people say

---

### Post by Pulka on 2007-10-09
hmmmm.....it's not to bad if i can save my /home directory. Apparently everything is alright with that one. Can i reinstall ubuntu keeping that home directory?

---

### Post by Paqman on 2007-10-09
> **skymera said:**
> 
i say reinstall using Gutsy :wink:


Hush you, it's still in beta! :)

---

### Post by skymera on 2007-10-09
true, but thursday Canduate is released.

im going up as we speak, 20mins left of downloaded.

---

