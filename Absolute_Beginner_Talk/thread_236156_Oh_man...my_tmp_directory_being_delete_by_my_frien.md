---
title: "Oh man...my /tmp directory being delete by my friend!!!"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by penguinKabuki on 2006-08-14
oh man...
my friend just delete the /tmp files by his mistake.
i was teaching him tu play with command....suddenly.....
he use the 
 rm -r /tmp

the moment he delete the directory.....
he login as...
root!

now...i cannot login into my computer....
what should i do to recover by my penguin?

---

### Post by bruce89 on 2006-08-14
/tmp gets cleaned on every reboot AFAIK, so just reboot, and try logging in again.
You might need to recreate the /tmp folder though:
```
cd /
sudo mkdir tmp
```

I notice you were logged in as root, that is very dangerous, use sudo instead - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).  It's a good thing it was only /tmp, as opposed to /.

---

### Post by penguinKabuki on 2006-08-14
thx...
the tmp dir back!!!

but other problem appear...

when i want to login....its keep asking for my password...
wierdly,if i login with console....it works!!!!

huhu....help me~~~

---

### Post by moma on 2006-08-14
Do this:

$ [COLOR="Green"]sudo mkdir /tmp[/COLOR]
$ [COLOR="Green"]sudo chmod 1777 /tmp[/COLOR] 

It will set the 't' sticky bit permission flag.
[http://www.linuxdevcenter.com/pub/a/linux/lpt/22_06.html]("http://www.linuxdevcenter.com/pub/a/linux/lpt/22_06.html")

Your /tmp directory must look like this (notice the sticky 't')
$ [COLOR="Green"]ls -ld /tmp[/COLOR]
drwxrwxrw[COLOR="Red"]t[/COLOR] 18 root root 8192 2006-08-14 14:01 /tmp

---

### Post by penguinKabuki on 2006-08-14
i got 

drwxrwxrwt 16 root root 4096 2004-02-20 10:47 /tmp

---

### Post by penguinKabuki on 2006-08-14
thx..........
I GOT MY PENGUIN BACK!!!
thx~~

---

