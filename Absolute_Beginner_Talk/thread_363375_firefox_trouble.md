---
title: "firefox trouble"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by n0ll on 2007-02-16
firefox truble

runing kubuntu-6.10-amd64 on a amd62 OEM box.

installed firefox via method 4 ./installnewfirefox.sh script
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

get a "firefox" installed ok message. but when i go Kmenu> internt> firefox
firefox looks like it is loading, but then it just goes away.

in a terminal when i type:
firefox 
i get: 
/opt/firefox/run-mozilla.sh: 424: /opt/firefox/firefox-bin: not found

then i do
cd /opt/firefox; ls -l | grep firefox

-rwxr-xr-x 1 root root     5247 2006-12-08 15:10 firefox
-rwxr-xr-x 1 root root 10521812 2006-12-08 15:11 firefox-bin
lrwxrwxrwx 1 root root       24 2007-02-16 17:55 plugins -> /usr/lib/firefox/plugins

should firefox-bin be a DIR?

while firefox is trying to load
ps -e | grep fire
returns NULL

seems to me like firefox is installed, but it does is not loading.

any ideas? do i just not know how to open firefox?

Note: i have also removed and reinstalled via Adept manager and add/remove programs, and both give the same err.

---

### Post by aysiu on 2007-02-16
There are no official Mozilla builds of Firefox for AMD64. That script will install only x86.

If you want AMD64, try the Swiftfox script, which will let you install to the processor type of your choice:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox)

---

