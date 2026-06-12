---
title: "How to send a file across SSH connection."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by d10b on 2007-12-04
I'm connected to my ubuntu machine at home from a windows machine using putty.  How do I send a file through the ssh connection to the windows machine I'm on?

---

### Post by mali2297 on 2007-12-04
I don't know about PuTTY, but here is how I would do it from a Linux terminal:
```

scp yourusername@address.to.ubuntumachine:/path/to/yourfile yourcopy

```

---

### Post by Dr Small on 2007-12-04
To use SCP with PuTTY, you must first download PSCP:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by buntunub on 2007-12-04
Look on Ubuntu Community Doc's under SSH How to. I remember seeing some stuff on that guide about Putty and file transfer configurations and such. Its just weird how I always seem to find the answer to 99.99999999999999999999999% of every problem I encounter with Linux from Google searches. :confused:

---

### Post by Zack McCool on 2007-12-04
Rather than putty, I usually use [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) from windows.  GUI, and you can easily see the status while you are doing other things...

---

