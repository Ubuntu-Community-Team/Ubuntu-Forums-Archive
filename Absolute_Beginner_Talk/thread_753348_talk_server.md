---
title: "talk server"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by kapt_leo on 2008-04-12
Hi,

I am trying to install talk server but i am not able to on gutsy gibbon.
i tried sudo apt-get install talk talkd xinetd but after installation i restarted xinetd but it keeps on saying talk daemon not running..

can some pls help me.

---

### Post by hyper_ch on 2008-04-12
I guess:
```

sudo /etc/init.d/talkd start

```

or

```

sudo /etc/init.d/talk start

```

should start it.

---

### Post by kapt_leo on 2008-04-12
sudo apt-get install talk talkd xinetd

abc@jaus:~$ sudo /etc/init.d/talk start
sudo: /etc/init.d/talk: command not found

abc@jaus:~$ sudo /etc/init.d/talkd start
sudo: /etc/init.d/talkd: command not found

---

### Post by hyper_ch on 2008-04-12
then I don't know... that would be the way to normally start/stop/restart daemons...

---

### Post by 655 on 2008-06-10
Has anyone gotten this working in a current version of Ubuntu?  A mere install does not suffice...

---

