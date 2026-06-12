---
title: "Gparted 0.2.5 help"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by bellaterror on 2006-06-24
I downloaded it and tried to use apt-get but didn't work any help. (I DL'd it to the desktop)

---

### Post by raptros-v76 on 2006-06-24
apt-get downloads and installs.

```
 sudo apt-get install gparted 
```

---

### Post by bellaterror on 2006-06-24
eh lemme explain a bit more in depth ummm I already have 0.1 on here I just downloaded 0.2.5 and am trying to basically upgrade it. (tried that code twice now still unsuccessful)

---

### Post by johnc4510 on 2006-06-24
What you downloaded, was probably an iso file. This type of file is meant to be burned to a cd, not installed on your computer. Is iso in the name of the file?

---

### Post by lazyd2 on 2006-06-24
Check the dependencies [here]("http://packages.debian.org/testing/gnome/gparted")

---

### Post by bellaterror on 2006-06-24
I'm a n00b to linux not computers... =/ and no it's not an iso file there are various files including shell script files text files and desktop configuration files

---

### Post by raptros-v76 on 2006-06-24
do you have it as a debian package (.deb)? if so, then do sudo dpkg -i <debian package name>

---

### Post by bellaterror on 2006-06-24
Not a deb file either it's a document with many other files within it
@lazyd2 It said that Error: Dependency is not satisfiable: libc6  ?

---

### Post by bellaterror on 2006-06-24
the error occured when trying to DL the deb package version of this....

---

### Post by bellaterror on 2006-06-25
anyone have any answer to this error???

---

### Post by skale on 2006-06-25
do 
file ____________
and post the output.

---

### Post by bellaterror on 2006-06-25
again the error is 

Error: Dependency is not satisfiable: libc6

---

### Post by bellaterror on 2006-06-25
here is what it is

[IMG]http://i13.photobucket.com/albums/a280/LsKamikazi/screenie.jpg[/IMG]

---

### Post by lazyd2 on 2006-06-25
[quote=bellaterror]here is what it is

[IMG]http://i13.photobucket.com/albums/a280/LsKamikazi/screenie.jpg[/IMG][/quote]Get **libc6.deb** from [here]("http://packages.debian.org/testing/libs/libc6") and **tzdata.deb **(another dependency) from [here]("http://packages.debian.org/testing/libs/tzdata")

One question though, why don't you use the one in the repos(just asking)

---

### Post by bellaterror on 2006-06-25
ummm dont knot what the repos is............:(

---

### Post by bellaterror on 2006-06-25
Error: dependency is not satisfiable: tzdata

WTF IS GOING ON

---

### Post by lazyd2 on 2006-06-25
[quote=bellaterror]ummm dont knot what the repos is............:([/quote]Just write ```
sudo apt-get install gparted
```

[COLOR=Gray]{repos=repositories}[/COLOR]

---

### Post by bellaterror on 2006-06-25
oh c i alredy tried didnt work... said its already installed but only 0.1 is installed... and well ya and BTW y is it that no matter wat DEB file i try to DL it comes up with an error?

---

### Post by bellaterror on 2006-06-25
no one has any solutions? please?

---

