---
title: "sudo -s potential hacker prob"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Xorg.conF on 2007-12-25
I have noticed whenever I use the sudo command in terminal and put in my password, it wont ask for it again for about 10 to 20 minutes.  I see this as a security risk, I know Linux safer then windows yea, but all the dude on his comp has to do is get into mine within the time and type sudo -s and he's now the root.

I need to reset the counter to 0, every time I type sudo it should ask for a password.

THX

---

### Post by LaRoza on 2007-12-25
> **Xorg.conF said:**
> I have noticed whenever I use the sudo command in terminal and put in my password, it wont ask for it again for about 10 to 20 minutes.  I see this as a security risk, I know Linux safer then windows yea, but all the dude on his comp has to do is get into mine within the time and type sudo -s and he's now the root.

I need to reset the counter to 0, every time I type sudo it should ask for a password.

THX

15 minutes actually. It can be set to ask everytime.

It is a convenience thing, and I doubt that any cracker would be able to take advantage of it unless they deliberately and knowinly tried to take advantage of your computer.

You can, if you wanted, make an account that does not have sudo privileges if you anticipate others being able to access this computer.

---

### Post by mikewhatever on 2007-12-25
Try this [http://ubuntuforums.org/showthread.php?p=116697#post116697](http://ubuntuforums.org/showthread.php?p=116697#post116697)

---

### Post by frup on 2007-12-25
> **LaRoza said:**
> 15 minutes actually. It can be set to ask everytime.

It is a convenience thing, and I doubt that any cracker would be able to take advantage of it unless they deliberately and knowinly tried to take advantage of your computer.

You can, if you wanted, make an account that does not have sudo privileges if you anticipate others being able to access this computer.

Actually unless user understand terminal commands it would be pretty easy....

UPGRADE yOUR cOmpiZ on j00r LuniX!!!!

first

sudo this blaah blaah
[password]
[.various commands.]
install my script to make it easy
./script
...
[script executes vulnerability]
...
script does it

---

### Post by LaRoza on 2007-12-25
That is pure social engineering, the best way to get into any system, even BSD.

---

### Post by Xorg.conF on 2007-12-25
well I set the timer to zero from mikewhatever's link.  I think if it's possible then it should be heeded, I don't really need the convenience anyway.   

thx for the help

---

### Post by frup on 2007-12-25
I personally think 5 mins should be the default not 15, 5 is convenient enough.

The trouble with social engineering is that an oblivious user will likely enter the password even if the timer is set to 0.

---

