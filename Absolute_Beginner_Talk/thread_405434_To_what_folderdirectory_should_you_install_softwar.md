---
title: "To what folder/directory should you install software?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by dimbulb1024 on 2007-04-09
I was wondering what is the proper folder/directory to install software to? Is there one?

Example: I have Moneydance which is a .sh file. To install it they instruct you to put it in the folder you wish to live and run the file. In Windows it was easy - Programs, but I am not sure about Linux. Do you use /ect, /usr, /opt ...

---

### Post by Compyx on 2007-04-09
Generally you put anything that isn't installed via your distributions package manager in /usr/local when installing for multiple users. Binaries go in /usr/local/bin and libraries go in /usr/local/lib.

That's the way I always do it, and many packages that build from source work this way (ie VICE).

---

### Post by taurus on 2007-04-09
I usually install extra stuff to /usr/local/bin unless you want to put it into /usr/bin.

---

### Post by terdon on 2007-04-09
Yes, that is the most common, but feel free to set up anything you feel comfortable with. It is your choice really...

---

### Post by dimbulb1024 on 2007-04-12
Thanks Compyx, taurus and terdon for your replies and the speed of them. You all replied within 6 minutes. WOW !

Unfortunetely, I didn't thank you as quickly. Noobies, what are you going to do? :roll:

---

### Post by aysiu on 2007-04-12
/opt is another option.

---

