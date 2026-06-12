---
title: "unable to parse XML-why??"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by danijela on 2008-02-21
im workin on Ubuntu..
anyway I have xml document : sample.xml

<?xml version="1.0"?>
<!DOCTYPE article PUBLIC "-//OASIS//DTD DocBook XML V4.5//EN"
"http://www.oasis-open.org/docbook/xml/4.5/docbookx.dtd">
<article>
  bla bla..
</article>

URL is valid and i have net connection

aftercommands :
$ export DB="/usr/share/sgml/docbook/docbook-xsl-1.51.1"
$ xsltproc -o sample.html $DB/html/docbook.xsl sample.xml

theres an error and warning: failed to load external entity "sample.xml"
unable to pharse sample.xml

Any ideas??
Thanx
Danijela

---

### Post by spiderbatdad on 2008-02-21
```
sudo apt-get install libexpat1-dev
```???

---

### Post by danijela on 2008-02-21
??

apt command not found

---

### Post by spiderbatdad on 2008-02-21
typo...unnecessary space after "apt"  should be apt-get...btw this is only a suggestion...you might go to synaptic and search xml parser for other packages.

---

### Post by danijela on 2008-02-21
hmm Invalid operation installl:( :( :(

---

### Post by danijela on 2008-02-21
sorry,lapsus ofcorse..we will c now does this help

---

### Post by danijela on 2008-02-21
dont know why but after that command everything block :(

---

### Post by andrew.46 on 2008-02-21
Hi,

 You may need another package as well as docbook:

```
$ sudo apt-get install docbook docbook-xsl
```

   Andrew

---

### Post by danijela on 2008-02-21
ive allready installed docbook-xsl -1.73.2 version in /usr/share/sgml/docbook

---

