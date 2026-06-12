---
title: "Filenames"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Durden10 on 2007-10-15
Hi

Is there a possibility to create a file automatically via script named after the folder it is in? Lets say I have the file test.txt in the folder hello, which command could transform text.txt into hello.txt?
Thanks

---

### Post by hyper_ch on 2007-10-15
it is possible if you have some common factor.

E.g. if you have in every existing folder only one .txt file renaming it to the folders name is no big deal.

However if you have like hundreds of txt files and they don't have a common criteria over all your folders then it's going to be tough to actually select/filter the one you want to rename.

---

### Post by Durden10 on 2007-10-15
I only have one file which I need to rename....

---

### Post by Durden10 on 2007-10-17
Hi, due to lack of response, I'm posting my question again:

Is there a possibility to create a file automatically via script named after the folder it is in? Lets say I have the file test.txt in the folder hello, which command could transform text.txt into hello.txt?
Thanks

---

### Post by dwhitney67 on 2007-10-17
yes.

```
#!/bin/sh

if [ $# -ne 1 ]
then
    echo "Usage:  $0 [filename]"
    exit 0
fi

mv $1 `basename $PWD`.`echo $1 | cut -d . -f2`

```

Use this at your own risk.

---

