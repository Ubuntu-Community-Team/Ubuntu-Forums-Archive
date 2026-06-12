---
title: "installed dtv doing this. need help."
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by dude of wonders on 2006-02-27
go here to see how i installed it.

[https://develop.participatoryculture.org/projects/dtv/wiki/GTKX11BuildDocs](https://develop.participatoryculture.org/projects/dtv/wiki/GTKX11BuildDocs)
```

cd tv/platform/gtk-x11

./test.sh

```
when i typed in that i get this in my terminal

```

/usr/lib/python2.4/distutils/dist.py:236: UserWarning: Unknown distribution option: 'console'
  warnings.warn(msg)
running install
running build
running build_ext
building 'fasttypes' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c /home/lionheart/tv/portable/fasttypes.cpp -o build/temp.linux-i686-2.4/home/lionheart/tv/portable/fasttypes.o
unable to execute gcc: No such file or directory
error: command 'gcc' failed with exit status 1
Traceback (most recent call last):
  File "DTV.py", line 14, in ?
    import app
  File "/home/lionheart/tv/platform/gtk-x11/../../portable/app.py", line 2, in ?    import feed
  File "/home/lionheart/tv/platform/gtk-x11/../../portable/feed.py", line 1, in ?
    from downloader import grabURL
  File "/home/lionheart/tv/platform/gtk-x11/../../portable/downloader.py", line 1, in ?
    from database import DDBObject, defaultDatabase
ImportError: No module named database


```

any ideas what i need to do??

---

### Post by Pragmatist on 2006-03-01
> gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c /home/lionheart/tv/portable/fasttypes.cpp -o build/temp.linux-i686-2.4/home/lionheart/tv/portable/fasttypes.o
unable to execute gcc: No such file or directory

First I would check to see which of these files are actually on my system.  

Also the part of this line that says: > -I/usr/include/python2.4  I may be wrong, but it seems to me that there should be a space after **-l** so that it becomes** -l /usr/include/python2.4**

Give us the test.sh script so we can see where it fails.

---

### Post by dude of wonders on 2006-03-01
thanks for the reply didnt think any help was coming glad i decided to check up on it. heres the script.


#!/bin/sh
PYTHON=`which python2.4`

if ! [ -a $PYTHON ] ; then
    PYTHON=`which python`
fi

$PYTHON setup.py install --prefix=./dist && PYTHONPATH=./dist/lib/python2.4/site-packages $PYTHON DTV.py


:neutral: so whats it look like doc, she gonna make it??

---

### Post by Pragmatist on 2006-03-01
Looks like your not the only one missing the module which provides the DDBObject

[http://sourceforge.net/mailarchive/message.php?msg_id=14124090](http://sourceforge.net/mailarchive/message.php?msg_id=14124090)

I guess that kind of thing happens with beta software.  I looked through the archives at the above link and didn't see anything definitive.  Maybe you can find more.  Good luck!

---

### Post by dude of wonders on 2006-03-01
thanks for the help maybe when dapper comes out this bug will fix its self, or i'll just remain patient and wait for the final release of dtv:)

---

