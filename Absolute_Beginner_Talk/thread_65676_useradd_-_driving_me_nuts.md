---
title: "useradd - driving me nuts"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by tospig on 2005-09-14
hi everyone:

i'm still a complete novice with linux, and would like to know exactly what to type in terminal to add a user (using useradd), and then in winscp in order to access it.

i've searched the forums - and the internet, and found nothing helpful to me, and am starting to lose it :'(

any help will be rewarded, i don't know how but it will be :)

---

### Post by mlomker on 2005-09-14
useradd -G group,group,group,group,etc username

You can look at the contents of /etc/group to see what groups your current user is in.

---

### Post by czambran on 2005-09-14
go [http://www.ahinc.com/linux101/users.htm](here)

---

### Post by tospig on 2005-09-14
cheers for the guide czambran, i entered in some info, and got the error: 

'unknown group other' (i defined -G to be 'other')

thoughts?

---

### Post by Nequeo on 2005-09-14
[QUOTE=tospig]cheers for the guide czambran, i entered in some info, and got the error: 

'unknown group other' (i defined -G to be 'other')

thoughts?[/QUOTE]
 Well... My guess is you don't have a group called 'other'. To see what groups you *do* have set up, try
```

cat /etc/group | more

```
If you really do want to have a user group called 'other' (though that seems a little strange to me. Group names are supposed to be descriptive, like 'accounts' or 'family'), type
```

sudo groupadd other

```

And a quick word about pre-existing user groups. Adding a user to the 'admin' group will let them use 'sudo'. Adding a user to 'adm'  group will let them read all system logs, but won't give them use sudo.

---

### Post by tospig on 2005-09-15
now what do i put into winscp in order to connect?

---

### Post by tospig on 2005-09-17
also, when i try to add a user, i get the message 

'unable to lock password file'

what's happening?

---

### Post by transactionlogfiller on 2005-09-17
[QUOTE=tospig]also, when i try to add a user, i get the message 

'unable to lock password file'

what's happening?[/QUOTE]

I would guess that means you don't have permission. Did you sudo useradd?

---

### Post by tospig on 2005-09-17
that's the one..

damn sudo - always forget that, cheers transactionlogfiller

---

