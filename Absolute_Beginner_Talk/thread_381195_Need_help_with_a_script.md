---
title: "Need help with a script"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-03-10
I'm trying to make a script to upload files to an ftp server, to update a website.  I'm a little stuck, here's what I have so far.
```

#!/bin/bash
# Website update script
cd Website(This is the directory with the files I want to copy.)
ftp ftp.servername.com
put index.html 
put about.html
put calendar.html
put contact.html
put schedule.html

```
However, it doesn't execute the put commands until I manually exit the ftp server, how can I fix this?

---

### Post by lloyd_b on 2007-03-10
Try this:
```
#~/bin/sh
cd Website
echo "put index.html about.html calendar.html contact.html schedule.html" | ftp ftp.servername.com
```

I'm not sure that this will actually work, mind you.  I've done something similar, but I've always used "ncftp" rather than "ftp", and it behaves a little differently.

Lloyd B.

---

### Post by vinchi007 on 2007-03-12
why dont you have "quit" command at the end of your script, which would exit out of ftp server.

---

### Post by IYY on 2007-03-12
> **Matt1632 said:**
> I'm trying to make a script to upload files to an ftp server, to update a website.  I'm a little stuck, here's what I have so far.
```

#!/bin/bash
# Website update script
cd Website(This is the directory with the files I want to copy.)
ftp ftp.servername.com
put index.html 
put about.html
put calendar.html
put contact.html
put schedule.html

```
However, it doesn't execute the put commands until I manually exit the ftp server, how can I fix this?

This is a bit of a tricky one. Here's how it's done:

```

#!/bin/bash
# Website update script
cd Website(This is the directory with the files I want to copy.)
ftp ftp.servername.com **<<END**
put index.html 
put about.html
put calendar.html
put contact.html
put schedule.html
[B]quit
END[/B]

```

---

