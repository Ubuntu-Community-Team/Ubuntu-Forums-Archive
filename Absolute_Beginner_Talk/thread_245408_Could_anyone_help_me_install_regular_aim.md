---
title: "Could anyone help me install regular aim?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by GonZo1323 on 2006-08-27
:KS Gaim is nice and all but i need regular aim, because the file share feature makes it easy to get files off my other computer, rahter than setup a network.


THANX IN ADVANCE

---

### Post by Anonii on 2006-08-27
> **GonZo1323 said:**
> :KS Gaim is nice and all but i need regular aim, because the file share feature makes it easy to get files off my other computer, rahter than setup a network.


THANX IN ADVANCE


Its actually easy:

[http://www.aim.com/get_aim/linux/latest_linux.adp#install2](http://www.aim.com/get_aim/linux/latest_linux.adp#install2)

Download the debian package.

[http://channels.netscape.com/wrap/linker.jsp?floc=at_oslin_2_l7&ref=http://ftp.newaol.com/aimgen/380469/aim-1.5.234-1.i386.deb](http://channels.netscape.com/wrap/linker.jsp?floc=at_oslin_2_l7&ref=http://ftp.newaol.com/aimgen/380469/aim-1.5.234-1.i386.deb)

Get in the directory it downloaded, using the terminal, and use the following command:


sudo dpkg -i aim*.deb

Now, to open the program , you have to type:
/usr/local/bin/aim
again in the terminal.
(If you have problems, reply here. It installed fine, in my system.)

---

### Post by GonZo1323 on 2006-08-27
ok thanks im at work right now but to night when i get home i will try any problems ill post

---

### Post by GonZo1323 on 2006-08-29
i get this error message
gonzo@gonzo-desktop:~$ sudo dpkg -i aim*.deb
dpkg: error processing aim*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 aim*.deb
gonzo@gonzo-desktop:~$



so i opened da deb package and clciked installed and it acted like it worked but i cant get it 2 work help

---

### Post by GonZo1323 on 2006-08-29
anyone please?

---

### Post by aysiu on 2006-08-29
Maybe this might help?
[http://www.ifolder.com/index.php/HowTo:Enabling_Sharing_with_Gaim](http://www.ifolder.com/index.php/HowTo:Enabling_Sharing_with_Gaim)

---

### Post by GonZo1323 on 2006-08-29
lol i need help with regular aim

---

### Post by aysiu on 2006-08-29
In your original post, you said you wanted to do file sharing. That's why I linked to that. I don't know if there's an easy way to install AIM on Ubuntu.

The binaries they have for other distros (including Debian) do not work easily with Ubuntu, and the source file they have doesn't appear to be a typical ./configure make sudo make install one.

---

### Post by GonZo1323 on 2006-08-29
ya i was trying to get samba to work but it so much work

---

