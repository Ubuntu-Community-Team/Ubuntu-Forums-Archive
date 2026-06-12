---
title: "ln -sf bash /bin/sh bricked my system :'("
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by mahy on 2006-12-04
i tried (in vain) installing up-to-date ati fglrx drivers according to [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide). One of commands i entered was "sudo ln -sf bash /bin/sh". I'm not 100% sure what it does, but now whenever i log into a terminal a warning message about not having permissions to /etc/profile is displayed, and graphical login (any other than failsafe xterm) fails altogether with the same reason. I hope someone can help me fix this quite soon... TIA

Mahy

---

### Post by taurus on 2006-12-04
It means that you just linked /bin/sh to /bin/bash!  However, on system running Edgy, /bin/sh is linked to /bin/dash...  So, you need to reverse the order again!

```

cd /bin
sudo rm  sh
sudo ln  -s  dash  sh

```

---

### Post by bodhi.zazen on 2006-12-04
> **mahy said:**
> i tried (in vain) installing up-to-date ati fglrx drivers according to [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide). One of commands i entered was "sudo ln -sf bash /bin/sh". I'm not 100% sure what it does, but now whenever i log into a terminal a warning message about not having permissions to /etc/profile is displayed, and graphical login (any other than failsafe xterm) fails altogether with the same reason. I hope someone can help me fix this quite soon... TIA

Mahy

LOL :lol: Nice one !

ln -s is a shortcut if you will. Your system is linking bash (the default bash shell) to sh (c-shell).

Try booting to the live CD and removing the link.

sudo rm bash

---

### Post by keeb on 2006-12-04
Isn't unlink safer than rm?

---

### Post by mahy on 2006-12-04
yeah, i know ln is about linking and symlinking files and folder, but this is beyond my skills to repair. I only passed the Unix course at college with the worst pass grade possible :)

---

### Post by idlewild on 2006-12-04
> **bodhi.zazen said:**
> 
Try booting to the live CD and removing the link.

sudo rm bash

Not a good idea!

To reverse the changes the command will be:
ln -sf dash /bin/sh

---

### Post by mahy on 2006-12-04
> **taurus said:**
> It means that you just linked /bin/sh to /bin/bash!  However, on system running Edgy, /bin/sh is linked to /bin/dash...  So, you need to reverse the order again!

```

cd /bin
sudo rm  sh
sudo ln  -s  dash  sh

```

doesn't help... no change at all :(

---

### Post by taurus on 2006-12-04
You need to copy /bin/bash from the LiveCD back to your harddrive since you already deleted when you link it to /bin/sh.

---

### Post by mahy on 2006-12-04
nah, i ran chmod +rx /etc/profile. That did the trick. I'll put a big sign reading "If it's not broken, don't fix it!" above my bed...](*,)

---

### Post by po0f on 2006-12-04
mahy,

This may come back to haunt you later on.  We can help you fix it, if you post the output of the following commands:
```
[FONT="Courier New"]$ ls -l /bin/sh
$ ls -l /bin/bash
$ ls -l /bin.dash[/FONT]
```

---

