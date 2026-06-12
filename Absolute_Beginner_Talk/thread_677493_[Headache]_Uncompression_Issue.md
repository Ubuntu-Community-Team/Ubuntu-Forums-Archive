---
title: "[Headache] Uncompression Issue"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by family on 2008-01-24
I have a ZIP file compressed by WinRAR, and Archive Manager gives me Error 98 talking about unsupported file-types. It is a Zip file, I assure you. The Manager will open its window and show the contents of the archive, but ultimately fail to extract...
I used 'Choose best compression method' to compress them, so I'm guessing that it wasn't Legacy Zip 2.0 compression, but Ubuntu should be able to uncompress files, no?
It's just 600 or so kb... :(
Anyone know of a third-party app capable of viewing this Zip?

---

### Post by emarkd on 2008-01-24
Try it from the command line and see if you get any errors.

unzip filename.zip

---

### Post by family on 2008-01-24
Yes, I have tried Unzip from commad-line, as well as 7zip, ark, and xarchiver
No luck
```

q@Q-Desktop:~$ cd ~/D*/
q@Q-Desktop:~/Desktop$ unzip GPG.zip
Archive:  GPG.zip
   skipping: GPGv2.py                unsupported compression method 98
   skipping: GPGv2.cpp               unsupported compression method 98
q@Q-Desktop:~/Desktop$ :(!
bash: syntax error near unexpected token `!'
q@Q-Desktop:~/Desktop$

```

---

### Post by emarkd on 2008-01-24
I dunno... apparently you can install Winrar using Wine

[http://imyousuf-tech.blogs.smartitengineering.com/2007/11/winrar-on-ubuntu.html](http://imyousuf-tech.blogs.smartitengineering.com/2007/11/winrar-on-ubuntu.html)

May be worth a shot...

---

### Post by family on 2008-01-25
I'm just going to compress it using an older version of Zip.
It disapoints me that one might have to install Wine (64 mb these days?) and then purchase WinRAR to uncompress a package... Hmmm. Perhaps this is something Archive Manager can improve on for Hardy?

---

