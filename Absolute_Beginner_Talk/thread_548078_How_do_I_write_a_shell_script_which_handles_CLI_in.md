---
title: "How do I write a shell script which handles CLI input on its own?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by some_random_noob on 2007-09-10
I want to write a shell script which fills out the input all by itself. For example, an FTP script which sends a file and also knows how to do it in advance:

```

ftp
ftp < open
ftp < 10.1.1.4
ftp < *password*
ftp < put
ftp < *file origin on local machine*
ftp < *file destination*

```

Isn't that how I'm meant to make it fill out fields by itself? I'm confused :confused:

Someone help me out here :( I want a script that will fill out the prompts which are usually sent to the user.

---

### Post by picpak on 2007-09-10
Basically, what you would do is just that:

```

#!/bin/sh

ftp
ftp < open
ftp < 10.1.1.4
ftp < *password*
ftp < put
ftp < *file origin on local machine*
ftp < *file destination*

```

Save it as *ftpscript* (or whatever you'd like to call it) and then run:

```
chmod +x ~/ftpscript
```

To run each command one after the other, use *&&* like so:

```

#!/bin/sh

ftp &&
ftp < open &&
ftp < 10.1.1.4 &&
ftp < *password* &&
ftp < put &&
ftp < *file origin on local machine* &&
ftp < *file destination* &&

```

To run each command at the same time, use *&* like so:

```

#!/bin/sh

ftp &
ftp < open &
ftp < 10.1.1.4 &
ftp < *password* &
ftp < put &
ftp < *file origin on local machine* &
ftp < *file destination* &

```

Hope this helps!

---

### Post by bodhi.zazen on 2007-09-10
You might like to take a look at expect :

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

	[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

