---
title: "[SOLVED] Older version of MySQL"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by briealeida on 2007-06-22
I'm using Ubuntu Server 6.06 LTS. I'm installing MySQL but I have version 5.0 something. I'm trying to use Cacti and it's not supported with MySQL 5 and I'd like to install an older version of MySQL so that I can use Cacti.

But I'm not sure how to go about doing that, installing an older version. What should I do?

---

### Post by briealeida on 2007-06-22
Maybe I can't roll back and should just uninstall and then install MySQL 4.1? But do I want MySQL or MySQL AB? I can't stand MySQL. This is so frustrating.

---

### Post by eluzi on 2007-06-22
U want mysql, and should for now uninstall mysql 5 and install it again, but it's possible to downgrade also....

# apt-get --purge remove program_name

You can download MySql 4.1 version somewhere and do:

# dpkg -i program_name

Guess it would do the trick...

---

### Post by briealeida on 2007-07-02
I found a virtual appliance that did everything I wanted.

Also, just as a note, MySQL 5 is NOT what I wanted. On that machine, I purged it and went through a bunch of attempts but invoking 'which mysql*' still had issues.

Thanks anyway.

---

