---
title: "postgresql removal and other problems"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by rshel on 2006-09-14
Hello,

I recently decided to give Glom a try but have had a lot of problems with Postgresql-8.1.  I could never connect to Postgresql-8.1, only 7.4, which had previously been installed, I suspect with another database frontend I was trying.  I couldn't get rid of gforge or 7.4, until I followed the advice in this thread: 

[http://www.ubuntuforums.org/showthread.php?t=246944&highlight=postgresql]("http://www.ubuntuforums.org/showthread.php?t=246944&highlight=postgresql")

8.1 install went fine then, but I kept getting this message:

```
createuser: could not connect to database template1: could not connect to server: No such file or directory
Is the server running locally and accepting
connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
```

Now, when I try to remove 8.1 I get this message:

```
E: postgresql-8.1: subprocess pre-removal script returned error exit status 1
```

I'm hesitant to try to use the procedure outlined in the link above to try to fix the problem, since I don't know if it would work with 8.1.  But I will if that's the only solution.  Is there anyway to remove 8.1 and reinstall it to solve problem #1 above, short of doing a reinstall of ubuntu?

Thanks in advance.

---

