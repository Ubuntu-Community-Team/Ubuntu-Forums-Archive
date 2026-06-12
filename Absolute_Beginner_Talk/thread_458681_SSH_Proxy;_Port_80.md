---
title: "SSH Proxy; Port 80"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-05-29
Greetings,
I have been reading on the Ubuntu Wiki, under SSHHowto, and saw [SSH as a Proxy](https://help.ubuntu.com/community/SSHHowto#head-edc382321673e192fe467cb5d73f2b5e723ae806)

Well, let's say I want to use port 80 instead of port 1080 for SOCKS, and I want to be able to use my internet connection from a library computer for instance. I want to be able to connect to my SSHd with the command:
```
ssh -D 80 user@host
```

But, I try it on localhost, and it immediately spits out this error:
> drsmall@drsmall:~$ ssh -D 80 localhost
Privileged ports can only be forwarded by root.


How can I forward port 80 for my SSHd, and be able to use my internet connection from the library?

Sincerely,
Dr Small

---

### Post by homergreg on 2007-05-29
Try :

sudo ssh -D 80 localhost


I don't know about how the command itself will work beyond that, but the error is due to not using sudo in front of ssh

---

### Post by Dr Small on 2007-05-29
You're a champ!
I should have thought about that :S

Dr Small

---

