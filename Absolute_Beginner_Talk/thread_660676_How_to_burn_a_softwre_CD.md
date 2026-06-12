---
title: "How to burn a softwre CD?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by abk123 on 2008-01-07
Hello everyone!!      (and forgive me 4 poor english)

I want to know how to burn a cd which contains the software which i have preinstalled in ubuntu using sudo apt-get install <package>

I have another computer which has no internet connection.It cannot be connected to any home network or anything.So i have to put the software in a CD and then install them on the isolated computer.How do i do that?

I am an absolute begginer so i dont know any command line things.Please gine me the commands which i can type into the terminal.

Thank you!:)

---

### Post by wolfen69 on 2008-01-07
aptoncd [http://aptoncd.sourceforge.net/download.html](http://aptoncd.sourceforge.net/download.html) will allow you to put your programs on a cd to use on any computer. download the .deb file [http://downloads.sourceforge.net/aptoncd/aptoncd_0.1-1_all.deb](http://downloads.sourceforge.net/aptoncd/aptoncd_0.1-1_all.deb) and just click to install,

---

### Post by jeffus_il on 2008-01-07
If it's only one program you can copy the downloaded package form the 
/var/cache/apt/archives/
directory.

Burn it to a cd or use and other copy method and then install on the other computer by double clicking on the deb file in nautilus and using gdebi (probably automatic) to install.

---

### Post by zipperback on 2008-01-07
[http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

- zipperback
:popcorn:

---

