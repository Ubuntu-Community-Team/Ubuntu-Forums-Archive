---
title: "cp Command Question"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by chuggaboo on 2007-12-29
Hi there! I have a question about the cp command.

Is there a way to use the -i option and automatically answer 'no'? (automatically NOT overwrite files that already exist)

It seems like it should be obvious, but I can't seem to find it anywhere. :D

---

### Post by eolson on 2007-12-29
maybe cp -b

Which would be backup up any file that would otherwise be over ridden?

---

### Post by scorp123 on 2007-12-29
> **chuggaboo said:**
>  (automatically NOT overwrite files that already exist) Taken from the manual page: 
```
-u, --update
              copy only when the SOURCE file is newer than the destination file 
or when the destination file is missing
``` Maybe this is what you are looking for?

---

### Post by chuggaboo on 2007-12-29
> **scorp123 said:**
> Taken from the manual page: 
```
-u, --update
              copy only when the SOURCE file is newer than the destination file 
or when the destination file is missing
``` Maybe this is what you are looking for?

I don't want it to overwrite even if it is newer. If it exists, I want it to be left alone. :)

cp -b doesn't seem like what I want, either. I'm not entirely sure, though. I don't know how it works.

---

### Post by scorp123 on 2007-12-29
> **chuggaboo said:**
> I don't want it to overwrite even if it is newer. If it exists, I want it to be left alone. :) Sounds like you could be interested in the **rsync** command. "rsync" offers e.g. these options (taken from the manual): ```
--ignore-existing       skip updating files that exist on receiver 
```

Also, there is another nice tool you could be interested in: **unison** ... It's available via "Synaptic".  There is a nice "unison" tutorial: 
[http://www.stanford.edu/~pgbovine/unison_guide.htm](http://www.stanford.edu/~pgbovine/unison_guide.htm)

---

### Post by R15I23D05D14Y on 2007-12-29
If you are set on using cp, you could also use the **yes** program and a pipe, eg:

```
yes n | cp -i source destination
```

---

### Post by scorp123 on 2007-12-29
> **R15I23D05D14Y said:**
>  ```
yes n | cp -i source destination
``` Nice :)

---

### Post by chuggaboo on 2007-12-29
Thank you both so much! Both of your suggestions seem to be exactly what I'm looking for! You both get 1000 points! :D

---

