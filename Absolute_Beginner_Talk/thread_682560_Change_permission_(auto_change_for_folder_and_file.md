---
title: "Change permission (auto change for folder and files)"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by inertz on 2008-01-30
Hi,

How can i set permission so folder will be 777 and file inside it will be 644

I have try to set eg : chmod -R 755 folder
Then i try to set chmod -R 644 *.* so all file inside folder will become 644 permission.
inside folder have some folder let say folder2

My problem is only file inside folder was change, not file inside folder2

Can someone help me? can it be done via bash script?

Thanks.

---

### Post by hyper_ch on 2008-01-30
> **inertz said:**
> Hi,

How can i set permission so folder will be 777 and file inside it will be 644

I have try to set eg : chmod -R 755 folder
Then i try to set chmod -R 644 *.* so all file inside folder will become 644 permission.
inside folder have some folder let say folder2

My problem is only file inside folder was change, not file inside folder2

Can someone help me? can it be done via bash script?

Thanks.

I don't quite understand where the problem is but there are a few things to mention:

1.
```

chmod -R 755 folder

```
That command also chmods the files to 755 and instead of 755 I'd use 0755. If you just want to chmod the folder run this:
```

chmod 0755 /path/to/folder

```


2.
```

chmod -R 644 *.*

```
That should be working however I'd also use 0644 AND with that command you only chmod files/folder that have a period "." in their filen/foldername.
Better to use:
```

chmod -R 0644 /path/to/folder/*

```

And of course you can put that in a bash script:

```

#!/bin/bash
PATH=/path/to/folder
chmod 0755 $PATH
chmod 0644 $PATH/*
echo "Done"

```

---

### Post by inertz on 2008-02-05
Hi,

It was not solve the issue.

The scenario is like this.

I have 3 folder, with 3 file.

folder1>file1>folder2
inside folder2>file2>folder3
inside folder3>file3

When i run as you suggest to me it change
folder to 0755-correct
folder2 to 0644-wrong
file2 to 0644-correct
folder3 to 0000-wrong
file3 to 0000-wrong

I want folder 755 and file 644. Can it be done?

---

### Post by inertz on 2008-02-06
Still not ok

---

