---
title: "Create split archives?"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Kimm on 2007-01-10
Does anyone know how I can split archives (preferably ZIP or RAR, but pretty much anything will do)?

I need to be able to unpack them in WinZIP on a windows computer later on...

---

### Post by kidders on 2007-01-10
Hi there,

Try the "split" command. (See split's man page for info.) It's used to divide large files into smaller bits.

---

### Post by Seine on 2007-01-10
And when you get to the other end you use the 'join' command.

---

### Post by kidders on 2007-01-10
> **Seine said:**
> And when you get to the other end you use the 'join' command.The "split" and "join" commands are **_unrelated_**. Don't use "join" in conjunction with "split" (unless of course you know what "join" is really for, I suppose.)

---

### Post by az on 2007-01-10
> **Kimm said:**
> Does anyone know how I can split archives (preferably ZIP or RAR, but pretty much anything will do)?

I need to be able to unpack them in WinZIP on a windows computer later on...

Can't fileroller do that alread?


Anyway, zipsplit is part of the zip package:

zipsplit [-hiLpst] [-n size] [-b path] zipfile

---

### Post by Seine on 2007-01-10
> **kidders said:**
> The "split" and "join" commands are **_unrelated_**. Don't use "join" in conjunction with "split" (unless of course you know what "join" is really for, I suppose.)

My apologies! I'm just a newbie too. :)

I've used split before and I thought I had used join to merge the file back together again. Perhaps I'm mistaken.

---

### Post by kidders on 2007-01-10
> **Seine said:**
> I've used split before and I thought I had used join to merge the file back together again. Perhaps I'm mistaken.You may have done something like **cat chunk* > whole** maybe.

---

### Post by spockrock on 2007-01-10
I really like 7zip, you can install with 'sudo apt-get install p7zip'

and to use and create then use this...
7z a -v10M <name of archive> <files to add>

that creates 10MB archives, so for 5Kb archives use -v5K switch....

---

### Post by Seine on 2007-01-11
> **kidders said:**
> You may have done something like **cat chunk* > whole** maybe.

Yes you're right. I used file redirection after reading a hint like that on these forums.

I just took a look at the man page for join and yes, its markedly different. Thanks. :-#

---

### Post by junkam on 2007-11-16
You can simply use RAR with the -v switch. Simply type
```
rar a -v100000k archive_name *.*
```

where the number after the -v switch is the size of each volume

---

