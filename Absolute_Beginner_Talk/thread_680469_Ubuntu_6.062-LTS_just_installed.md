---
title: "Ubuntu 6.062-LTS just installed"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by zonekeeper on 2008-01-28
But,,,,how do I set the fikkin root password....this is on a n HP ProLiant 3G with dual drives. Everything went wonderful.....now asks for root passoword....no where did it ask me to set one????

---

### Post by steveneddy on 2008-01-28
Language, buddy. This is family forum.

What is your log in password?

---

### Post by emarkd on 2008-01-28
You didn't set one.  Ubuntu doesn't set one automatically, and you really don't need one.  Your account that you created at startup is a normal user account but of the admin group, so your password can do everything that root can.  You just have to enter it to do something admin related.

---

### Post by Rocket2DMn on 2008-01-28
Should be the same as the password you set for your username.  Where/why are you logging in to root?

---

### Post by zonekeeper on 2008-01-28
> **steveneddy said:**
> Language, buddy. This is family forum.

What is your log in password?

Frikkin isn't bad language on any known planet.

I used Matt and matt. No joy. Even swapped the caps around
. No joy.

---

### Post by emarkd on 2008-01-28
Um, if that's really your login and password you should change it quickly and try not posting it in public forums in the future.

He meant that your password works like the root password, although they're not exactly the same thing.  You can't login as root using it, but you can do anything that root can do after you login as yourself

---

### Post by steveneddy on 2008-01-28
> **zonekeeper said:**
> Frikkin isn't bad language on any known planet.

I used Matt and matt. No joy. Even swapped the caps around
. No joy.

So, matt is your login name?

and the password you set is......?

---

### Post by steveneddy on 2008-01-28
> **emarkd said:**
> Um, if that's really your login and password you should change it quickly and try not posting it in public forums in the future.

He meant that your password works like the root password, although they're not exactly the same thing.  You can't login as root using it, but you can do anything that root can do after you login as yourself

Just give us your IP address....

---

### Post by Rocket2DMn on 2008-01-28
If you need to change the root password, you can reboot the computer into the recovery kernel and change the password with the command
```
passwd
```
NEVER post your password on the forums, please change it now.  You can run "passwd" on your regular login too to change the password.

---

### Post by Rocket2DMn on 2008-01-28
> **steveneddy said:**
> Just give us your IP address....

Very not funny.

---

### Post by h0ax on 2008-01-28
su
followed by your password will not give you root access

you must do
sudo -s
then enter your regular password

or you can do
sudo passwd root
and set a password for the root account
so that when you do 
su
you can put that in

hope that helps

---

### Post by zonekeeper on 2008-01-28
> **steveneddy said:**
> Language, buddy. This is family forum.

What is your log in password?

Frikkin isn't bad language on any known planet.

I used Matt and matt. No joy. Even swapped the caps around
. No joy.


This machine is not networked right now, so good luck getting in...heh....brb

---

