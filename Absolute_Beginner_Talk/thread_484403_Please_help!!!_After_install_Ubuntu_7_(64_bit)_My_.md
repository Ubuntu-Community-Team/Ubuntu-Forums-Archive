---
title: "Please help!!! After install Ubuntu 7 (64 bit) My Vista won't boot"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by duydaniel on 2007-06-25
Hello.

I have searched many forums... I could not find a solution that work...
I had Vista 32 bit... then installed Ubuntu 7 64bit  on another patition.
Then only Ubuntu boots... Vista is still on the hard drive but cannot boot.
I am an absolute novice... I have no idea how Ubuntu works yet... I want to give Linux a shoot but Bill Gates won't let me...

Any body can help me? Thank you.

---

### Post by Crafty Kisses on 2007-06-25
> **duydaniel said:**
> Hello.

I have searched many forums... I could not find a solution that work...
I had Vista 32 bit... then installed Ubuntu 7 64bit  on another patition.
Then only Ubuntu boots... Vista is still on the hard drive but cannot boot.
I am an absolute novice... I have no idea how Ubuntu works yet... I want to give Linux a shoot but Bill Gates won't let me...

Any body can help me? Thank you.

This link may be helpful to you:
[http://www.pro-networks.org/forum/about78184.html](http://www.pro-networks.org/forum/about78184.html)

---

### Post by duydaniel on 2007-06-25
I could not modify menu.lst since I am not "root" to do that...
I have no idea how to log in as root?

---

### Post by Clay_Banger on 2007-06-25
open the terminal and type:
```
gksudo gedit /boot/grub/menu.lst
```
then copy this into the bottom of the file, changing "hd0,1" to what ever partition/drive vista is on.
```
title Windows Vista
root (hd0,1)
makeactive
chainloader +1
```
save & exit, you should be able to boot into vista at the grub menu now..

---

### Post by TomUsher on 2007-06-26
I have been through exactly this process, and having entered those lines I get
"Error 12 invalid device requested"
Any more clues ?



Please ?

---

### Post by Clay_Banger on 2007-06-26
you will need to change this bit:
```
root (hd0,1)
```
to the location of your vista installation.
so if vista is on disk 2, partition one, enter:
```
root (hd1,1)
```
or disk 1, partition 3:
```
root (hd0,3)
```
hope that helps

---

