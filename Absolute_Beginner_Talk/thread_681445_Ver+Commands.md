---
title: "Ver+Commands"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-29
Hello!
I wanna know my system version. For this in xp i could simply type ver in command. What should I do in ubuntu?
+++
How can I see the commands list. I'm interested in learning them!
+++
in windows cmd you can get information on a command by writing /? after that. Is there something same in linux?
Thanks.

---

### Post by brettg on 2008-01-29
To see your (kernel) version use;

uname -r

To get specific command help;

man <command> 

or (usually)

<command> --h

hth

---

### Post by bodhi.zazen on 2008-01-29
> **Hoom@n said:**
> Hello!
I wanna know my system version. For this in xp i could simply type ver in command. What should I do in ubuntu?

```
cat /etc/issue
```

> ++
How can I see the commands list. I'm interested in learning them!

```
help
```

See also :

	[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
	[http://doc.gwos.org/newdoc/doku.php/clibeginner](http://doc.gwos.org/newdoc/doku.php/clibeginner)
	[http://www.justlinux.com/nhf/Command_Reference](http://www.justlinux.com/nhf/Command_Reference)

[http://linuxcommand.org/](http://linuxcommand.org/)

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

> +++
in windows cmd you can get information on a command by writing /? after that. Is there something same in linux?
Thanks.

use man :

```
man man
```

or 

```
man <command>
```

---

### Post by Hoom@n on 2008-01-29
Thank you.

---

