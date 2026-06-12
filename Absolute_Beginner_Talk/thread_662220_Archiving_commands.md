---
title: "Archiving commands"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2008-01-08
Ok this may seem like a silly question but what are the commands for creating and decompressing:
[LIST]
[*]tar.bz2
[*]tar.gz
[*]tar
[*]gz
[*]bz2[/LIST]:rolleyes:

---

### Post by shareMenaPeace on 2008-01-08
I dont know :D
But with rightclick on an archive i can unpack it.
Maybe you need to enable ALL software sources todo so ...(administration - Sources here enable first and second tab all except source code.)


Cheers

---

### Post by yabbadabbadont on 2008-01-08
```
man tar
man gzip
man bzip2

```
:D

---

### Post by ryanVickers on 2008-01-08
> **shareMenaPeace said:**
> I dont know :D
But with rightclick on an archive i can unpack it.
Maybe you need to enable ALL software sources todo so ...(administration - Sources here enable first and second tab all except source code.)


Cheers

contrary to what this thread may lead you to believe, I know what I'm doing ;)
I just needed the terminal commands very specifically, not the graphical ones

---

### Post by ryanVickers on 2008-01-08
> **yabbadabbadont said:**
> ```
man tar
man gzip
man bzip2

```:D
there seems to be no entry for gz or bz2... but maybe tar will say it all...

EDIT: perhaps i should use "gzip and bzip2 then? ;) lol

---

### Post by shareMenaPeace on 2008-01-08
ok ok, its just im actualy try to sleep but something makes me spam beginenr forum with stupid links, hihi ....
:popcorn:

---

### Post by monte48lowes on 2008-01-08
tar.bz2  'tar xjf'
tar.gz     'tar xzf'
tar          'tar xf'
gz            'tar xzf'
bz2          'tar xjf'

Mike

---

### Post by ryanVickers on 2008-01-08
that's to make them is it? very well then, thanks! :D

or is it to extract them... :confused:...

lol either way, its useful! :D (I just have to know which it is ;))

---

### Post by PinkFloyd102489 on 2008-01-08
> **monte48lowes said:**
> tar.bz2  'tar xjf'
tar.gz     'tar xzf'
tar          'tar xf'
gz            'tar xzf'
bz2          'tar xjf'

Mike

Not exactly ;-)




To make them:

For a simple .tar:
```
tar cvf name.tar name
```

For a gzip tar:
```
tar cvzf name.tar.gz name
```

For a bz2 tar:
```
tar cvjf name.tar.bz2 name
```

For a gzip:
```
gzip file
```

For a bzip2:
```
bzip2 file
```


and to decompress those, do these:

For a simple tar:
```
tar xvf name.tar
```

For a gzip tar:
```
tar xvzf name.tar.gz
```

For a bz2 tar:
```
tar xvjf name.tar.bz2
```

For a gzip:
```
gunzip -d name.gz
```

For a bzip2:
```
bunzip2 -d name.bz2
```



That should do it.

---

### Post by ryanVickers on 2008-01-08
OK actually I have a new very specific request:

what would be the command for all the formats I listed to:

-create <archive a> from the files in <folder a> and put the archive at <folder b>

-uncompress <archive a> to <folder a>

EDIT: OK thanks that should do but if I have trouble I'll be back ;)

---

### Post by blueridgedog on 2008-01-08
> -create <archive a> from the files in <folder a> and put the archive at <folder b>

tar cvfz /path/to/archivea /path/to/foldera
or
cd /path/to/foldera
tar cvfz /path/to/archivea ./*

> -uncompress <archive a> to <folder a>

There are other ways to redirect tar output, but for safety, this is what I do:

cd /path/to/foldera
cp /path/to/archivea ./
tar xvfz archivea

---

### Post by ryanVickers on 2008-01-08
OK these last 2 posts should be all I need THANKS A LOT!! :D

---

### Post by PinkFloyd102489 on 2008-01-08
You can unpack a tar directly to a directory.

Example:

tar xvzf blah.tar.gz /home/me/packages/




Same goes for gunzip and bunzip2, just append the directory on the end of the command.

---

### Post by zipperback on 2008-01-08
From the command line type:    man tar

- zipperback
:popcorn:

---

### Post by blueridgedog on 2008-01-08
> **PinkFloyd102489 said:**
> You can unpack a tar directly to a directory.

Example:

tar xvzf blah.tar.gz /home/me/packages/




Same goes for gunzip and bunzip2, just append the directory on the end of the command.

Agree, but I have fat fingered that and just got in the habit of cd'ing to the desired location and moving the tarball to ./

---

