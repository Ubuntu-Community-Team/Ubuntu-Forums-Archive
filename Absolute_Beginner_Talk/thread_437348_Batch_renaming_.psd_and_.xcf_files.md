---
title: "Batch renaming .psd and .xcf files"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-05-08
1) What I have are hundreds of .psd and .xcf files in close to 100 over sub-directories for some software project.

2) The current filenames are as follows:

140_1.xcf, 140_1.psd, 140_2., xcf, 140_2.xcf, etc. 

3) And I need to rename all of them to C001-1_1.xcf, C001-1_.psd, C001-2.xcf, C001-1_2.psd and so on. Like 140_1.xcf to C001-1_1.xcf, 140_1.psd to C001-1_1.psd and so on.  

What this means is that, I need to preserve "-1.xcf", "-1.psd", "-2.xcf", "-2.psd"

4) Oops, I forgot to mention that I also have tons of .jpg, .pcx, etc. image files and I don't want to rename them either. 

5) Now, I'd love to run Irfanview and see if it can do this but I don't have WinXP right and Wine doesn't seem to run Irfanview correctly for me. Okay, I've tried using F-spot but it can't load .xcf files, I think(not sure about .psd files) and KRename didn't seem to do it right?

Any chance of some software which will do this for me? I'd prefer to not use CLI for this task unless I can use a script or something. There are hundreds of files and typing in lines after lines of coding is going to mess up my concentration and I could screw up too many files.

---

### Post by mills on 2007-05-08
not sure if this is what your looking for but i saw it today while trying to educate myself a little

```
Rename a bunch of file extensions
e.g. change *.txt into *.htm
  for f in *.txt; do mv ./"$f" "${f%txt}htm"; done
```

so i think 

```
for f in *.psd; do mv ./"$f" "${f%psd}xcf"; done
```

should be what your after

got the info from here, iam no expert so best double check

[http://webtools.live2support.com/linux/mv.php](http://webtools.live2support.com/linux/mv.php)

---

### Post by Lucifiel on 2007-05-09
Ahh thank you but I'm not trying to rename file extensions at all. 

But still, I'll note these commands down somewhere for use in the future. ;)

---

### Post by cryogenic on 2007-05-09
have you tried gwenrename? It's available in the repos. Admittedly I've never used it but it's worth a look, I guess.

---

### Post by Lucifiel on 2007-05-09
> **cryogenic said:**
> have you tried gwenrename? It's available in the repos. Admittedly I've never used it but it's worth a look, I guess.

Thank you. I'm looking at the site of gwenrename now. Hmmm... there doesn't seem to be any way to exclude the other files with different file extensions like .xcf and so on.

---

### Post by Lucifiel on 2007-05-09
Just updated first post with some information I'd left out by mistake. :p 

Oh and I'm downloading Picasa now. I wonder if that'll work.

---

