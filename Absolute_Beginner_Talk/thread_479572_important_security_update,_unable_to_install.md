---
title: "important security update, unable to install"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-06-20
the update icon on the tray shows new updates to install but as i select them and then click on install updates it tells that unable to retrieve from server then give the following description :

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-16_2.6.20-16.28_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-16_2.6.20-16.28_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-16-generic_2.6.20-16.28_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-16-generic_2.6.20-16.28_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-16-generic_2.6.20-16.28_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-16-generic_2.6.20-16.28_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.28_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.28_i386.deb)
  404 Not Found

my internet connection is fine am always installing updates but why these updates dont i really dont know???

---

### Post by diatribe on 2007-06-20
the server itself may be lagging, try again later would be my advice

---

### Post by akkad on 2007-06-22
i found out that the files not available on the server, but as i googled the files i found them but with it seems a newer version just like the following :
the files needed by my update manager are :
linux-headers-2.6.20-16_2.6.20-16.28_i386.deb
linux-headers-2.6.20-16-generic_2.6.20-16.28_i386.deb
linux-image-2.6.20-16-generic_2.6.20-16.28_i386.deb
linux-libc-dev_2.6.20-16.28_i386.deb

using my search results i found :
linux-headers-2.6.20-16_2.6.20-16.29_i386.deb
linux-headers-2.6.20-16-generic_2.6.20-16.29_i386.deb
linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
linux-libc-dev_2.6.20-16.29_i386.deb

the deffirence is in the version (the number 28 become 29) , so is it ok to install them instead??
this is the link where i found the files:
[http://ftp.cica.es/guadalinex/repositorio/guadalinex-toro/pool-ubuntu/main/l/linux-source-2.6.20/](http://ftp.cica.es/guadalinex/repositorio/guadalinex-toro/pool-ubuntu/main/l/linux-source-2.6.20/)

---

### Post by PartisanEntity on 2007-06-22
I too would recommend that you wait a little, it is most probably a server lag issue.

---

### Post by akkad on 2007-06-22
plz will any body click on one of the files links above in my first post and see if the files are availabe, am trying once and once again but it is useless !!!

---

### Post by seshomaru samma on 2007-06-22
i get :
```
The requested URL /ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-16_2.6.20-16.28_i386.deb was not found on this server
```.

---

### Post by akkad on 2007-06-22
the same to me :(  , where shall i find the files ??

---

