---
title: "New installation on lappy"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by stickysnail on 2007-08-22
Well I am proud to say that I have deleted Vista from my new laptop and have just Ubuntu running. Well I need some suggestions at what to get started with first. Commands are the first thing that I am really interested in. Also getting apache up and simulating a web server. If any of you can point me in the right direction or give some good tips I would much appreciate it.

---

### Post by Ek0nomik on 2007-08-22
Commands:

[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

[http://www.freesoftwaremagazine.com/articles/beginner_intro_cli_part_2](http://www.freesoftwaremagazine.com/articles/beginner_intro_cli_part_2)

[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

[http://www.justlinux.com/nhf/Command_Reference](http://www.justlinux.com/nhf/Command_Reference)

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

Apache:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

You can ignore all the other components if you wish to only have Apache.

I think a simple:

(Accessories/Terminal)

```
sudo apt-get install apache2
```

will do the trick.  Then you can change the files being served by Apache in /var/www/.  Try typing 'localhost', without the''s in Firefox after you install Apache.

---

### Post by Aishiko on 2007-08-22
I was under the impression that you were going for a dual boot set-up, what changed your mind?

---

### Post by Dr Small on 2007-08-22
> **Aishiko said:**
> I was under the impression that you were going for a dual boot set-up, what changed your mind?
He accidentially removed windows while installing Ubuntu :p

---

