---
title: "turning ports off on xubuntu (i.e. turn it into a server)"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by neorou on 2007-04-02
So,
I've been using xubuntu now for a couple of weeks. I've been an OS X user for about 5 years now. But I am very attracted to simplicity of xubuntu.

Ubuntu itself does not seem to have a GUI-equipped server edition. Am I mistaken?

Anyway, is there a way to turn xubuntu to a LAMP & SMB file server? I have the LAMP covered. Used synaptic to get everything up and running and am hosting a site on an internal private network. I could not however get it to run faster file transfer between it and my macs. So far, I have resorted myself to using ftp for everything.

Anyone?

:confused:

---

### Post by atomic0x on 2007-04-02
You can install samba to have a SMB server.  I don't pretend to know how to set it all up, but a good start would be to open a terminal and type:
```

sudo apt-get install samba samba-common
```

You can also install a samba-doc and/or samba-doc-pdf package.  These docs will tell you all you need to know, and more about samba.  They are also available at [http://www.samba.org](http://www.samba.org)

---

### Post by arbulus on 2007-04-02
You could use NFS to share with your Mac.  I dunno if it would be faster than Samba, but here are a couple of links on it:

[http://sial.org/howto/osx/automount/](http://sial.org/howto/osx/automount/)
[http://www.eecs.umich.edu/dco/help/NFSMac.htm](http://www.eecs.umich.edu/dco/help/NFSMac.htm)

You can also share files over SSH, but I'm not too familiar with how to do that.

The great thing about using Macs on a network with Linux machines is that you can use most Linux/Unix protocols for communication.  After all, Macs are essentially just Unix boxes.

---

### Post by neorou on 2007-04-05
Yeah, I tried SAMBA. It works to a certain extent. I was having some problems with authentication. I had not thought of using NFS. I'll give that a try and compare it.

Thanks guys.

---

