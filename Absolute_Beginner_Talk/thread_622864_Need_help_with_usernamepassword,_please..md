---
title: "Need help with username/password, please."
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-11-25
I have just installed Gutsy on a computer but seem to have made a 'Boo-Boo'.

Although I'm sure I know what username and password I entered, the login screen tells me that I have entered the wrong information.

Is there a way in which I can access my username/password information, so as to check it or change it, or do I have to completely reload the program?

---

### Post by Pumalite on 2007-11-25
[https://help.ubuntu.com/community/LostPassword?highlight=%28password%29](https://help.ubuntu.com/community/LostPassword?highlight=%28password%29)

---

### Post by L Campbell on 2007-11-25
> **Pumalite said:**
> [https://help.ubuntu.com/community/LostPassword?highlight=%28password%29](https://help.ubuntu.com/community/LostPassword?highlight=%28password%29)

Thanks for your help.

IF  I am understanding this correctly, I have the option of entering ' passwd ' or ' username ' and then entering what I want that to be?  Or did I mis-understand this?

qwer

---

### Post by Ub1476 on 2007-11-25
```
passwd <username>
``` ---> where it says "username" write in your username

```
writing in new password here...
```

```
init 2
```

---

### Post by The Cog on 2007-11-25
Once you are in rescue mode, you can change the password of a user (fred for instance) with the command
**passwd fred**
notice the bad spelling of the word passwd.
If you don't know your user name because you may have mis-typed it during install, the command 
**ls /home**
(that first letter is a lower-case L - ls means list)
will show you which user names have been given home directories, which tells you which users there are on the system.

Hope this helps

---

### Post by L Campbell on 2007-11-25
> **Ub1476 said:**
> ```
passwd <username>
``` ---> where it says "username" write in your username

```
writing in new password here...
```

```
init 2
```

Thanks for your help.

I can see that I'm too confused here and am going to do a re-install.

Kind regards.

---

### Post by frank002 on 2007-11-25
Make sure you are using the same case. In other words, if when you set your log in and password you were using uppercase, then switch to uppercase at log in. Just a thought.

---

