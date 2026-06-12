---
title: "Source list and source.list.d"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Mirena on 2007-01-09
I am  a newby and kind of confused, are there two source list in Ubuntu edgy Eft? 
the botton line is I can't update or access the repositories as I explained in my other post, the sorce.list is Ok (source-o-matic made)

but  when I tried
logar@Tiamat:~$ cat /etc/apt/sources.list.d/edgy-multiverse.list
# automatically added by gnome-app-install on 2006-12-19 03:56:16.434353
deb None edgy multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
deb None edgy-updates multiverse

I am wondering what is it supposed to say instead of None so I can edit that sorce list as possibly solve the problem, I change the first line with the info on the other list and now I have a line 3 error  that I cannont correct, I tried browsing the forums and the web to  get a correct 3rd line  to no avail
Help please!](*,)

---

### Post by quartzy on 2007-01-09
I don't have anything in my /etc/apt/sources.list.d/ dir.. have you tried moving them to something else and making it rebuild them? (move them rather than deleting).

---

### Post by Mirena on 2007-01-09
I did not know it existed until I ran this command   yesterday and got the gedit to  find it, I have tried to rebuild it but I just can´t figure out the 3rd line me.

---

