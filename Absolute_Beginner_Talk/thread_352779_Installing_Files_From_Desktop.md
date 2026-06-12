---
title: "Installing Files From Desktop"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by andtsoreyu on 2007-02-03
I am VERY VERY VERY new to Ubuntu and I love it.  The problem is I have no idea how to install any files such as

.bin
Archive Files
or anything.

I have seen a lot of people install them by making them excutable in ternimal but when I try to do that such as

chmod a+x file.bin

it says this file or directory doesn't exists, and yes I put the file name right.  Do I have to point it to my desktop (that is where the file is at) or what, and if I have to how in gods name do you do that.


Thanks a Lot,

Matt

---

### Post by taurus on 2007-02-03
Remember, Linux/Unix is case sensitive so desktop is not the same as Desktop.  

```
cd ~/Desktop
```
Now, see if you file is in there.

```
ls -la
```

---

### Post by meng on 2007-02-03
You are not in the correct directory when you type that command. When you first open a terminal you are in your /home/username directory, you need to get to your /home/username/Desktop directory

so:
cd Desktop
chmod a+x (etc.)

note it has to be Desktop with an upper-case D, Linux is case-sensitive.

---

### Post by fenian on 2007-02-03
Here is a good guide for installing anything on ubuntu...

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by andtsoreyu on 2007-02-04
Thanks a lot everyone I got everything working with the installation files.  Got some other problems, but I have already posted about them.


Big Help thanks,

Matt

---

