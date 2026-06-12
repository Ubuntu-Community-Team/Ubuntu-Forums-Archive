---
title: "samba problems"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by inmate#001 on 2006-08-19
when i try to access files shared over samba from my windows computer it asks me for a username and password i have tried my login info my account on my linux computer and it dosent work how do i fix this

---

### Post by GeekSpeek'r on 2006-08-19
might try your windows credentials

---

### Post by wjp.reg on 2006-08-19
After setting up the shares on Linux, did you 

```
sudo smbpasswd -a <username>
```

to set up the samba username/password combo, or is it that yo can't access the shares on the windows box?  This wasn't clear to me from your post.

---

### Post by kebes on 2006-08-19
By default, users on your computer are not added as samba users. You can add them by using the "smbpasswd" command. Thus, open a terminal and type:
```

smbpasswd -a bob
```

which will add user bob as a samba user. For more information on that command, use "man smbpasswd" on the commandline.

If you're not interested in using the command-line, you could install the "webmin" interface. It gives you a web-browser based point-and-click interface for running and administering servers. You can use it to do lots of things, including adding samba shares and users. You can also access it remotely (if you enable this functionality), which is great for administering your machine from afar.

Hope that helps.

---

### Post by inmate#001 on 2006-08-19
i cant accesss files shared on samba from my windows computer i can see the file but it requiers a password to access it and i did not set one as far as i know

---

### Post by djsroknrol on 2006-08-19
Are the shares mounted as "rw" (read/write) in your fstab?

---

### Post by wjp.reg on 2006-08-20
> **inmate#001 said:**
> i cant accesss files shared on samba from my windows computer i can see the file but it requiers a password to access it and i did not set one as far as i know

inmate#001;

As I said and kebes echoed; you MUST set up smbpasswd to permit access to your linux shares from windows, just as you had to set up a username and password to use ubuntu.

Do a search on samba HOWTO: for more info.

---

### Post by whatrucrazy on 2006-08-20
this thread is a great howto on setting up samba, its fairly easy to follow and implement, even if you don't have much experience in using the terminal. 

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

read this and hopefully your probs will be solved...;)

---

