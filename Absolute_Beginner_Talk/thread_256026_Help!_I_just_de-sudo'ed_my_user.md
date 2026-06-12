---
title: "Help! I just de-sudo'ed my user"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by evolvedlight on 2006-09-12
While following the tutorial at: [http://www.howtoforge.com/debian_subversion_websvn](http://www.howtoforge.com/debian_subversion_websvn), I did the following commands:
```

# apt-get update
# apt-get install subversion
# apt-get install libapache2-svn

# mkdir /var/svn-repos/
# svnadmin create /var/svn-repos/openrevision

# groupadd subversion
# usermod -Gsubversion evo <- evo is my username

# chown -R www-data:subversion /var/svn-repos/*
evo is not in the sudoers file.  This incident will be reported.
```

I cannot get into the users control any more?

Do I have any other options apart from re-installing ubuntu?

Steve

---

### Post by az on 2006-09-12
Boot into recovery mode and restore your user's permissions and groups.
In recovery mode, you are root.

---

### Post by evolvedlight on 2006-09-12
Thanks. I just found [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

Should have actually read that sticky called "READ ME FIRST"

](*,) 

S

---

