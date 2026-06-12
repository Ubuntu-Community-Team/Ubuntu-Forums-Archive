---
title: "Sudo password???? help"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Cragsterboy on 2008-02-29
Hey,

yesterday i could get into the root@cragsterboy on terminal by typing 'Sudo -i' and when i do it today it says enter password, so i put my password i use in and it doesn't work, i dont know whats happened but its really annoyin me cos i need to get into the root so i can install beryl.


~Crag

---

### Post by Joeb454 on 2008-02-29
1) It's your normal user password

2) Try compiz-fusion instead, beryl isn't being developed anymore :)

---

### Post by Rodney2 on 2008-02-29
Are you sure you do not have the Caps Lock on, the password is usually always in lower case only.

---

### Post by Cragsterboy on 2008-02-29
ok i type in my normal password and all it does is this

```

[sudo] password for cragsterboy:
<password>cragsterboy@cragsterboy:~$ <password>
bash: <password>: command not found
Cragsterboy@cragsterboy:~$

```

It just does that when i enter my password :(

And thanks for telling me about compiz-fusion

~Crag

---

### Post by mister_pink on 2008-02-29
Are you pressing return twice after the first line? You shouldnt see anything appear as you type your password, but it is being entered!

Edit: Also, what version are you on? 7.10 has compiz fusion by default. If you dont have it you can probably add it via the normal Add/remove programs route

---

### Post by Cragsterboy on 2008-02-29
awww nice one!


thankyou worked it out (stupid me)


Cheers :KS

---

### Post by agray on 2008-02-29
the root account is locked by default in ubuntu.  did you already have access to it?  if not, you need to enable the account by typing

*sudo passwd*   (then it will prompt you for your user account password)
*[sudo] password for {user account name here}:*    (it will prompt you again with)
*Enter new UNIX password:*   (this will be the password for root, then it prompts you one more time with)
*Retype new UNIX password: *   (then it should say)
*passwd: password updated successfully*

---

### Post by rbprogrammer on 2008-02-29
i'm really surprised no one said that it is really unsafe to log in as root at all.  why did you need root access anyway? wouldn't just a plain sudo do just fine.

---

### Post by aysiu on 2008-02-29
If you want Compiz Fusion, you shouldn't have to log in as root or even use the terminal:
[http://www.psychocats.net/ubuntu/desktopeffects](http://www.psychocats.net/ubuntu/desktopeffects)

---

