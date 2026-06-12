---
title: "Mounting time capsule drives in Ubuntu? (Connection refused)"
date: 2010-01-04
forum: Apple Hardware Users
---

### Post by DaSal on 2010-01-04
So I've been looking for a way to mount my time capsule drives under Ubuntu, and found some guides, but none of them work for me. Apparently what you need to do is:

sudo mount.cifs //10.0.1.1/timecapsulename/dirname /media/timecapsule/ -o pass=pa55w0rd

My time capsule's ip is 192.168.1.10, it's name is "Time Capsule", the drive I'm trying to mount is called Movie HD

If I input the following command:

sudo mount.cifs //192.168.1.10/Time Capsule/Movie\ HD /media/timecapsule/ -o pass=mypassword

I get a connection refused error. I tried a couple different variations such as "/"Time Capsule"/Movie HD", etc, every possible combination, but I get a connection refused error (111) every time. Help? :P

(I have two drives on my time capsule, the internal, Movie HD, and an external usb one, Media HD, I want to actually mount them both)

On my time capsule I did set it guest access to read only... :(:confused:

Also, when I go to my places> network I do see the time capsule in the list, but I get an error message that it can't access the shares when I try to open it.

---

### Post by schucki.be on 2010-01-17
Hello DaSal,
I also had troubles mounting my Time Capsule.
Now I can!
I installed smbfs and smbclient and changed my fstab.
This is my fstab addition:
//10.0.0.1/TimeCapsule/map /media/capsule cifs password=password,rw,iocharset=utf8,file_mode=0777 ,dir_mode=0777.

Does that work for you?

Good luck!

> **DaSal said:**
> So I've been looking for a way to mount my time capsule drives under Ubuntu, and found some guides, but none of them work for me. Apparently what you need to do is:

sudo mount.cifs //10.0.1.1/timecapsulename/dirname /media/timecapsule/ -o pass=pa55w0rd

My time capsule's ip is 192.168.1.10, it's name is "Time Capsule", the drive I'm trying to mount is called Movie HD

If I input the following command:

sudo mount.cifs //192.168.1.10/Time Capsule/Movie\ HD /media/timecapsule/ -o pass=mypassword

I get a connection refused error. I tried a couple different variations such as "/"Time Capsule"/Movie HD", etc, every possible combination, but I get a connection refused error (111) every time. Help? :P

(I have two drives on my time capsule, the internal, Movie HD, and an external usb one, Media HD, I want to actually mount them both)

On my time capsule I did set it guest access to read only... :(:confused:

Also, when I go to my places> network I do see the time capsule in the list, but I get an error message that it can't access the shares when I try to open it.

---

