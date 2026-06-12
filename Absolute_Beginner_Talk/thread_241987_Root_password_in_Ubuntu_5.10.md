---
title: "Root password in Ubuntu 5.10?"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by borzoi on 2006-08-23
Hello everybody,
during installation of Ubuntu 5.10 (desktop), I wasn't asked for root password. I repeated installation three-four times, so I'm reasonably sure: it asked me just for non-privileged user password.
Of course, I'm now in distress any time I'm required to do a su or sudo.
Is there a default root password in 5.10?

---

### Post by deadgobby on 2006-08-23
Open up the terminal and type in   

sudo passwd root

[http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password](http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password)

 This will change the root pw.

Gobby

---

### Post by mcduck on 2006-08-23
Ubuntu is configured to use sudo instead of root account. Sudo uses your *users* password, and only the first user (created while installing Ubuntu) is able to use sudo by default. So no root password is needed.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

btw, is there any reason why you are using old 5.10 instead of the latest 6.06 version? You might find 6.06 noticeably faster and more finished..

---

