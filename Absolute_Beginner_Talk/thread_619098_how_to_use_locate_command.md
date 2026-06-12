---
title: "how to use locate command ?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-11-21
how to locate files ina directory by using locate command.
i searched "info locate" command  
it is show like 
       (-d <path>
              --database=<path> Specfies the path of databases to search in)
so i tried like this...
locate -d /home/username/somewhere file_name

but this search the whole system....


any one know that 
how to locate files inside a directory (& subdirectory) by using locate command.

---

### Post by jordanmthomas on 2007-11-21
The -d switch is for choosing a database, not a directory to search in.

Perhaps you should try FINDing another command.
```
find /home/username/somewhere -name file_name
```

This can probably be done using locate, but find is a much better tool for what you're wanting to do.

---

### Post by daimaru on 2007-11-21
first you have to build database:

```
sudo locate -u
```
after that is done use locate filename
for example
```
locate kismet.conf
```

---

### Post by delphiguy on 2007-11-21
like daimaru said do
sudo slocate -u

to update system
and then you can
locate <file>


hope this helps.

---

### Post by jordanmthomas on 2007-11-21
But this does not search in a certain directory.  It searches ALL directories.

---

### Post by 5-HT on 2007-11-21
> **mokkai said:**
> 
any one know that 
how to locate files inside a directory (& subdirectory) by using locate command.
```

locate Pattern | grep ^/some/base/starting/directory
```

will search for pattern only in the indicated directory and all subdirectories.
cheers,

---

### Post by mokkai on 2007-11-21
thank you all

---

### Post by whazooo on 2007-11-21
> **daimaru said:**
> first you have to build database:

```
sudo locate -u
```
after that is done use locate filename
for example
```
locate kismet.conf
```

Great! I didnt know that switch existed
I always used updatedb

Thanks for this

---

