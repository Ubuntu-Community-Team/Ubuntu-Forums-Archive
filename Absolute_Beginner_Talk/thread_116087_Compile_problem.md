---
title: "Compile problem"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by nkingcade on 2006-01-11
I have a question. I opened a tarball. Clamav-0.88. Went to the resulting Clamav-0.88 directory. Ran ./confclamav-0.88.tarigure. There appeared to be no errors. I then went to run "Make". The machine returned "no makefile found in the clamav-0.88 directory. Am I missing something?

Neal

---

### Post by 23meg on 2006-01-11
Look for a file called "Makefile" in the directory; is it there? Are you sure you've changed to the clamav-0.88 directory with the "cd" command?

---

### Post by DoorGunner on 2006-01-11
go to the ubuntu guide and make sure you " install Basic Compilers "

[http://www.ubuntuguide.org/#build-essential](http://www.ubuntuguide.org/#build-essential)

then go back and try you compile

---

### Post by nkingcade on 2006-01-12
DoorGunner, 23 Meg,

Thanks alot. As it turns out, the config file found I was lacking a couple of libraries. I installed them an the make file showed after running ./configure again. To you, again "thanks".

Neal

---

### Post by DoorGunner on 2006-01-12
any thing for another ubuntuian... :cool:

---

