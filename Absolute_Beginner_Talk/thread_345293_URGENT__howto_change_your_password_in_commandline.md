---
title: "URGENT : howto change your password in commandline ?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Maxwell7 on 2007-01-24
I changed my password yesterday through the gui and now I can't login anymore. I guess it is because a strange character in it. However, I can still log in in the commandline mode ( <CTRL>+<ALT>+<F1>  )

Can someone pleeeease tell me how to change my password (or reset it). I have exam tomorrow and can't access my files anymore. ](*,) ](*,)

---

### Post by stijn_pol on 2007-01-24
```
sudo passwd maxwell7
```
If your username is maxwell7 ;)

---

### Post by Maxwell7 on 2007-01-24
Well, it's not .... but I see where you are going.  :-) 

Thank you sooo much !! I was really panicking here

---

### Post by Bachstelze on 2007-01-24
If you're logged in as yourself, you can run just *passwd* to change your own password.

---

### Post by frolle on 2007-01-24
Did any of it help?

---

### Post by Maxwell7 on 2007-01-24
Yes, it did .. Thank you very much again for all of your help !! I LOVE Ubuntu and this community  !!


for those that wanna know what I did : 

I couldn't log in to Gnome anymore, because of a strange symbol in my password ( the "ç" ) My only explanation is that the gdm-login used a different keymap than my keyboard. When I switched to tty1 by pressing <CTRL>+<ALT>+<F1> I was able to login to my account. 

```
ubuntu@ubuntu:/$passwd 
current_password
new_passwd
new_passwd
```

So with your help I just changed the password back to the old one. :D 

Now i can prepare again for the exam. Thanks again

---

