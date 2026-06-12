---
title: "understanding uncomment"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by dmichaels on 2006-09-21
i know this character # symbolizes uncomment. but what does uncomment mean and what does it do?

---

### Post by bodhi.zazen on 2006-09-21
Remove the # from the front of the line.

---

### Post by dmichaels on 2006-09-21
can u give a more elaborate answer? sorry but im having trouble understanding it all.

---

### Post by aysiu on 2006-09-21
This is what a **commented out** line looks like: ```
# deb http://archive.ubuntu.com/ubuntu main
``` This is what an **uncommented** line looks like: ```
deb http://archive.ubuntu.com/ubuntu main
``` The *#* sign in the front of a line basically says "ignore this line--pretend as if it doesn't exist."

So, for example, this shell script would make a backup of your home directory and then eject the backup drive afterwards: ```
#/bin/bash
rsync -av /home/username /media/drive
sudo eject /media/drive
``` This shell script would do *nothing*: ```
#/bin/bash
# rsync -av /home/username /media/drive
# sudo eject /media/drive
```

---

### Post by bodhi.zazen on 2006-09-21
What file are you talking about?

I DOS you add comments in a file like this:```
REM Comments
```

In Linux you do it like this```
# comments
```

In some configuration files authors will include options, but disable them with a comment. Like this:```
# Configuration file xyz

# Options - To enable these options, uncomment the option:
# Option 1
# Option 2
# Option 3
```

To enable option 2, uncomment:```
# Configuration file xyz

# Options - To enable these options, uncomment the option:
# Option 1
Option 2
# Option 3
```
Option 2 is enabled, option 1 & 3 are not.

---

