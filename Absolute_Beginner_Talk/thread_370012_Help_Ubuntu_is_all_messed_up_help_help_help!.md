---
title: "Help Ubuntu is all messed up help help help!"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by scwinn on 2007-02-25
When I reboot I get an error message

"Server authorization directory (daemon/serv Auth Dir) is set to /usr/lib/gdm but this does not exist. Please redirect gdm configure and restart gdm

now what????

I cannot run anything!!!!

HELP ME PLEASE!!!!!!!

---

### Post by shareMenaPeace on 2007-02-25
Hello, 
you could try login with failsafe or if this not works just switch to the console with STRG ALT F2 (back to the desktop STRG ALT F7)

```
sudo dpkg-reconfigure gdm

```
than boot if it still not works try 

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by shareMenaPeace on 2007-02-25
Better follow this topic first
[http://ubuntuforums.org/showthread.php?t=368168&highlight=Server+authorization+directory](http://ubuntuforums.org/showthread.php?t=368168&highlight=Server+authorization+directory)

---

