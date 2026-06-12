---
title: "Proxing Terminal"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-11-27
I have been following this thread: [http://ubuntuforums.org/showthread.php?t=307782](http://ubuntuforums.org/showthread.php?t=307782) to proxy my connection via terminal.

I have followed the instructions, no error messages have reported back so I guess it's worked (I might add, I took away the username bit as I was using a free proxy).

I'm not convinced I am full proxies tho :confused: Is there a cmd that you can do which outputs your external ip?

---

### Post by Bachstelze on 2006-11-27
You could do

```
wget http://www.whatismyip.com
```

It will create a HTML file in the current dir with your WAN IP in it.

---

