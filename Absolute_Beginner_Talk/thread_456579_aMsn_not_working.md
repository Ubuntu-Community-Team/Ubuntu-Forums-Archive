---
title: "aMsn not working"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by TigerTail on 2007-05-27
I try to use aMSN but it wont let me a popup comes and says i need TLS but it wont let me click on any of them I am running Ubuntu Feisty any help i just need to know how to get TLS thanx.

---

### Post by TigerTail on 2007-05-27
nevermind everyone i found it in another forum

---

### Post by DAFORZE on 2007-05-29
Could you post the link to the solution to the people (like me) who are still stuck on the same problem?
Thanx very much!

---

### Post by ironfistchamp on 2007-05-31
From another forum I got this

```

wget http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz
tar xvzf tls-1.5.0-linux-x86.tar.gz
sudo cp -f ~/tls1.50/* /usr/lib/tls1.50/

```

That did the job for me


Original Link:  [http://www.getautomatix.com/forum/lofiversion/index.php/t1182.html](http://www.getautomatix.com/forum/lofiversion/index.php/t1182.html)

HTH

Ironfistchamp

---

### Post by Pekay on 2007-06-01
Wow thanks for that ironfistchamp, got it all working now =D.

---

### Post by ironfistchamp on 2007-06-02
No probs glad it worked for you.

---

