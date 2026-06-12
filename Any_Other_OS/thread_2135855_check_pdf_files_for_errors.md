---
title: "check pdf files for errors"
date: 2013-04-15
forum: Any Other OS
---

### Post by Si1414 on 2013-04-15
I have several pdf files and want to check whether they are downloaded properly or not. I want to check for any possible unfinished downloads. 
I am using the following code, however the following code only checks pdf files in your current folder and not the subfolders. 
How to check all pdf files inside current folder **and all its sub folders**?




```
for f in *.pdf; do
  if pdfinfo "$f" > /dev/null; then
    : Nothing
  else
    echo "$f" is broken
  fi
done

```
I am using Cygwin on Windows 7 (64 bit).


Thank you for your help.

---

