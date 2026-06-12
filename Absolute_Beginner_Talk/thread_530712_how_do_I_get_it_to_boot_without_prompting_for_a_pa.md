---
title: "how do I get it to boot without prompting for a password?"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by derek45 on 2007-08-20
I just installed 7.04 on another machine.

I've got my others set up so you don't have to put in your password when it boots or when you work in Terminal.

I can't remember how to set this up.

I searched but couldn't find it.

How do I make it stop prompting me for a password?

Thanks

---

### Post by scrooge_74 on 2007-08-20
Hum if what you want is to avoid the need to log into the GUI just go to 

System > Administration > Login window> Security> enable automatic login for [username]

If you are the only one that uses the PC I think is ok.  In the prompt are you refering for doing admin task?  If so please refrain from that is not a good security idea

---

### Post by NilsE on 2007-08-20
Assuming Ubuntu go into System/Administration/Login window then the security tab and enable automatic login and select your ID


EDIT: Scrooge_74 clicked faster than I did and beat me to it

---

### Post by nitro_n2o on 2007-08-20
you can type sudo -i in the terminal and it'll not ask you for a password for the session.. 
but generally you shouldn't do that it a security risk

---

### Post by cmnorton on 2007-08-20
I also found this post.

[http://ubuntuforums.org/showthread.php?t=293529](http://ubuntuforums.org/showthread.php?t=293529)

---

### Post by derek45 on 2007-08-20
Got it,  Thanks:biggrin:

---

