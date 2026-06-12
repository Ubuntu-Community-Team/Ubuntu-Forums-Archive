---
title: "Cannot find 'ptviewer' in synaptic"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Wylkar on 2008-02-19
I cannot find 'ptviewer' in synaptic, is it part of another file? Also is there a way to tell if you have a program installed other than using synaptic?

---

### Post by neurostu on 2008-02-19
I have most of the Ubuntu repostories enabled on my machine and:
```

$aptitude search ptviewer

```
returned no results. I would guess that it isn't in the Ubuntu distros

---

### Post by Wylkar on 2008-02-19
do you have any idea where I could get it?

---

### Post by neurostu on 2008-02-19
It looks like it is no longer supported by the developer, but you might be able to find it here:
[http://www.all-in-one.ee/~dersch/](http://www.all-in-one.ee/~dersch/)

---

### Post by Wylkar on 2008-02-19
I have downloaded the files and it says:
 Applet/ptviewer.jar The java class ptviewer.class compressed as jar file. This is the basic panorama viewer without any extensions.This file has to be loaded by the html-browser to display panoramas. It is recommended to also install the ptviewer.class file since some browsers can not read compressed jar-files.
How would I load this with my browser (firefox)?
thanks

---

### Post by FuturePilot on 2008-02-19
You could use the BigApplet&Application ptviewer.jar.  That one functions as a standalone application.

---

### Post by Wylkar on 2008-02-20
when I open the folder (which I have downloaded and is on my desktop) in firefox and click on the .jar files it acts like I am downloading it. do I need to copy it into the firefox directory like I would for a patch?
thanks

---

### Post by neurostu on 2008-02-20
No what you probably need to do is create a webpage and then embed the .jar into the webpage like an applet. 

I don't know to much about how to use jars try google I'm sure the answer is out there...

---

