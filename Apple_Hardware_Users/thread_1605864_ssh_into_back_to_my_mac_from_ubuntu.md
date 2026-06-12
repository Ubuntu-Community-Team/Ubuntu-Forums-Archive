---
title: "ssh into back to my mac from ubuntu"
date: 2010-10-25
forum: Apple Hardware Users
---

### Post by powerpants on 2010-10-25
hi guys,

i have successfully ssh'd into one of my other macs from my macbook pro by using

```
ssh -6 "login@computername.firstname\.lastname.members.mac.com."
```

a little annoying because my mobileme username is firstname.lastname.

anyway, i am now trying to use the same command from my ubuntu machine, and i keep getting the error

```
ssh: could not resolve hostname computername.firstname\\.lastname.members.mac.com.:No address associated with hostname
```

(there are supposed to be two \'s between firstname.lastname in the above line.)

any ideas as to what is going on? i am wondering if it has something to do with the \ i have to use to delimit the . in my mobileme username.

thanks!

---

