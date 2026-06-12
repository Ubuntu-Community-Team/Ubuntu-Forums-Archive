---
title: "how to extract files ?"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-06
Iso ,bin , cue files - I need to extract
Not burn to cd....but extract like "unrar".

---

### Post by uzi09 on 2006-07-06
hmm, not too sure how exactly to extract it. i think the closest thing to that would be the program called foobar2000.

a link to it is available under the "Uses" section in this wiki page:
[http://en.wikipedia.org/wiki/Cue_sheet](http://en.wikipedia.org/wiki/Cue_sheet)

figured i'd give you the wiki since it provides a lot of info on how exactly it works as well as other uses for bin/cue files.

---

### Post by FredB on 2006-07-06
for iso files, you can mount them and see / extract their content.

In command line, type :

```

sudo mount *name-of-file.iso* -o loop *name of directory used as a target*
```

With iso named image.iso and a target directory named file-iso

sudo moint image.iso -o loop ~/file-iso.

And you can browse it using nautilus.

For nero .bin file, you can use bin2iso :

[http://users.andara.com/~doiron/bin2iso/]("http://users.andara.com/~doiron/bin2iso/")

And mount it.

Hope I helped a little ;)

---

### Post by MaximB on 2006-07-08
fredB - I've managed to exctract .iso files but the link you gave me to the .bin files program is broken
could you pose me a link to other program for .bin files ?
like "isobuster" in windows or somthing ?

---

### Post by FredB on 2006-07-08
Ouch :(

Here is a link for the source code file :

[http://mange.dynalias.org/linux/bin2iso/](http://mange.dynalias.org/linux/bin2iso/)

And also this page could help :

[http://wiki.linuxquestions.org/wiki/CD_Image_Conversion](http://wiki.linuxquestions.org/wiki/CD_Image_Conversion)

---

### Post by MaximB on 2006-07-09
ok .... I've downloaded the source code....what do I need to do with him now ?
have a no idea how to  use source files
tried the command on this page - but maybe I'm missing somthing

---

### Post by cantormath on 2006-07-25
Does anyone know how to extract a .img archive?  Isobuster is able to do it but im looking for a native solution.

---

### Post by taurus on 2006-07-25
> **cantormath said:**
> Does anyone know how to extract a .img archive?  Isobuster is able to do it but im looking for a native solution.
You would mount it the same way as you do for .iso...

```

sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop <filename>.img /mnt/iso

```

---

### Post by cantormath on 2006-08-01
> **taurus said:**
> You would mount it the same way as you do for .iso...

```

sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop <filename>.img /mnt/iso

```

Thanx, I will give that a try.  Its amazing that everyone I have asked says that they know it can be know, but they dont know how to do it.

---

