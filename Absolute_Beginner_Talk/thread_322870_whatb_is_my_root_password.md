---
title: "whatb is my root password???"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by joejack on 2006-12-21
what is my root password??? i cant figure it out, please let me know

---

### Post by LookTJ on 2006-12-21
I think root is disabled by default?

Why would you want to use the root account?

Don't you mean your sudo password? If so, it's your password on the user you use.

---

### Post by scxtt on 2006-12-21
there is no root password, preface commands w/ **sudo** and enter YOUR password ...

---

### Post by Ferri on 2006-12-21
In Ubuntu usually there's the root account is disabled. You can do administrative tasks using "sudo" (just put sudo before de command). It will ask for the password, which is the same you  have for your user.

---

### Post by Sef on 2006-12-21
To understand why root has been disabled by default, read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by lucky_chouhan on 2006-12-21
just start ubuntu in recovery mode and type passwd in terminal enter you password and restart. then go to system -> admininstrator -> users & groups and select your user and view properties here check the box. (administrator authentication allow for this user) and restart.:)

---

### Post by daniminas on 2006-12-21
hmm.. in my Dapper i type:
```
$sudo su root
```

then MY password... and you're root! :confused:

---

### Post by paddy2706 on 2006-12-21
actually restarts are not required. just do a sudo passwd and after authenticating with your user password enter your new root password. after that you can login as root.

---

### Post by dmjones500 on 2006-12-21
You can type

```
sudo -i
```

and enter YOUR password to access a root prompt.

---

