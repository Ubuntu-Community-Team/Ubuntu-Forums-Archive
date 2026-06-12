---
title: "xml2-config not found while installing PHP"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2006-12-30
I am trying to install PHP on my Ubuntu 6.06 system. When I do 'sudo ./configure', I get the following error:-

```
checking whether to enable IPv6 support... yes
checking how big to make fd sets... using system default
checking whether to enable versioning... no

Configuring extensions
checking whether to enable LIBXML support... yes
checking libxml2 install dir... no
checking for xml2-config path...
configure: error: xml2-config not found. Please check your libxml2 installation.
```

Also, I get the following output while trying to check libxml*

```
$ ls /usr/lib/libxml*
/usr/lib/libxml2.so.2             /usr/lib/libxmlsec1-openssl.so.1
/usr/lib/libxml2.so.2.6.24        /usr/lib/libxmlsec1-openssl.so.1.2.9
/usr/lib/libxmlsec1-nss.so.1      /usr/lib/libxmlsec1.so.1
/usr/lib/libxmlsec1-nss.so.1.2.9  /usr/lib/libxmlsec1.so.1.2.9
```

Can anyone suggest me what's missing and what do I need to do to proceed with PHP installation.

- Smith

---

### Post by logos34 on 2006-12-30
i think you need the development packages (libxml2-dev)

---

### Post by Perfect Storm on 2006-12-30
```
sudo aptitude install libxml2-dev
```

Should solve it.

---

### Post by smith.norton on 2006-12-30
Is libxml2-dev present in the CD or Ubuntu or do I have to download it from the online repository?

I am sorry I am not at home now that I can check the CD and at home, I don't have Internet.

---

### Post by Perfect Storm on 2006-12-30
You have to download it. Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and download it. You also need zlib1g-dev to make it work.

---

