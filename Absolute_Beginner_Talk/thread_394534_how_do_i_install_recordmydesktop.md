---
title: "how do i install recordmydesktop?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2007-03-27
hey guys, i need somthing to record my desktop. i saw a post for recordmydesktop but im not to sure on how to install it. any help would be great, thanks.

---

### Post by zvacet on 2007-03-27
[http://linux.softpedia.com/get/Multimedia/Video/recordMyDesktop-15059.shtml]("http://linux.softpedia.com/get/Multimedia/Video/recordMyDesktop-15059.shtml")

---

### Post by thelinuxguy on 2007-03-27
> **da1nonlymikeo said:**
> hey guys, i need somthing to record my desktop. i saw a post for recordmydesktop but im not to sure on how to install it. any help would be great, thanks.

I downloaded the .tar.gz file from [http://sourceforge.net/project/showfiles.php?group_id=172357&package_id=202906&release_id=487972](http://sourceforge.net/project/showfiles.php?group_id=172357&package_id=202906&release_id=487972)

After extracting the contents, the INSTALL file outlines the steps you need to take to install it on your system. Some lines from this file are:

```

~$ gzip -d gtk-recordmydesktop-x.y.z.tar.gz
~$ tar -x gtk-recordmydesktop-x.y.z.tar
~$ cd gtk-recordmydesktop-x.y.z
~$ ./configure --prefix=/usr/
~$ make
~$ sudo make install

```


A good article on installing software on Linux, in general, is available at [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

Hope this helps.

---

### Post by cowlip on 2007-03-27
recordmydesktop is in the Feisty repos...maybe you can try to install from here too?  [http://packages.ubuntu.com/feisty/graphics/recordmydesktop](http://packages.ubuntu.com/feisty/graphics/recordmydesktop) (just take the deb files, not the repository)

This also has .deb packages: [http://recordmydesktop.sourceforge.net/downloads.php](http://recordmydesktop.sourceforge.net/downloads.php)

---

### Post by da1nonlymikeo on 2007-03-27
i downloaded the tar.gz but then at the next step...

mike@mike-laptop:~$ gzip -d gtk-recordmydesktop-0.3.3.1.tar.gz
gzip: gtk-recordmydesktop-0.3.3.1.tar.gz: No such file or directory


but i saved that exact file to my desktop?

---

### Post by johnc4510 on 2007-03-27
You must first navigate to the desktop as shown in the example below. Note: insert your user name where /johnc is.

johnc@Feisty:~$ cd /home/johnc/Desktop
johnc@Feisty:~/Desktop$

---

### Post by da1nonlymikeo on 2007-03-27
alright now on the second step i do..

mike@mike-laptop:~/Desktop$ tar -x recordmydesktop-0.3.3.1.tar


 but that just gives me blank terminal and dosent do anything.

---

### Post by lamalex on 2007-03-27
thats ok, look your desktop, you should have a folder. and it's a good idea to do tar -xvf filename.tar.gz that will give you lots of output so you know it's working.

---

### Post by da1nonlymikeo on 2007-03-27
theres no folder:confused:

---

### Post by johnc4510 on 2007-03-27
mike@mike-laptop:~/Desktop$ tar -x recordmydesktop-0.3.3.1.tar

It looks like you typed the file name incorrectly. Should have .gz at the end

---

### Post by thelinuxguy on 2007-03-27
> **da1nonlymikeo said:**
> theres no folder:confused:

Download the .tar.gz file again.
Open it in the file roller GUI by double-clicking the .tar.gz file and then extract it to some place where you can find it. The GUI should reduce the initial confusion.

---

### Post by MrKlean on 2007-03-27
You can also use the *  ... in other words the file name record* will work too ; )

---

### Post by blockcipher on 2007-03-27
I followed this.

[http://www.ubuntuforums.org/showthread.php?t=294605](http://www.ubuntuforums.org/showthread.php?t=294605)

---

