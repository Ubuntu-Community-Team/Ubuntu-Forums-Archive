---
title: "Problem entering su in terminal"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by Macker on 2006-09-20
hello all,

im a Brand new person to linux, and let me start by saying im really sorry if im asking a really obvious question..

i installed ubuntu last night and so far i love it!!
i installed flash for mozilla too and was proud cos it was my first time ever installing anything through terminal and bash commands..

however i was installing java addon for mozilla i needed to login to "su" i take it this means superuser.. or root?

well i dont remember it asking me to setup a root account when i was installing it.. and i only used 1 password when setting up ubuntu and i tryed this password and its not working..

so my question is... can i now go back and setup my root account, or is it only possable when installing ubuntu for the first time..

thanks, and sorry again if its a stupid question

Mack

---

### Post by benfindlay on 2006-09-20
Ubuntu uses a sudo account rather than an su account. In order to run commands that need root access, you type ```
sudo [command]
``` This will prompt you for your current user's password and then execute your given command

hope this helps

---

### Post by RoyArne on 2006-09-20
```
sudo -s
```
will give you root privileges at the command line, use **exit**. When you're done.

```
sudo *command*
```

lets you run that particular command with root privileges.

---

### Post by maduranga on 2006-09-20
ok.. if u want to login as root from the terminal, just type "sudo -s" and try with the password u have.. If u mean login in from the login screen as root, then u have to give the permission and enable it before login.

---

### Post by Macker on 2006-09-20
sweet, thats 2 things i have learned already within 30 mins of joining the site.. i cant wait to get home after work and turn it on again.. i will try installing java addon tonight as my next mission.. i know it might be easy for u guys but its a challenge for me.. but i enjoy it..
thanks for the help everyone

i think im going to enjoy it here :D

---

### Post by 3rr0r on 2006-09-20
> **Macker said:**
> sweet, thats 2 things i have learned already within 30 mins of joining the site.. i cant wait to get home after work and turn it on again.. i will try installing java addon tonight as my next mission.. i know it might be easy for u guys but its a challenge for me.. but i enjoy it..
thanks for the help everyone

i think im going to enjoy it here :D

I HIGHLY reccomend getting automatix for easy installation of java/flash/ and other applets and basic files that at times can be difficult to correctly install for persons new to linux (including me) :tongue:

---

### Post by bulldog on 2006-09-20
And here is the link for Automatix

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

So you don't have to search for it.

---

### Post by Macker on 2006-09-20
Brilliant!! thanks lads, i will install that from home later and use it for installing java :D

thanks

---

