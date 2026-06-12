---
title: "LAMP Server on Desktop version"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Mike VandeBerg on 2006-10-02
I have just downloaded Ubuntu desktop version 6, I was wondering if you can still install the LAMP Server components and make them work.. I see that Apache, MySql and PHP are part of the available components in the software download screen, but will they all work on the desktop version, or do I have to download the server version to make them work?

Thanks in advance for any replies..

Mike

---

### Post by divague on 2006-10-02
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Mike VandeBerg on 2006-10-02
Thanks for the reply, but that link talks about the server cd, or "any method". Im still confused on whether the lamp components will install and work on the "Desktop version" that I downloaded...

Thanks,
Mike

---

### Post by rossio on 2006-10-02
I'm 99% certain that the 'server version' is simply a less graphical packaging of the same stuff, along with a more server-oriented set of software. No sense having lots of graphical widgets if the only use is going to be as a server. That being said, I don't see any reason why a LAMP installation wouldn't work on the Desktop version. The instructions on [the given webpage]("https://help.ubuntu.com/community/ApacheMySQLPHP") will work - click on that [Any Method]("https://help.ubuntu.com/community/InstallingSoftware") link you mentioned, and choose your favourite method in order to install the packages it mentions:  
```
apache2 php5-mysql libapache2-mod-php5 mysql-server
```

Worst case scenario: you try it and it doesn't work, so you use *sudo apt-get remove ...* for whichever LAMP components you installed.  :)

---

### Post by Mike VandeBerg on 2006-10-02
Hey thanks for the replies good people.... This forum rocks, and I think Ubuntu is gonna rock too.......


Thanks again,
Mike

---

