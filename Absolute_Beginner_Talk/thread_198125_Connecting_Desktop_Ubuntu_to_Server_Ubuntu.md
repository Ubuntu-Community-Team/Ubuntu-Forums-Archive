---
title: "Connecting Desktop Ubuntu to Server Ubuntu"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by klcant on 2006-06-16
I currently have a desktop PC and a server setup witn Ubuntu 6.06.  Is there a way to login to the server from my desktop (kind of like terminal server)?  I found this post:

[http://www.ubuntuforums.org/showthread.php?t=156019&highlight=log+server+desktop](http://www.ubuntuforums.org/showthread.php?t=156019&highlight=log+server+desktop)

Is this the best way?  It looks like this will do what I am looking for ... but not sure.  Thanks all for the help.

---

### Post by olsonar on 2006-06-16
just pure ssh will work. just install openssh-server on the server and openssh-client on the desktop, then open a terminal on the desktop and type

```
ssh 0.0.0.0
``` 
replacing 0.0.0.0 with the IP of your server

---

