---
title: "Extracting archive"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by VoXoM on 2008-03-03
How do I extract a tar.gz file to a certain folder using terminal?

Thanks.

---

### Post by Duck2006 on 2008-03-03
Double click on the filet and then extract to where you want it.

---

### Post by Cypher on 2008-03-03
The easiest way
```

mkdir <new directory>
cd <new directory>
tar -zxf /path/to/file.tar.gz

```

You can also do 
```

tar -ztvf /path/to/file.tar.gz | less

```
to see what directory structure the archive contains. Hit 'q' to exit from the file listing.

---

### Post by VoXoM on 2008-03-03
> **Duck2006 said:**
> Double click on the filet and then extract to where you want it.

Yes, but what is the command like if I absolutely need to use terminal..?

---

### Post by it.henrik on 2008-03-03
> **VoXoM said:**
> How do I extract a tar.gz file to a certain folder using terminal?

Thanks.

```
tar --help
``` gives you a quick help on the command line options

From the output of 
```
tar --help
```
---------------------------
```
 tar -xf archive.tar   # Extract all files from archive.tar.
```
---------------------------

--help works on almost all commands
otherwise you can get more detailed help in
```
 man tar
```

---

### Post by Duck2006 on 2008-03-03
> **VoXoM said:**
> Yes, but what is the command like if I absolutely need to use terminal..?


Cypher post has given you that.

---

