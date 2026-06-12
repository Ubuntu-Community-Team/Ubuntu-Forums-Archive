---
title: "no video played!"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by syareefdol on 2007-12-22
hey guys!need some help again!!when i open youtube webpage..there no video cant be play..why is dat?do i have wrong installation??any command line for configure it?help me!bless all!

---

### Post by webofunni on 2007-12-22
Hello,

  You need flash support for viewing flash videos from youtube....................

Assuming you are using firefox 

close browser windows 

1. Get flashplayer from [http://www.macromedia.com/go/getflash](http://www.macromedia.com/go/getflash)
2. Down load the tar.gz file
3. Unpack it tar -zxvf install_flash_player_9_linux.tar.gz
4. copy the file libflashplayer.so to /usr/lib/mozilla/plugins
cp libflashplayer.so /usr/lib/mozilla/pugins
 
thats all

---

