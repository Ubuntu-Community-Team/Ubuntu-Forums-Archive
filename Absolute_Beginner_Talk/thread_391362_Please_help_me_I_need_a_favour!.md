---
title: "Please help me I need a favour!"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by camz on 2007-03-23
Hi guys I need a little help.
Could someone do this please:

Please put in this command
> sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup

And then this one:
> sudo gedit /etc/apt/sources.list

Could someone please tell me what comes up when they have put in the second code. It will open in Gedit so could you please copy and paste that entire selection of text onto a post so I can set mine back to default. Sorry I had to do this but I had messed it up.

Thanks a lot,
Camz

---

### Post by seshomaru samma on 2007-03-23
each person's sources list is different 
if you messed up your list you can generate a new one with [_**this site **_]("http://www.ubuntu-nl.org/source-o-matic/")

---

### Post by Foudre on 2007-03-23
it doesn't really differ that much, but it depends if say you are on dapper, or edgy, or the 386 or athlon build, you need to supply with more info then that, or that website might work, but web site hopping is annoying and tends to lead to you doing things you shouldnt anyways. IE breaking it by doing something or like installing some script. Well just say what version you are using, or if you already took care of this or what ever

---

### Post by camz on 2007-03-23
Im using Edgy 6.10, please help, but for the moment I will try his method

---

### Post by camz on 2007-03-23
His link helped a lot, but if I could have the original defaults it would be even better!

---

### Post by chewearn on 2007-03-23
I using edgy 32-bit, here is my sources.list; "official" repos are enabled except unstable; only non-official repo in the list is beryl

 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

---

### Post by camz on 2007-03-23
Thanks

---

