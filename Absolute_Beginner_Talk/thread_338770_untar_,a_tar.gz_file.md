---
title: "untar ,a tar.gz file"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-01-14
how do you untar a tar.gz file,is there a command for it ,i am searching forums and google but any help appreciated
:D

---

### Post by rabid9797 on 2007-01-14
if you have automatix install archive manager(im recommending this because it'll be helpful in the future too)

if not, go to [http://getautomatix.com](http://getautomatix.com) download and install, then install the archive manager(along with whatever else you want)

---

### Post by marx2k on 2007-01-14
from the tar man page.

 tar -xvvzf foo.tar.gz
 extract gzipped foo.tar.gz

---

### Post by po0f on 2007-01-14
STREETURCHINE,

You can use file-roller, just double click on it.  From the command line:
```
[FONT="Courier New"]$ tar xvzf tarball.tar.gz[/FONT]
```

[list]
[*]**x**: extract the archive
[*]**v**: verbose (not really needed)
[*]**z**: gzip format (use **j** if it's a *.tar.bz2)
[*]**f**: the argument following is the file to extract (or create if you use **c** instead of x)
[/list]

---

### Post by STREETURCHINE on 2007-01-14
```
rabid9797  	if you have automatix install archive manager(im recommending this because it'll be helpful in the future too)
```

i have archive manager but when i double clicked it extracted the file but the i could not use it

```
po0f  	STREETURCHINE,

You can use file-roller, just double click on it. From the command line:
Code:

$ tar xvzf tarball.tar.gz


```

thanks i did not know you could do that with file roller,i have it installed just never used it

```
marx2k  	from the tar man page.

tar -xvvzf foo.tar.gz
```

thanks i found it finaly by googling just had to work out the right wording to get me there..

so thanks for your help ,we all took differant route's but got the same result

---

