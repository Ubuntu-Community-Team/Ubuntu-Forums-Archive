---
title: "help me please"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-19
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst

^ i went there and put # before ubuntu kernel.. thinking it will hide grub menu.. but now when i start .. its a shell .. and it only says grub>

how do i put the # back ? and bring it back to normal.. 

im using ubuntu live cd.. can anyone help me out quickly please ?

thanks

---

### Post by HunkieChan on 2007-03-19
please anyone.. i need to get into my system.. please ?

---

### Post by HunkieChan on 2007-03-19
uh someone knows about.. please.. what can i do ?

---

### Post by bodhi.zazen on 2007-03-19
LOL

No big deal ...

With the live CD, mount your Ubuntu root partition and edit menu.lst removing the # :p

To do this, open a terminal

Assuming /dev/hda1 as Ubuntu (change the commands to your Ubuntu root partition) :

```
sudo -i    <- Become root
mount /dev/hda1 /mnt
nano /mnt/boot/grub/menu.lst  <- you could use any editor you like here ...
```

Should be good to go ...

If you do not know your ubuntu partition, ```
sudo fdisk -l  <- Do not need sudo if you are already root ;) 
```

HTH

---

### Post by HunkieChan on 2007-03-19
> **bodhi.zazen said:**
> LOL

No big deal ...

With the live CD, mount your Ubuntu root partition and edit menu.lst removing the # :p

To do this, open a terminal

Assuming /dev/hda1 as Ubuntu (change the commands to your Ubuntu root partition) :

```
sudo -i    <- Become root
mount /dev/hda1 /mnt
nano /mnt/boot/grub/menu.lst  <- you could use any editor you like here ...
```

Should be good to go ...

If you do not know your ubuntu partition, ```
sudo fdisk -l  <- Do not need sudo if you are already root ;) 
```

HTH

it says hda 1 doesnt exit.. what can i do ?

---

### Post by HunkieChan on 2007-03-19
oh got it.. i should have seen the last part.

---

### Post by HunkieChan on 2007-03-19
how do i save it though ?

---

### Post by BobSongs on 2007-03-19
To save a file in Nano you "write out" [ctrl + O] (that's the capital letter O)

---

### Post by HunkieChan on 2007-03-19
> **BobSongs said:**
> To save a file in Nano you "write out" [ctrl + O]

thank you sir

---

