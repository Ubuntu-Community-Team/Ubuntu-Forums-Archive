---
title: "&quot;Ghosting&quot; Ubuntu"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2008-01-04
hey all,

Ive read a few other threads on how to Ghost ubuntu but I havent quite found an answer. I have ubuntu 7.10 with tons of settings n such on an external 200 GB hard drive. I got a larger drive and want to migrate ubuntu over onto it.

So how do I 
1) Migrate ubuntu, all my settings and Grub onto the new HD 

thanks all!!

---

### Post by Fixman on 2008-01-04
There are many ways. The faster one is formatting the drive as ext3. Then, from Ubuntu, do ```
 sudo gedit /etc/fstab
```

Then, look for an entry of "/dev/hdb0" (or /dev/sdb0), and change it for

```
UUID=(don't change this) /mnt/new (don't change this)
```

Later, run on a terminal

```

sudo mkdir /mnt/new
sudo mount /dev/hdb0 # Try sudo mount /dev/sdb0 if that doesn't work
sudo cp -R / /mnt/new # This should take a looooooong time, try to leave the computer steady for a time

```

The other way (easier and more secure) is using Ubuntu live CD, and going to 

```
system->administration->partition editor
```

There select your old Ubuntu partition

```
right click->copy
select your new HD
right click->paste
apply
wait a looooooooong time (longer than of way 1)
```

And you have it there.

---

### Post by PinkFloyd102489 on 2008-01-04
The only thing Ive seen is to used parted or Clonezilla to move the files and then reinstall Grub from the Live CD with instructions.

---

### Post by Paqman on 2008-01-04
One method I like that works for reinstalls:

[Create a list of all your installed packages](http://ubuntuforums.org/showthread.php?t=261366). Do a fresh install on your new drive, reinstall all your packages automatically, and copy your /home folder to the new install. Make sure you set up the user accounts exactly the same and all will be well.

---

### Post by tech9 on 2008-01-04
> **JasonBourneLinux said:**
> hey all,

Ive read a few other threads on how to Ghost ubuntu but I havent quite found an answer. I have ubuntu 7.10 with tons of settings n such on an external 200 GB hard drive. I got a larger drive and want to migrate ubuntu over onto it.

So how do I 
1) Migrate ubuntu, all my settings and Grub onto the new HD 

thanks all!!

to create an image, clonezilla is your best bet, you could also try partimage

---

