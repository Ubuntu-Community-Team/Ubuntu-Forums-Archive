---
title: "ntfs3g"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by muzz1989 on 2007-08-06
hi, im new to ubuntu and linux in general. im running unbuntu 6.06 from the live CD and im trying to install ntfs-3g so i can browse my ntfs partion. i tried doing the 
sudo apt-get install ntfs-3g
but it came back with "couldnt find package ntfs-3g". so i went to the ntfs3g website and downloaded it and ran configure, but it says "configure: error: no acceptable C compiler found in $PATH" 
where can i get a C compiler so that i can install ntfs3g?

thanks in advance!

---

### Post by Ek0nomik on 2007-08-06
Have you ever compiled anything before?

Try installing this bundle for some essential compiling tools:

```
sudo apt-get install build-essential
```

---

### Post by Ek0nomik on 2007-08-06
Also, I think you can add it to your repository so you won't get that error:

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

ntfs3g I believe is in the 6.10+ repository by default, but maybe it wasn't in 6.06.

---

### Post by Seisen on 2007-08-06
> **Ek0nomik said:**
> Also, I think you can add it to your repository so you won't get that error:

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

ntfs3g I believe is in the 6.10+ repository by default, but maybe it wasn't in 6.06.

Its in the edgy  universe repositories but its not in the dapper repositories.

---

### Post by asmoore82 on 2007-08-06
> **muzz1989 said:**
> hi, im new to ubuntu and linux in general. im running unbuntu 6.06 from the live CD and im trying to install ntfs-3g so i can browse my ntfs partion. i tried doing the 
sudo apt-get install ntfs-3g
but it came back with "couldnt find package ntfs-3g". so i went to the ntfs3g website and downloaded it and ran configure, but it says "configure: error: no acceptable C compiler found in $PATH" 
where can i get a C compiler so that i can install ntfs3g?

thanks in advance!

that's way too much trouble to go through for a Volatile Live environment ...
you don't need ntfs3g to browse files, just to make changes and/or delete files.

---

### Post by muzz1989 on 2007-08-06
> **asmoore82 said:**
> that's way too much trouble to go through for a Volatile Live environment ...
you don't need ntfs3g to browse files, just to make changes and/or delete files.

oh, i thought that was the problem because i cannot browse my ntfs partition but i can browse the virtual FAT partition.
it says i dont have permission to browse the ntfs partition, but everything's the same as the vfat, so i dont know.

---

### Post by stchman on 2007-08-06
> **muzz1989 said:**
> hi, im new to ubuntu and linux in general. im running unbuntu 6.06 from the live CD and im trying to install ntfs-3g so i can browse my ntfs partion. i tried doing the 
sudo apt-get install ntfs-3g
but it came back with "couldnt find package ntfs-3g". so i went to the ntfs3g website and downloaded it and ran configure, but it says "configure: error: no acceptable C compiler found in $PATH" 
where can i get a C compiler so that i can install ntfs3g?

thanks in advance!

If you want to browse your NTFS partition then you don't need ntfs-3g.  You will need it if you plan to write to the partition.  I recommned you upgrade to feisty.

---

### Post by Inxsible on 2007-08-06
> **muzz1989 said:**
> oh, i thought that was the problem because i cannot browse my ntfs partition but i can browse the virtual FAT partition.
it says i dont have permission to browse the ntfs partition, but everything's the same as the vfat, so i dont know.
you probably do not own the mount point of the ntfs drive,
you can change that by

```
sudo chown -R <your username>:<your group> <path to mount point>
```

---

### Post by ubuscout on 2007-08-14
Hi folks

...it seem i've get similar problem.... :(

I need remove some file from windows ntfs partition, so usually I try these step ...

1) boot with livecd (Feisty Fawn 7.04) 
2) Install ntfs-3g by synaptic manager
3) mount windows ntfs volume in tmp 
4) and remove file ...   :)

...everything works fine if I can connect my pc in internet by lan (I have no modem)... but I'm in trouble if try install ntfs-3g in command line ...

First I do :

1)  "./configure"   and  here I get problem...    "gcc can't make output file" (something like this) 


Someone can help me ?!? thx :)

---

### Post by Genecks on 2007-08-14
> **ubuscout said:**
> Hi folks

...it seem i've get similar problem.... :(

I need remove some file from windows ntfs partition, so usually I try these step ...

1) boot with livecd (Feisty Fawn 7.04) 
2) Install ntfs-3g by synaptic manager
3) mount windows ntfs volume in tmp 
4) and remove file ...   :)

...everything works fine if I can connect my pc in internet by lan (I have no modem)... but I'm in trouble if try install ntfs-3g in command line ...

First I do :

1)  "./configure"   and  here I get problem...    "gcc can't make output file" (something like this) 


Someone can help me ?!? thx :)

Did you install build-essential?

Whenever you think of ./configure, make, make install, or gcc, you ought to have somewhere in your mind the term "build-essential"

---

### Post by antharr on 2007-08-20
When installing ntfs-3g, the installation creates a group called fuse. Go to System>Administration>Groups and Users and add users to the fuse group.

---

### Post by ubuscout on 2007-08-20
> **Genecks said:**
> Did you install build-essential?

Whenever you think of ./configure, make, make install, or gcc, you ought to have somewhere in your mind the term "build-essential"

ok now,   ...it's past some day and I'm not really really sure but  I think remember I've looked it and "build-essential" was there... 


If I find some minute, I'll try it again... but I'm almost sure... it was

thx

---

### Post by ubuscout on 2007-08-20
> **antharr said:**
> When installing ntfs-3g, the installation creates a group called fuse. Go to System>Administration>Groups and Users and add users to the fuse group.

thx... I'll look it !   ...I hope try it again as soon as I can...   :)

---

