---
title: "Need help Compiling the file &quot;John The Ripper&quot;"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2008-02-27
so i get close to compiling, but it turns out something ilke this

```
cd /home/linuxx/Desktop/John/$ make
```

Then it says something im missing a package or something any ideaS?

---

### Post by Crafty Kisses on 2008-02-27
> **LiNuXxToOthEMaX said:**
> so i get close to compiling, but it turns out something ilke this

```
cd /home/linuxx/Desktop/John/$ make
```

Then it says something im missing a package or something any ideaS?

You probably need build-essentials.
```
sudo apt-get install build-essentials
```
Then try to compile it again.

---

### Post by LiNuXxToOthEMaX on 2008-02-27
ok i tried that, and i got it, but this is how it goes now when im compiling

```
cd /home/linuxx/Desktop/John/makefile
```
it says something about makeinstall.file or something? anyideas on how to compile

---

### Post by Crafty Kisses on 2008-02-27
Luckily I've compiled this file before, I think.

It would go a little something like this.
```
cd /home/linuxx/Desktop/John
cd /home/linuxx/Desktop/John$
cd /home/linuxx/Desktop/John$ make

```

Then after that, your making the file, it will ask you for the following file to compile.
```
make -f.linux
```
You go through the same steps as above, for this, then, after you have done all that, do the following:
```
cd /home/linuxx/Desktop/John$ makeinstall
```
After that, you should be good, then you can download the package.

Hope this helps. :)

---

### Post by LiNuXxToOthEMaX on 2008-02-27
> **Codename said:**
> Luckily I've compiled this file before, I think.

It would go a little something like this.
```
cd /home/linuxx/Desktop/John
cd /home/linuxx/Desktop/John$
cd /home/linuxx/Desktop/John$ make

```

Then after that, your making the file, it will ask you for the following file to compile.
```
make -f.linux
```
You go through the same steps as above, for this, then, after you have done all that, do the following:
```
cd /home/linuxx/Desktop/John$ makeinstall
```
After that, you should be good, then you can download the package.

Hope this helps. :)

tanks it worked

only thing was it was

```
make -f makefile.linux
```
whatever tho, thanks 4 helping me man!! i appreciate it

---

### Post by Crafty Kisses on 2008-02-27
Yeah, I figured it was that, I wasn't sure. 

So yeah, next time I guess it would be:
```
make -f makefile.linux
```

Mark the thread solved, John the Ripper, is one of the easiest files to Compile.

---

