---
title: "where are things installed?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-02-01
Is there a default installation directory?  Such as in windows it's C:/program files/

The reason I'm asking is that I found a deb package for filezilla the ftp client and I love using filezilla, but the deb package didn't have the latest version.  I found the update and when I extracted the compression there were two folders, one was a bin folder and the other was a folder called share.  If I open up the bin folder I can run the file there, which will run filezilla.

I'm just not sure where to place these folders/files so that my shortcuts will continue to work.  Is there a way to tell where things are pointing?

thanks in advance

---

### Post by empthollow on 2007-02-01
you need to place these folders in your $PATH to see this type 
```
echo $PATH
```
in the terminal, alternatively you can add those directories to your path
```
export PATH=$PATH:/to/my/folder/bin
```

---

### Post by Sef on 2007-02-01
Read about the [Linux File System]("http://http://www.freeos.com/articles/3102/").

---

### Post by mikewhatever on 2007-02-01
> **Sef said:**
> Read about the [Linux File System]("http://http://www.freeos.com/articles/3102/").

No article there.

Edit:That's strange. Following Sef's link brought me to a page of commercials, but I then googled and found the article.

---

### Post by bone2006 on 2007-02-02
it's because the link he posted was this [http://http//www.freeos.com/articles/3102/](http://http//www.freeos.com/articles/3102/) instead  of

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

Thanks for the link, going to read it now

---

