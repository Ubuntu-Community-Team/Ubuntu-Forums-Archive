---
title: "FTP permissions based on user"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by JohnnyAvocado on 2007-01-29
I have an ftp directory tree that looks like this...

user1 --- full access to user1 folder (but only user1 folder)
user2 --- full access to user2 folder (but only user2 folder)
user3 --- full access to user1 folder (but only user3 folder)

Then there is user 4 who needs to have full read/write access to all 3 folders (but only these 3 folders and not additional folders that come along - i.e. user4, user5, user6, etc.)

(All the users already belong to a common group as I chrooted them based on group.)

In IIS it used to be you just gave user4 permission to each folder he would need access to. What is the equivilant in Ubuntu?

Thanks so much.

---

### Post by dannyboy79 on 2007-01-29
we need to know what ftp server you're using.

---

### Post by JohnnyAvocado on 2007-01-29
Sorry, I am using proftpd.

Thanks.

---

### Post by dannyboy79 on 2007-01-29
it should tell you in here: [http://www.ubuntuforums.org/showthread.php?t=51611&page=15&highlight=proftps](http://www.ubuntuforums.org/showthread.php?t=51611&page=15&highlight=proftps)

or ask Frodon with a PM. he is pretty smart with Proftpd. tell him I said Hi and hope he is doing well.

---

### Post by JohnnyAvocado on 2007-01-29
Thanks much. I will read up.

---

### Post by JohnnyAvocado on 2007-01-30
Just wanted to provide a follow-up. I later realized that this was not an FTP specific question. I finally got it straighted out just nicely but wanted to make sure I posted the solution incase anyone found themselves in the same situation. I actually started a new post on it, and [here]("http://ubuntuforums.org/showthread.php?p=2083083#post2083083") is the link should anyone need it.

---

