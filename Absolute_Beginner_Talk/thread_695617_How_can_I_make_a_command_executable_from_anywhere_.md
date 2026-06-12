---
title: "How can I make a command executable from anywhere (for only one user)?"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-13
I have my little script set up, "foo"

Right now I have to do..

"~/Desktop/folderX/foo"

how can I change it so I just type "foo" ?

---

### Post by sigge on 2008-02-13
You need to move the file to somewhere in your path environment. It also needs to be chmod'ed to executable.

sudo mv ~/Desktop/etc/foo /usr/local/bin/ (or wherever you want/need it...)
sudo chmod +x /usr/local/bin/foo (to make it executable.)
:guitar:

---

### Post by carverj on 2008-02-13
follow these instructions:
[http://ac12.wordpress.com/2007/04/18/ubuntu-environment-variables/](http://ac12.wordpress.com/2007/04/18/ubuntu-environment-variables/)

and add /Desktop/folderX/foo:

(I would personally just add it to my bash environment variable with a command that 
looks something like: - export PATH=$PATH:/Desktop/folderX/foo) 

Oh and to ensure that only one user can execute, yes it is sudo chmod +x {/filename}
if you wanted a particular user to own that file so that only they may execute it, 
use the chown command (eg, chown tom:tom {/filename})
ls -l

---

### Post by Cypher on 2008-02-13
The best way to keep this file local to your account is to create a "bin" directory in your home directory and place the file there, this directory will be automatically added to your path if it exists..so
```

cd ~
mkdir ~/bin
mv ~/Desktop/folderX/foo ~/bin/foo

```

---

