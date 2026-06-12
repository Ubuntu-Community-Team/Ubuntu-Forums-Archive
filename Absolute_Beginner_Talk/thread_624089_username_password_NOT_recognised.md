---
title: "username password NOT recognised"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by nick69 on 2007-11-26
I used to log on with my burned Ubuntu 7.10 CD but suddenly
it does not accept my username  and password
Any solutions ?

---

### Post by samuel.rajesh on 2007-11-26
> **nick69 said:**
> I used to log on with my burned Ubuntu 7.10 CD but suddenly
it does not accept my username  and password
Any solutions ?

you use the live cd ? if so i dont think it needs a password

---

### Post by nick69 on 2007-11-26
It does ask for username password and I had logged on several times recently but now it does not recognise them.
In fact I formated the swap and root partitions (from windows) to start all over from the beginning but it keeps asking me for  username password ? ? ??????????????????????????????????????????

---

### Post by samuel.rajesh on 2007-11-26
> **nick69 said:**
> It does ask for username password and I had logged on several times recently but now it does not recognise them.
In fact I formated the swap and root partitions (from windows) to start all over from the beginning but it keeps asking me for  username password ? ? ??????????????????????????????????????????


Formatted em from windows  are they still in ext3 format ? or did u use something like partion magic to format them

---

### Post by nick69 on 2007-11-26
NOT in ext3 format anymore ,  used partion magic to delete them in fact and start all over again.
Thanks for helping me . . .

---

### Post by samuel.rajesh on 2007-11-26
> **nick69 said:**
> NOT in ext3 format anymore ,  used partion magic to delete them in fact and start all over again.
Thanks for helping me . . .


If u deleted the partion ,you should be able to boot from the live cd with out a password ,jus check ur partions to be sure and dont format them as fat32 or ntfs jus leave them unallocated ,be careful dont delete ur windows partions if u have them unless u want to .

---

### Post by nick69 on 2007-11-26
> **samuel.rajesh said:**
> If u deleted the partion ,you should be able to boot from the live cd with out a password .

I agree with you since they are now unallocated  I should be able to boot from the live cd without a password 
that is why i am frustrated and one step away from giving up this linux version . . .

---

### Post by samuel.rajesh on 2007-11-26
> **nick69 said:**
> I agree with you since they are now unallocated  I should be able to boot from the live cd without a password 
that is why i am frustrated and one step away from giving up this linux version . . .

Dont give up yet mate hang on ,im sure there are people on this forum who can help you out ,can it have something to do with grub ,jus wait for someone to answer

---

### Post by nick69 on 2007-11-26
ok thanks anyway

---

### Post by bodhi.zazen on 2007-11-26
I am not following you.

If you are booting the ubuntu CD it automatically logs you in, just wait at the log in screen ....

If you are booting from hard drive, besides how can you boot from a hard drive if you wiped the partition, but if you are booting to a hard drive, first make sure caps lock is off.

It that is not the problem , boot to recovery mode

Enter :

```
passwd <user>
```

where user is you log in user name

Then reboot.

---

