---
title: "Synaptic broke, tried to fix, need help"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2007-01-15
Used a custom list & broke synaptic, reverted to original[backed up] & keep getting this error:

E: Dynamic MMap ran out of room
E: Error occurred while processing snowflake (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.de.debian.org_debian_dists_unstable_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

I'm at a loss as to what to do, neither apt-get or aptitude works either.  I don't know what Dynamic MMap, snowflake, or MergeList is, can someone please help with some info?

Thanks for any info

---

### Post by teaker1s on 2007-01-15
[http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106]("http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106")

---

### Post by randiroo76073 on 2007-01-15
Thanks teaker1s, I'll start trying out the article suggestions & post back if sucessful or not :)

---

### Post by randiroo76073 on 2007-01-16
Well, that didn't help, still getting the same message.  Anyone else have any advise/info?
TIAFAI

---

### Post by Sef on 2007-01-16
1) Could you post your sources list here.

From the Terminal (Applications > Accessories > Terminal):

cat /etc/apt/sources.list


2) Try commenting out the /var/lib/apt/lists/ftp.de.debian.org_debian_dists_unstable_main_binar y-i386_Packages list.  To comment out, but a # before the ftp.

---

### Post by randiroo76073 on 2007-01-17
Ok, I've got everything cleared up but 1, here I keep running into a stone wall
E: Dynamic MMap ran out of room
Any info on ths would be greatly appreciated :)

---

### Post by sethwoodworth on 2007-03-04
This will fix the mmap cashe problems, it doubles the cashe amount.  I had the *exact* problem but it mentioned an xfce patch instead.

sudo apt-get update -o APT::Cache-Limit=25165824

---

