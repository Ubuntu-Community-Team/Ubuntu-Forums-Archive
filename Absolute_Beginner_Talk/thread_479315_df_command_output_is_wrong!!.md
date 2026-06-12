---
title: "df command output is wrong!!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-06-20
When I issue ....
    df  -h

... I get an output where my root partition name is wrong.  In other words, df states that /dev/sdb3 is mouted on / but, I really have /dev/sda6 mounted as /

I read that there are some UUID issues with df.  Is there a fix for this misreport?

Thanks

Carl

---

### Post by Cypher on 2007-06-20
What does "mount" report?

---

### Post by cwmoser on 2007-06-20
mount reports that /dev/sda6 is mounted on /  ....

$  mount

/dev/sda6  on  /  type ext3  (rw,errors=remount-ro)


Carl

---

