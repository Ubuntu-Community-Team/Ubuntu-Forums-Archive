---
title: "Multiple rar files with an extract-to folder"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Unknowndeepness on 2006-07-09
Hello there.
Ive got a little movie, splitted into a number of rar-files,
and they are all on a ntfs (read-only) disc.

I know i can open the file (first .rar file) with ark, and then extract to some folder.

But how can i do this with a commandline?

---

### Post by mogelhead on 2006-07-11
It sounds like you already have rar installed, so I skipp that part.

Try the following command:
```
rar x /path/to/file.part01.rar -w~ ~
```
x is for extract
-w assigns a working directory, in this case ~ (your home folder), I'm not shure you need this parameter, but since you said your files resided on a read only ntfs partition, I thought I better mention there exists such an option.
the last ~ is where the extracted files should go, your home folder again

I got this information from
```
man rar
```

---

### Post by Kobalt on 2006-07-11
Personnaly, I've install the rar package and I can extract multiple .rar files with File Roller... Perhaps you wanna install this on your Kubuntu (it seems you're using KDE : ark).

---

### Post by Unknowndeepness on 2006-07-18
> **mogelhead said:**
> It sounds like you already have rar installed, so I skipp that part.

Try the following command:
```
rar x /path/to/file.part01.rar -w~ ~
```
x is for extract
-w assigns a working directory, in this case ~ (your home folder), I'm not shure you need this parameter, but since you said your files resided on a read only ntfs partition, I thought I better mention there exists such an option.
the last ~ is where the extracted files should go, your home folder again

I got this information from
```
man rar
```

This worked just fine :) 
Thanx for your help :mrgreen:

---

