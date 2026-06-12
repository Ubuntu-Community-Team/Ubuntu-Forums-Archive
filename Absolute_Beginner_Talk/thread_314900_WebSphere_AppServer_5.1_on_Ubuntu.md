---
title: "WebSphere AppServer 5.1 on Ubuntu"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by faseyiks on 2006-12-08
I have just installed Ubuntu onto my machine at work because I need to install the Linux version of the Websphere AppServer 5.1 to work with in my environment.

After the installation I get this message starting the appserver:

wasadmin@xzt6f3-desktop:/opt/WebSphere/AppServer/bin$ ./startServer.sh server1
/bin/uname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/opt/WebSphere/AppServer/java/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
expr: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Can someone help.
Even when I run sudo aptitude update, i get errors requesting as follows:

Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
  407 Proxy Authentication Required [IP: 192.85.50.83 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
  407 Proxy Authentication Required [IP: 192.85.50.83 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_GB
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
  407 Proxy Authentication Required [IP: 192.85.50.83 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
  407 Proxy Authentication Required [IP: 192.85.50.83 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_GB
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  407 Proxy Authentication Required [IP: 192.85.50.83 80]


I shall be glad to be assisted.

faseyiks

---

### Post by deadgobby on 2006-12-08
Did you check this out yet?
[http://www-128.ibm.com/developerworks/forums/dw_thread.jsp?forum=541&thread=132780&cat=51](http://www-128.ibm.com/developerworks/forums/dw_thread.jsp?forum=541&thread=132780&cat=51)

---

