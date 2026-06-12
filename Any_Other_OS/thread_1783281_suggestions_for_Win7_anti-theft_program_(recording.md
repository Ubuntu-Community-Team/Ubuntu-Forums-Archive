---
title: "suggestions for Win7 anti-theft program (recording thief on webcam, recording IP, etc"
date: 2011-06-15
forum: Any Other OS
---

### Post by hanzj on 2011-06-15
Hello,
We've just bought a Win7 laptop with a webcam. Is there a FREE program that can help me recover my laptop in case it gets stolen? Some features I think would be good are: recording of thief using the laptop's webcam, recording of IP address, recording of the screen, etc.

Note: this laptop is planned to have Ubuntu, but the program should be for Windows 7.

Thanks.

---

### Post by ruffEdgz on 2011-06-15
So you are going to place Ubuntu on the laptop but you still want to use Windows software?

Well, I know lojack ([http://www.lojack.com/](http://www.lojack.com/)) has worked for a lot of people that I know in the past.

Webpage to lojack laptop: [http://www.lojack.com/pages/laptop.aspx](http://www.lojack.com/pages/laptop.aspx)

---

### Post by Mark Phelps on 2011-06-15
+1 for Lojack.  Use it myself for my tablet PC.

But it's not free.

---

### Post by pqwoerituytrueiwoq on 2011-06-15
for a cheap (free) solution i would use curl at startup to fetch a php page (use your home computer or a free web host) i made with some long random key (to verify it is that computer) to recored the ip address it is on
sudo apt-get install curl
for windows [http://curl.haxx.se/download.html#Win32](http://curl.haxx.se/download.html#Win32)
[PHP]<?php
if($_GET['key']=='53263-HEY-THIS-IS-MY-LAPTOP-454456'){
$file=fopen('lastloc.txt','a');
fwrite($file,$_SERVER['REMOTE_ADDR']);
fclose($file);
}
?>[/PHP]the startup command
```
curl http://example.com/myscript.php?key=53263-HEY-THIS-IS-MY-LAPTOP-454456
```

this would store your ip address to a file so if it is stolen you can report it's location (police) with its ip address

---

### Post by hanzj on 2011-06-15
I asked for programs that are FREE. [http://www.absolute.com/en/lojackforlaptops/home.aspx](http://www.absolute.com/en/lojackforlaptops/home.aspx) has products, all that cost money.

---

### Post by Perfect Storm on 2011-06-15
Moved to Other OS/Distro Talk.

---

### Post by krapp on 2011-06-16
Why not use a laptop lock instead?

---

