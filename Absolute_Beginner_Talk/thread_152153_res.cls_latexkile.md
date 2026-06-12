---
title: "res.cls /latex/kile"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by findik1 on 2006-03-29
I was using MikTex on windows machine to write my CV with sytle file:
\documentclass[overlapped,line,draft,10.8pt,letterpaper]{res}
\usepackage{bibunits} %to use many bibliographies

when I run in kile it gies an error : File `res.cls' not found. \usepackage

I used synaptic and apt-get to get this file but could not find:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package res


Any idea what to do? I know MikTeX had all the packages from CTAN, everthing is not necessary but why does not Ubuntu have these main things?
Thanks,
findik

---

### Post by findik1 on 2006-03-29
ok I donloaded the files from CTAN web page:-D

---

### Post by Munchkinguy on 2007-09-19
With TeX Live, you can do
```
sudo apt-get install texlive-latex-extra
```

---

