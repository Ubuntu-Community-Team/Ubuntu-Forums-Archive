---
title: "Lost a file, but it is most clearly there.."
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by bobandirus on 2007-09-01
Terminal cant find this file! and z:/home.... has worked before! So where the heck is it??? And yes I do have mono installed (fairly shure) before anyone askes.
[http://i194.photobucket.com/albums/z276/bobandirus/whereisitthen.png](http://i194.photobucket.com/albums/z276/bobandirus/whereisitthen.png)

---

### Post by forestpixie on 2007-09-01
delete - sorry thought I had it :(

you could try dragging the file onto the terminal - that's supposed to work isn't it

---

### Post by splintercellguy on 2007-09-01
The path looks wrong, and why use Wine for Mono apps?

---

### Post by Majorix on 2007-09-01
Try this:
```
wine /home/andrew/Desktop/Paint.NET.3.10.exe
```

---

### Post by bobandirus on 2007-09-01
> **splintercellguy said:**
> The path looks wrong, and why use Wine for Mono apps?

Because I dont know how to use mono:( *will go looking for a howto*

> 

Try this:
```
 wine /home/andrew/Desktop/Paint.NET.3.10.exe 
```


Thanks that worked but then it didnt due to needing mono....

---

### Post by Majorix on 2007-09-01
Search for mono runtime under Synaptic.

Then
```
mono /path/to/file
```

Hope that helps.

---

