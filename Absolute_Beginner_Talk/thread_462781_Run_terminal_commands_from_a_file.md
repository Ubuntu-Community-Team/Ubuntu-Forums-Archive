---
title: "Run terminal commands from a file?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Mr Steve Gnarly on 2007-06-03
Just one simple question really..

Is there any way I can save terminal commands to a file and then run the file through the terminal so these commands would all get exicuted one after the othere?

---

### Post by hyper_ch on 2007-06-03
Yes there is....

use as file extension ".sh" (for shell file) --> just makes it easier to remember

then use as first line this:
```

#!/bin/bash

```

and then you can start with your terminal commands, e.g.

```

#!/bin/bash

################ RESTORE SOURCES.LIST ###############

cp -f backup_files/sources.list /etc/apt/sources.list
cp -f backup_files/secring.gpg /etc/apt/secring.gpg
cp -f backup_files/trustdb.gpg /etc/apt/trustdb.gpg
cp -f backup_files/trusted.gpg /etc/apt/trusted.gpg

#####################################################

# Add Medibuntu
# wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
# wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

aptitude -y remove mozilla-thunderbird

aptitude update
aptitude -y upgrade

# Skype
aptitude -y install skype

# Java
aptitude -y install sun-java6-jre sun-java5-jre

....
....
....
....
....

```

You can then run that script from shell by issuing this in the folder:
```

sh file.sh

```
or if you need it to execute as sudo:
```

sudo sh file.sh

```

Of course you could also make single commands within the script to execute as sudo... just put the sudo in the first line :)

---

### Post by Mr Steve Gnarly on 2007-06-03
Thats great, 

thanks for that it will save me hours of copy and pasting :)

---

### Post by dev3 on 2007-10-29
I want to do the same thing, but Not via the terminal, but via an Icon on the screen. Let me explain: 
I want to make an Icon on the desktop, which when double clicked, will run some code in the terminal, and then close the terminal. 
How do I do it??

---

