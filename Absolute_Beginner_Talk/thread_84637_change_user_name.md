---
title: "change user name"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by OBnascar on 2005-10-31
I want to change my user name but can not find how to do that. Or can one delete an account and create a new one. I prefer the first option if it can be done ?

If anyone knows how to do this, please let me know, post back, ok ?

thanks, jerry

---

### Post by matthew on 2005-10-31
There is a command that can change a users name. However the user cannot be logged in at the time it is done, which makes it a bit difficult if you are the only user. Also, your home folder would need to be renamed and the ownership and permissions to all files/folders in it would need to be modified as well. In other words it's a bit of a pain. If you still want to pursue it I recommend reading the manual page for the command "usermod" by entering this in a terminal:
```
man usermod
```
Make sure you understand everything fully before you use this! You can really mess things up.

I actually think making a new user is a better idea. Create the user, get things set up perfectly and use that account for a week or so and make sure you can do everythin you want to be able to do with the new account. Only after the new account has been tested for a while would I say you can feel pretty safe deleting the original account. (This is from someone who has had to massive surgery on a system because of doing something similar...it's better to go slowly and in managable steps with testing after each step than to make a huge mistake with no safety net.)

---

### Post by OBnascar on 2005-10-31
matthew,

I really botched this post up ! What I was refering to was changing a user name in the forums............lol.............sorry !

---

### Post by matthew on 2005-10-31
LOL. No problem. That one is a lot easier to take care of. Send a private message to either ubuntu-geek or kassetra and they can change your user name for you. :)

---

