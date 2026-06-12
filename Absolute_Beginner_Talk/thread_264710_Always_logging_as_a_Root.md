---
title: "Always logging as a Root"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by ubbu on 2006-09-25
Hi,

How is this possible ? I mean I have to type sudo nautilus in terminal or write password etc, Right it could be harmful for security reasons but how can I ignore these and log in as a root always

thanks in advance

---

### Post by bodhi.zazen on 2006-09-25
Yes. This is neither secure or safe. When logged in as root you can damage your configuration. As a non-root user you can not. Obviously if you want you can access root when you want with sudo. This gives protection and a "heads up" you are about to change your sys config.

If you run as root you will get no warning and may inadvertently do some real damage.

Not to mention security.

---

### Post by nereid on 2006-09-25
You could enable the root account. The first password is your user password and the next to times enter the new root password.

```

sudo passwd

```

Then you can log in as root with your brand new root password. But beware! There is a reason, why you should not be logged in as root!

---

### Post by ubbu on 2006-09-26
thanks for the responds

the thing is, for example I am writing a file and want to save it into the /var directory but the program I am using lets say gedit comes up with an error message that I don't have the permission to write ? THings like that

how can I solve this problem with out logging in as a root ? Or logging as a root won't solve this problem ?

thanks in advance

---

### Post by bluefrog on 2006-09-26
you can always gksudo gedit
which opens gedit with root.
do your modification save the file and close gedit to avoid making mistakes..

works with all kind of programs

you can put shortcut on your panel, edit them and add gksduo in front of the command. so then opening things with root is just one click away. closing the program after use is a good practice...

James

---

### Post by aysiu on 2006-09-26
Why is it such a pain to enter a password? Does your bank issue you a passwordless ATM card? Does your credit card have you log into their website without a password? Does your apartment or house not require a key to get in?

Just create a launcher for the command ```
gksudo nautilus
``` and be done with it.

---

