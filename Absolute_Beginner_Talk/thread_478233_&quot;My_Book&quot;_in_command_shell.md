---
title: "&quot;My Book&quot; in command shell"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by colddayinapril on 2007-06-19
so, i have a western digital external drive. the drives name is "My Book", but, because of my noobieness, i've yet to figure out how to get the command line to read spaces.

whats the proper way to:
:/$ cd media/My Book

cause that^ sure as hell don't work :)


also, is there a way to change the device name?

---

### Post by Jussi Kukkonen on 2007-06-19
```
cd /media/My\ Book
```
or you can just press <TAB> after "cd /media/My"

---

### Post by jd65pl on 2007-06-19
You can also use the code below:

```
cd '/media/My Book'
```

---

### Post by hyper_ch on 2007-06-19
Or just rename it to "My_Book" or "mybook" or ...

---

### Post by colddayinapril on 2007-06-19
thanks guys.
and like i said, i want to rename it. but i don't know how to rename a device. 

also, will it boot under the new name every time, or will i have to change it's name when ever i have to unplug it?

---

### Post by hyper_ch on 2007-06-19
It's not the device that needs to be renamed but the folder and mounting point :)

Unmount the drive, then execute the following:

```

sudo mv "/media/My Book" /media/mybook
[code]

Then open your fstab
[code]
sudo nano /etc/fstab

```

Search for the entry of that partition --> /media/My Book

And change it to /media/mybook

Then press ctrl-x --> y --> enter to save and exit nano.

---

### Post by colddayinapril on 2007-06-20
ok, i tried this with the drive mounted and unmounted. 

this is what happens when i try it unmounted:

```
mark@Winona:/$ sudo mv "/media/My Book" /media/mybook
mv: cannot stat `/media/My Book': No such file or directory
```

this when the drive is mounted:

```
mark@Winona:/$ sudo mv "/media/My Book" /media/mybook
mv: cannot move `/media/My Book' to `/media/mybook': Device or resource busy
```


and this is what the etc/fstab file looks like in both cases:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1c2065aa-d599-4554-abd4-fac5e845792f /               ext3    defaults,erro$
# /dev/sda5
UUID=775cd58f-cc7b-4a59-8217-c5f0168c83ef none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


...no mention of a "my book", evne when the damn things mounted and running.
i'm sort of at a loss here :/

---

### Post by hyper_ch on 2007-06-20
How do you mount that partition then?

---

### Post by colddayinapril on 2007-06-20
wow... i'm an idiot.

i just realized the problem. the My Book drive has software built into it that turns it off and on with the computer. which is why when i unmount it, it jsut turns it self right back on, and i have to manualy shut it down. 

so, the software on the drive is probably what's telling the system its name is My Book. which means that my problem needs to be take to the Western Digital help line, not here... 

oh well, thanks for the help anyways, guys.

---

