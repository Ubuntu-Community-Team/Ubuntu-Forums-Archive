---
title: "Help Please"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by agonoruci on 2006-12-01
I do not understand how to install grz.tar or whatever files. I tried a command in Terminal sudo sh something. What is hte code, much thanks forhelp.

---

### Post by lumpki on 2006-12-01
You can just right-click on the archive (in your file manager) and click "extract here". Or, on the command line:
```
tar -xzvf filename.tar.gz
```

Type "man tar" for all the gory details.

---

### Post by Bachstelze on 2006-12-01
Hou might find [this](http://psychocats.net/ubuntu/installingsoftware) interesting.

---

### Post by Ben Sprinkle on 2006-12-01
> **lumpki said:**
> You can just right-click on the archive (in your file manager) and click "extract here". Or, on the command line:
```
tar -xzvf filename.tar.gz
```

Type "man tar" for all the gory details.

What's the "z" do? I always do -xvf.

---

### Post by Amit Yaron on 2006-12-01
> **Goat Spirit said:**
> What's the "z" do? I always do -xvf.

Z stands for "zipped".
Extract/Create a zipped (Tape) ARchive.

---

### Post by Ben Sprinkle on 2006-12-01
What? I don't understand, tape? The z has no use in my opinion. :confused:
```

sudo tar -cvf newtar.tar foldertobeused
sudo tar -xvf newtar.tar

```
c means create.
x means extract.

v means show output.
f means file.

---

### Post by Bachstelze on 2006-12-01
Actually, z is used to handle gzipped tarballs. Try to use it on a bzipped one and you will have a nice error ;)

---

### Post by Ben Sprinkle on 2006-12-01
Oh, but can't you just use gzip for that?

---

### Post by Bachstelze on 2006-12-01
Well, yeah, you could use gunzip to get a .tar and then extract it with tar -xvf but it's nicer to have it done in one command ;)

---

### Post by lumpki on 2006-12-01
> **Goat Spirit said:**
> What's the "z" do? I always do -xvf.

See the man page ;)

But you're right, tar can figure it out, you usually don't have to specify the compression scheme that was used to create the archive.

"The only case when you have to specify a decompression option while reading the archive is when reading from a pipe, or from a tape drive that does not support random access. However, in this case GNU tar will indicate which option you should use."
[http://www.gnu.org/software/tar/manual/html_node/gzip.html](http://www.gnu.org/software/tar/manual/html_node/gzip.html)

---

### Post by Ben Sprinkle on 2006-12-01
Well doing:
```

sudo tar -xvf file.gz

```
It un zips it fine, is this supposed to happen from a gzipped archive?
Can tar also handle bzipped? I hate that long *** command for unzipping bz2. ;)

---

### Post by Bachstelze on 2006-12-01
To extract a bzipped tarball :

```
tar xjvf *.tar.bz2
```

---

### Post by Ben Sprinkle on 2006-12-01
Rofl, that's funny. You can use tar for almost anything.

---

