---
title: "My picture cannot be loaded from my server"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by ddhazxiao on 2008-01-07
Hi guys..

my problem is , my picture cant be displayed in the index page from my server.. plz help me. 

[www.savekidney.com](www.savekidney.com)

Thanks !

---

### Post by hyper_ch on 2008-01-07
Are you sure you have to correct path and filename?

```

http://www.savekidney.com/Pic/title.jpg

```

is not the same as

```

http://www.savekidney.com/pic/title.jpg

```

or

```

http://www.savekidney.com/Pic/Title.jpg

```

or

```

http://www.savekidney.com/Pic/title.JPG

```

---

### Post by ddhazxiao on 2008-01-07
yes. since i used Quanta plus to add the img. i think the path is correct.

---

### Post by hyper_ch on 2008-01-07
Thinking and knowing are two different things.

Where is the picture located and what is its filename?

---

### Post by zipperback on 2008-01-07
I checked the direct link to the image you are referencing.

[http://www.savekidney.com/Pic/title.jpg](http://www.savekidney.com/Pic/title.jpg)

Also, if you call up the /Pic directory in your browser you can see that the file is there, so I am guessing it's a file permissions issue.

```

Forbidden

You don't have permission to access /Pic/title.jpg on this server.

```


Check your file permissions on the image.

- zipperback
:popcorn:

---

### Post by ddhazxiao on 2008-01-07
Thanks!.. i din't notice the file permission.
problem solved.

---

