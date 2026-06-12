---
title: "installing .bin with kubuntu"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by ktown on 2007-06-26
Hey, just a simple question. How do I install a .bin file (Google Earth) with Kubuntu?

---

### Post by FleetAdmiral74 on 2007-06-26
I know there are google earth guides out there. Just google "google earth kubuntu" and you will likely find a ton of guides.

---

### Post by ktown on 2007-06-26
just a more general question, whenever i get the binary codes, what do i do with them to install them

---

### Post by aktiwers on 2007-06-26
Google earth can be installed using Automatix2.

But to install .bin files.. right-click on the file and pick "properties".
Then navigate to "Permision" tap and give it execute rights.

Or type this in terminal:
```
chmod +x yourbinfile.bin
```


And then just run it from Terminal like this:
```
./yourbinfile.bin
```

Thats all! Remember to make sure you are in the same directory as the bin file ;)

[http://monkeyblog.org/ubuntu/installing/#installer](http://monkeyblog.org/ubuntu/installing/#installer)
[http://monkeyblog.org/ubuntu/installing/#permissions](http://monkeyblog.org/ubuntu/installing/#permissions)

---

