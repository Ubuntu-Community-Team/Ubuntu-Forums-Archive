---
title: "fstab - automounting an external drive"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Wardazo on 2007-03-23
Hi

I'm trying to mount an external hard drive at boot. I have included the following line in my fstab:

/dev/sda1       /home/wardazo/Lacie         vfat        rw,user,auto,sync       0      0

But, it doesn't mount. When I click on the the external harddrive symbol on my desktop, it mount correctly in /home/wardazo/Lacie.

What am I doing wrong? I thought "auto" automounts at boot.

Very grateful for any help.

Ward

---

### Post by twikletoes on 2007-03-23
do it manually in the command line by typing 
```
sudo mount /dev/sda1
```

---

### Post by twikletoes on 2007-03-23
if that doesn't work 
```
dmesg | tail
```
then review the error message

---

### Post by Wardazo on 2007-03-24
Thanks for the reply, but mounting it is not the problem.

Automounting it at boot the problem.

If anyone has any other ideas I'd be really grateful.

Thanks

Ward

---

### Post by basilwatson on 2007-03-24
> **Wardazo said:**
> Hi

I'm trying to mount an external hard drive at boot. I have included the following line in my fstab:

/dev/sda1       /home/wardazo/Lacie         vfat        rw,user,auto,sync       0      0

But, it doesn't mount. When I click on the the external harddrive symbol on my desktop, it mount correctly in /home/wardazo/Lacie.

What am I doing wrong? I thought "auto" automounts at boot.

Very grateful for any help.

Ward

Is this of any help??

[http://www.smorgasbord.net/book/export/html/195]("http://www.smorgasbord.net/book/export/html/195")

I am having the same trouble 

Stephen

---

### Post by bulldog on 2007-03-24
What are you trying to achieve?
The mounting can't be done before the OS has booted,ie. has 'read the fstab' file.

External drives will be auto mounted like you said it does,so what is your purpose.

If you want to boot from the external drive you have to set it in the BIOS,like an option boot from USB device.

---

### Post by Wardazo on 2007-03-24
Hi

Basically I'd like to turn on a computer and have it mount an external hardrive without having to type anything.

The computer I refer to is simply a file server and I like to serve the files that are on my external hard drive too. It works perfectly with the external HD but only... once I've mounted it manually.

I though inluding auto in the fstab would mount it automatically when the computer is starting up... it would seem that i am wrong. So how is it done ;)

Thanks

ward

---

### Post by chamberlain2006 on 2007-03-24
You can go to System>Preferences>Sessions>Startup Programs and add "sudo mount /dev/sda1".  This will mount the drive when you sign in.

---

### Post by bulldog on 2007-03-24
As far as I know,and I have an external drive too,you won't have to type anything.
If ubuntu is booted you'll find your external drives in the /media folder.

---

