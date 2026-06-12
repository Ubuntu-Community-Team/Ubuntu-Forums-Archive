---
title: "I have a .deb file... How to install it?"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by Starlight on 2006-02-22
Hello! I've downloaded Opera 9 as a deb file, but I don't know how to install it... Can anyone help me? :)

---

### Post by kaamos on 2006-02-22
Hello!

Move the file to your home directory and then:
Applications->Accessories->Terminal
```
sudo dpkg -i name_of_file.deb
```

---

### Post by Starlight on 2006-02-22
Thank you! It works :)

---

### Post by Ozitraveller on 2006-02-22
[QUOTE=kaamos]Hello!

Move the file to your home directory and then:
Applications->Accessories->Terminal
```
sudo dpkg -i name_of_file.deb
```[/QUOTE]

And in Dapper you just double-click them! :)

---

### Post by Brunellus on 2006-02-22
[QUOTE=Ozitraveller]And in Dapper you just double-click them! :)[/QUOTE]
somehow, I'm still a bit uneasy about this.  I got myself into MASSIVE trouble doing this with RPMs in SuSE.

---

### Post by byen on 2006-02-22
yes... as kaamos has answered... you can install .deb by doing
sudo dpkg -i packagename.deb
sudo apt-get -f install

-the first installs the deb
-the second takes care of any dependencies.(you should do this only if you get a message telling you about dependencies.

> And in Dapper you just double-click them!
I did not know that... Cool! Hope its easier than what Brunellus has faced with SuSE :-D

---

