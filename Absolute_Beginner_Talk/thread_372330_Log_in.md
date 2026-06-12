---
title: "Log in"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by holsv1 on 2007-02-28
I have just installed ubuntu 6.10 desktop on a server, but I can't log inn....
Is it an universal login name or what?


Thanks.

---

### Post by FyreBrand on 2007-02-28
When you went through the install process you were asked to create a user name and password.  That is the login you are supposed to use.  You can create other less privileged users after you login.

Do you remember the username and password?

---

### Post by holsv1 on 2007-02-28
Yes, I hve tryed that alot of times now but, login faild :(

---

### Post by FyreBrand on 2007-02-28
> **holsv1 said:**
> Yes, I hve tryed that alot of times now but, login faild :(Have you tried doing a recovery startup and then resetting your user password.  Also make sure you spelled your username right when you setup your system.  I've made that mistake before on a really late night reinstall and it's a pain.

---

### Post by bodhi.zazen on 2007-02-28
And make sure caps lock is off ....

---

### Post by holsv1 on 2007-02-28
hmm... I will take a reinstall now, but this time I WILL remember my username/password :P


But thanks for the replies :)

---

### Post by JermainWijnhard on 2007-02-28
I've had the same thing! dont re-install!

Try and install with the user name "OEM" and your own password. Then theres a command you need to input in the CLI that deletes the oem account creates the account name you designated. The command i mentioned earlier is mentioned during the install before you are asked to restart your comp.

---

### Post by bodhi.zazen on 2007-02-28
Don't need to re-install ...

Boot to recovery mode.

enter this command : ```
cat /etc/shadow
```

You will see your user name on the list ;)

OK then : ```
passwd user_name
```To re-set your password.

Then reboot and you should be good to go :twisted:

---

### Post by holsv1 on 2007-02-28
> **JermainWijnhard said:**
> I've had the same thing! dont re-install!

Try and install with the user name "OEM" and your own password. Then theres a command you need to input in the CLI that deletes the oem account creates the account name you designated. The command i mentioned earlier is mentioned during the install before you are asked to restart your comp.



nooo... to late :-/

---

