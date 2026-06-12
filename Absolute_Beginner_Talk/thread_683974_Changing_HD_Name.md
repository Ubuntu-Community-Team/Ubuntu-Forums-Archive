---
title: "Changing HD Name"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Fizzzy on 2008-01-31
I have a small dilemma here, but i'm hoping theres a simple fix I can do without formating one of my HD's.
Here's my problem
I have 2 External HD's, both the same type, but one is bigger than the other.
They both have the same Drive Name, from when I had them used on XP.
What happens, is when I turn on my computer, they turn on automatically, and whichever one is turned on first is named "HDNAME" and the second is named "HDNAME (2)"
This causes a problem with some of my applications, I was wondering if there is a way I can rename the drive, whenever I try it via Places>Computer, it says that it could not be renamed, even when it is unmounted.
I just need a way to rename one of the drives, so they will not have problem with names.

Thanks for a reply in advance :)

---

### Post by logos34 on 2008-01-31
Use [tune2fs]("http://www.linux.com/base/ldp/howto/Partition/labels.html").

e.g.

sudo tune2fs -L <new_name> /dev/sdc1  

check how they're designated

sudo fdisk -l

---

### Post by Fizzzy on 2008-01-31
I tried it, heres what I got:
```
tune2fs: Bad magic number in super-block while trying to open /dev/sdc1
Couldn't find valid filesystem superblock.
```
Should of I unmounted it first, or am I doing something else wrong? :|

---

### Post by shad0w_walker on 2008-01-31
Judging by the fact you used them on Windows you aren't going to be using anything other than NTFS or maybe FAT.

[http://man.linux-ntfs.org/ntfslabel.8.html](http://man.linux-ntfs.org/ntfslabel.8.html)

Assuming you are using NTFS then the tool ntfslabel should do the trick. It works basically the same way that the last command does except different tool doing the work.

```

sudo ntfslabel /dev/sdc1 <new_name> 

```

Make sure you are using the right device name for the hard drive (Probably gonna be different from /dev/sdc1

---

### Post by Fizzzy on 2008-01-31
It goes back to the normal command after I do it, I tried mounting both of them (I did did the command to both of the Volumes) and it still had the same problem.
I'm sure it's the right Volume paths, and im sure I unmounted it.
I hope i'm not missing something obvious :(

---

### Post by logos34 on 2008-01-31
sorry, missed the XP part.

'sdc1' was just an example--check your drives with

sudo fdisk -l

post it.

---

### Post by bodhi.zazen on 2008-01-31
Changing the label depends on the file system.

See this link (scroll down to the end of the first post).

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

There is a section "How to Label"

You can determine the file system with ```
sudo fdisk -l
```

---

### Post by yabbadabbadont on 2008-01-31
> **bodhi.zazen said:**
> You can determine the file system with ```
sudo fdksi -l
```

Don't you mean ```
sudo fdisk -l
``` ;)

---

### Post by bodhi.zazen on 2008-01-31
LOL, yes indeed, fixed, typed too fast ...

---

### Post by yabbadabbadont on 2008-01-31
> **bodhi.zazen said:**
> LOL, yes indeed, fixed, typed too fast ...

Everyone has lexdyslic moments now and then.

---

### Post by Fizzzy on 2008-02-01
Thanks for your help, I finally got them renamed now :-)

---

### Post by logos34 on 2008-02-01
Mark as 'Solved'  (>thread tools)

---

### Post by bodhi.zazen on 2008-02-01
Or see this link : [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

