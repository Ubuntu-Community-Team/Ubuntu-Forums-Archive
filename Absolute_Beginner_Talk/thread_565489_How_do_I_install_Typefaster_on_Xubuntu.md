---
title: "How do I install Typefaster on Xubuntu"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by niceguy123 on 2007-10-02
The download seems to be for window although the doc says that it runs on linux [https://sourceforge.net/projects/typefaster/](https://sourceforge.net/projects/typefaster/)

How do I install on Xubuntu?

Thanks,

---

### Post by hyper_ch on 2007-10-02
You'll have to get the source code:

[http://downloads.sourceforge.net/typefaster/TypeFaster-v0.4.1-source.zip?modtime=1111599742&big_mirror=0](http://downloads.sourceforge.net/typefaster/TypeFaster-v0.4.1-source.zip?modtime=1111599742&big_mirror=0)

and compile it yourself.

Basically for compiling you'll need the build-essential package:

```

sudo apt-get install build-essential

```

Then you need to unzip that package and go into the folder and then run those commands:
```

./configure

```
```

make

```
```

sudo make install

```

But once you downloaded the zip file and unzipped it, there should be some closer install instructions.

---

### Post by niceguy123 on 2007-10-02
I unzipped before I ran sudo apt-get install build-essential, and then I went into the folder that I unzipped to and ran ./configure and got "no No such folder or directory message.

What now?

---

