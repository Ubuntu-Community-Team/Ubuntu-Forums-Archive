---
title: "Two hard drives-Two Ubuntus?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Indy452 on 2008-02-12
I have two hard drives in my computer,  the  master has a fully functining version of Xubuntu which I cherish and the slave drive has Ubuntu installed on it.

When I boot up It uses the master drive which opens Xubuntu.  I can access the slave drive from my desktop in Xubuntu but I can't run Ubuntu (slave)  that way. 

I would really like the option of booting from either hard drive on startup. I saw a tutrial on booting windows from a second hd but I would like to know how I can boot a different Ubuntu distro.

Can someone help me figure this one out?:confused:

Thanks for reading.

Neal

---

### Post by oedha on 2008-02-12
you have to work on the grub
you can try to use super grub disk

---

### Post by Indy452 on 2008-02-13
> **oedha said:**
> you have to work on the grub
you can try to use super grub disk


What is super grub disk? 

What procedure do I take?  

Hasen't anyone done this before?

---

### Post by skymera on 2008-02-13
cant you add your slave drive to Grub?

---

### Post by Crooksey on 2008-02-13
In your menu.lst you need something like...

```

Title Ubuntu2
root(hd1,0)
kernel /path/to/kernel

```

The important part is the **root(hd1,0)**

The 1 shows grub to look for a second hard disk, and then the 0 indicates first partiton on the drive, so if ubuntu was on partiton 3 on harddrive 2, it would be...

```

root(hd1,2)
```

Just copy the entry for your Xubuntu, but change the root and kernel sections accordingly.

---

### Post by Indy452 on 2008-02-13
> **Crooksey said:**
> In your menu.lst you need something like...

```

Title Ubuntu2
root(hd1,0)
kernel /path/to/kernel

```

The important part is the **root(hd1,0)**

The 1 shows grub to look for a second hard disk, and then the 0 indicates first partiton on the drive, so if ubuntu was on partiton 3 on harddrive 2, it would be...

```

root(hd1,2)
```

Just copy the entry for your Xubuntu, but change the root and kernel sections accordingly.



So I need to add these codes to the grub list when I first start the computer?

I'snt grub something that you have too access before boot then?

Is there any way to access grub when fully booted?

Thanks for the replies folks. 

Neal

---

### Post by kpkeerthi on 2008-02-13
You need to exercise extra caution with those grub commands. If you are a newbie, I suggest you use [super grub disk]("http://www.google.co.in/search?q=SUPER+GRUB+DISK") to automatically fix the GRUB.

---

### Post by Crooksey on 2008-02-13
> 
So I need to add these codes to the grub list when I first start the computer?

I'snt grub something that you have too access before boot then?

Is there any way to access grub when fully booted?

Thanks for the replies folks. 

Grub is a program that runs before operating systems are loaded, the menu.lst is the configuration file for grub, you edit it from within the operating system, in your xubuntu it will be located at.

```

/boot/grub/menu.lst
```

Edit it in there, then reboot and you should load it ok, also..

```

man grub
```

Will help you out.

---

