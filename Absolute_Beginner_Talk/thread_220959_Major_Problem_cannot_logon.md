---
title: "Major Problem cannot logon"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Demetrios on 2006-07-22
I have installed Ubuntu 6.06, and for some reason I must have spaced the user name or it did not appear I don't have one. I did input a password. The system was installed using the oem option. Any idea how to login, without a user name?? ](*,) ](*,)

---

### Post by trent dillman on 2006-07-22
You could reboot into recovery mode, which will give you a root terminal. Then, you could do
```
tail /etc/shadow
```
Your user name should be towards the end.

---

### Post by Demetrios on 2006-07-22
Thanks

I did as instructed but the last line in the code is oem, at the end of that line there is no name only 99999:7:::

It appears I did not input a user name, what happens now?

---

### Post by flargen on 2006-07-22
I don't know if this will work for sure, but if you can get to a root console in recovery mode, try making a new user:
```
adduser *username*
```
Choose a password etc, reboot and you should be able to log in as your new user.

---

### Post by Demetrios on 2006-07-22
Excellent

Right on the money.........Thanks:p :p :p :p

---

### Post by flargen on 2006-07-22
Glad to help :)

---

### Post by trent dillman on 2006-07-22
Be sure to add that new user to the admin group so you can use sudo!

---

### Post by PriceChild on 2006-07-22
You must have done an "OEM" install.

These are intended for computers to be resold on. oem is a temporary account which is only meant to be used to make the new users permenantly before being deleted.

You WILL have entered a password at some point in the instillation.

Try using:
username: oem
password: <<whatever you told it>>

---

