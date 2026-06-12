---
title: "Adding J2SE and MySQL"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by marv12marv on 2007-09-04
I do not have internect access on my Ubuntu box, so I am attempting to add these after the fact. I now have a Desktop install and I have both the Server and the Alternate CD if that helps me.

1.) Java
I down loaded jdk-6u2-linux-i586.bin off the Sun site (it was the only 'linux' install) and copied it onto my Obuntu hard drive. How do I execute this install? Typing 'jdk-6u2-linux-i586' in a terminal box gives an error message.

2.) MySQL
From the MySQL site I've downloaded:
libmysqlclient15-dev_5.0.21-3ubuntu1_i386.deb
mysql-client-5.0_5.0.21-3ubuntu1_i386.deb
mysql-common_5.0.21-3ubuntu1_all.deb
mysql-server-5.0_5.0.21-3ubuntu1_i386.deb

When I issue the command "sudo dpkg -i <package name>.deb" I get a dependancy error. How do I install MySQL?

thanks.

---

### Post by aitorcalero on 2007-09-04
> 1.) Java
I down loaded jdk-6u2-linux-i586.bin off the Sun site (it was the only 'linux' install) and copied it onto my Obuntu hard drive. How do I execute this install? Typing 'jdk-6u2-linux-i586' in a terminal box gives an error message.

You may need to change file properties to execution:

```
sudo chmod +x jdk-6u2-linux-i586.bin
```

then execute it (./ is important):

```
sudo ./jdk-6u2-linux-i586.bin
```

You have to use sudo since some files will be installed in root's directories

> 2.) MySQL
When I issue the command "sudo dpkg -i <package name>.deb" I get a dependancy error. How do I install MySQL?


You should review all dependency libraries of all of deb files. It is a tedious process but, if you do not have internet connection it is the only way.

An alternative way is to download an Ubuntu DVD with repositories.

---

