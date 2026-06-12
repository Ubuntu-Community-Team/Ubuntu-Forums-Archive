---
title: "Superuser Password???"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by think13 on 2006-09-24
Well, I just got Ubuntu installed, and I want to change the default boot OS.  The only way I can find to do that is to become the superuser and edit a file in /boot/grub.  In the console I type su and then enter my password.  It then says 'Authentication failure' which I believe is fancy talk for 'You entered the wrong password'.

Help?

---

### Post by bodhi.zazen on 2006-09-24
Ubuntu uses sudo rather then su.

type sudo <commnad> or sudo su in the terminal.

Enter you user log-in password. You will not see the text on the screen as you type your PW.

---

### Post by think13 on 2006-09-24
Thank you, that worked!

---

### Post by Brunellus on 2006-09-24
> **think13 said:**
> Thank you, that worked!
The "why" and "wherefore" of this is dealt with at 

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

Always a good page to read to understand users, permissions, and how ubuntu handles them.

---

### Post by jkvv_1973 on 2006-11-01
> **bodhi.zazen said:**
> Ubuntu uses sudo rather then su.

type sudo <commnad> or sudo su in the terminal.

Enter you user log-in password. You will not see the text on the screen as you type your PW.


I was using "su -p" (trying to install some sound theme)

and I had authentication failure...I guess Ill try this later when 

I get home...Ubuntu rox!:KS

update can someone put "Solved" on the thread title...thanks ADMIN

---

### Post by BRUNOALVISIO on 2007-05-11
I am an new user of UBUNTU.I typed "sudo" in the terminal and the following message appeared:

bruno@Notbook:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
bruno@Notbook:~$

It does not ask me for my password.Could somebody tell me what to do?

I have another doubt: I am trying to install xmgrace. Is it completely necessary to log in as the super-user?.

Thank you

Bruno

---

### Post by carlosqueso on 2007-05-11
the proper use for sudo is ```
sudo <command>
``` where command is what you want to do.  If you need to do many commands, you can use ```
sudo -i
``` or ```
sudo su
```

---

