---
title: "error msg help...."
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by night_raiders on 2007-06-27
Ok so when i try to install something mainly stuff from the add/remove section i get this error msg.... what does this mean? how can i fix it?

i am NEW to linux/ubuntu so if possible say it in words that i could probaly understand...

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E:_cache->open() failed, please report.

---

### Post by CherenkovBlue on 2007-06-27
the package manager was interrupted last time it was installing something, open your terminal and type :
sudo dpkg --configure -a then press enter, this should solve your issue,

---

### Post by night_raiders on 2007-06-27
well when i did that it said password: so do i type my user pass i tried and it said incorrect so..... what do i do

---

### Post by CherenkovBlue on 2007-06-27
you're password should have worked. i've noticed that when people cant see their password being typed in it freaks them out... perhaps you mistyped it?

---

### Post by Pizzarth on 2007-06-27
not your user password, the system/root password. you were asked for both when you insatlled. One for your user, and one for root

---

### Post by cogadh on 2007-06-27
> **Pizzarth said:**
> not your user password, the system/root password. you were asked for both when you insatlled. One for your user, and one for root
Whoa, there! It is not asking for a root password, Ubuntu doesn't require a root password and it does not create one when you install it. Ubuntu uses sudo (**S**uper**U**ser **DO**), which requires your normal user password to temporarily enable root-like access.

---

### Post by CherenkovBlue on 2007-06-27
> not your user password, the system/root password. you were asked for both when you insatlled. One for your user, and one for root

theres no root  password, we have sudo ... its your user / log in password.

---

### Post by night_raiders on 2007-06-27
well even when i do that it says incorrect

---

### Post by tcoffeep on 2007-06-27
It worked for me by just pushing enter...

Maybe you could try that?

---

### Post by Pizzarth on 2007-06-27
oh... hm... yea I did the same thing CherenkovBlue. I was just under the impression that wanting to gain superuser privelidges required the root password ^^ my bad. IMO that makes more sense =/ doesn't it?

thanks cogadh, but i know what sudo is :P

---

### Post by cogadh on 2007-06-27
Are you sure you are using the same password you use to log in to Ubuntu? Are you trying this under the default user account you created when you installed Ubuntu?

> **Pizzarth said:**
> thanks cogadh, but i know what sudo is :P
The explanation was more for night_raiders anyway.

---

### Post by night_raiders on 2007-06-27
lol this is my computer the rest of the family doesnt use it... so i have the default account....

---

### Post by CherenkovBlue on 2007-06-27
anywho... your password still isnt working?

---

### Post by Pizzarth on 2007-06-27
you do all the usual stuff? ^^ check for caps, make sure numlock is on..

---

### Post by night_raiders on 2007-06-27
i will just tell you this my pass is all numbers

---

### Post by tcoffeep on 2007-06-27
Did you try the method I shot at you?

Like I had said, it said something like that...and I just pushed enter.
Uhm...perhaps you can also try writing your username before you write your password...

Get back to me...

---

### Post by CherenkovBlue on 2007-06-27
> you can also try writing your username before you write your password

that wont work.

---

### Post by tcoffeep on 2007-06-27
I'm new to this...

It did work for me. Maybe I'm just confusing something with something else...
Sorry.

---

### Post by CherenkovBlue on 2007-06-27
you should probably go to system>administration>users and groups and change your password

---

### Post by jrev on 2007-06-27
You type sudo before a command that isn't allowed to the normal user.

The first user being registered on your PC is considered to be a reliable person so the system gives him or her the power to act as an administrator for a few minutes by typing this magic word : **sudo **

of course you have to put a command after the sudo otherwise you ask permission for nothing.
If you just want to be like the supervisor for a couple of minute you type **sudo su**

then you are the supervisor for the next commands to be typed.
I don't know if I have made myself clear ?:D

---

### Post by CherenkovBlue on 2007-06-27
any luck  night_raiders?

---

### Post by night_raiders on 2007-06-27
i got that fixed now but now when i open the package for frostwire and when it loads so i can click install package it says error: failed to satisfy all dependencies (broken cache)

---

### Post by CherenkovBlue on 2007-06-27
missing some libraries maybe? frostwire needs a java runtime environment...do you have one installed? i dont remember if it will install java for you or not.

---

