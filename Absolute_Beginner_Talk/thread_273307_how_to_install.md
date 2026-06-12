---
title: "how to install?"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-10-07
hello ive got an tar.gz packet that i would like to install its an program and how to extract it then install it under dapper drake?

---

### Post by PPAAUULL on 2006-10-07
Did you look in the reps for the program?

---

### Post by haxer on 2006-10-07
Hmm yes but i managed to make it work:)

---

### Post by onioneater36 on 2006-10-07
I would recommend listening to PPAAUULL and checking in the repositories to see if the program is there, but if you need to install the gzipped tarball, you do it with the following command...

tar -xvzf package.tar.gz

substituting the name of your package.

Enjoy

---

### Post by onioneater36 on 2006-10-07
You might need to put a "sudo" in front of the command line I gave you if it writes files into directories that your user account does not have write privelages to.

---

### Post by CatKiller on 2006-10-07
Glad you got this one working. For future reference: [How to intall ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

