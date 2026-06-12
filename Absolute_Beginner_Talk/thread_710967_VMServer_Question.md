---
title: "VMServer Question"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-29
I've downloaded VMserver, and compile it, and some how on the installation, I got confused when it asked me about servers, localhost, net mask etc.. I answered them all with yes and with random IP address, don't know why, probably did not expected that VMServer or VMWare Server is that complicated, VirtualBox is much more easy to use and to install, and does not consume much space.

Now, I can't find any uninstall for VMWare Server, so, how will I remove it on my computer?

And what is the difference between VMWare Server and Player?

---

### Post by kpkeerthi on 2008-02-29
If you installed from source.. cd to the source directory (from where you ran **make install**) and run **make uninstall**.

---

### Post by jrusso2 on 2008-02-29
The server is really meant as a server that you can access from other work stations across a network but you can use it stand alone too.  You can create the virtual images with it.

VMware player is just a player and you can't use it to create the images but there are lots of images you can download pre made for it.

---

### Post by zvacet on 2008-02-29
If you installed correctly and it is runing there is no need to remove it.Anyway if you want to do it try with 

```
 sudo vmware-uninstall.pl
```

---

