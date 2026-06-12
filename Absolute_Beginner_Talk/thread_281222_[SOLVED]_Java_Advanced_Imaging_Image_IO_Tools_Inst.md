---
title: "[SOLVED] Java Advanced Imaging Image I/O Tools Installation help needed"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by jis on 2006-10-20
I want to use tiff files with a Java software ([http://jalbum.net](http://jalbum.net)) so I have to install Java Advanced Imaging Image I/O Tools. You can get them from [here]("http://java.sun.com/products/java-media/jai/downloads/download-iio-1_0_01.html"). After clicking "Installation" you can see the platform requirements: Red Hat 6.2 or subsequent compatible version of linux. Any change you can make this work on Ubuntu?

---

### Post by ubuntuuser on 2006-10-20
I don't know why they limit it to Redhat. I can't see why it should not work with ubuntu. Have you actually tried to install it? I would do it myself, but I'm not on a linux box right now.

---

### Post by Sef on 2006-10-20
Applications > Accessories > Terminal

sudo aptitude update

sudo aptitude install alien

sudo alien -i/path to file name

[How to Install Anything]("http://monkeyblog.org/ubuntu/installing/")

or

change to desktop where file resided (cd /path to where file resides)

then sudo alien -i file name

[Psychocats installing alien]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by jis on 2006-10-21
Sef, are you sure I could use alien? The file is not any rpm package. I am not sure which file to install, or should I install several files. I have both Sun Java(TM) Runtime Environment (JRE) 5.0 and Sun Java(TM) Development Kit (JDK) 5.0 installed. (I guess JAlbum is using JRE.) I have linux-386 kernel installed, but there is "linux-i586" in those file names that are on the Download page. Could there be compatibility problems? I suppose I should add sudo to the beginning of some of the commands given in the Installation Instructions. I can not do the CLASSPATH installation, because command setenv given in the instructions is not a command in my terminal.

---

### Post by jis on 2006-10-23
I found the project pages [here]("https://jai-imageio.dev.java.net/"), but have not yet solved the installation problem.

---

### Post by jis on 2006-10-24
I managed to install the tools.

---

### Post by jis on 2007-09-08
Case: Feisty, where sun-java6-jre package installed.
Follow the JRE installation instructions at [http://download.java.net/media/jai-imageio/builds/release/1.1/INSTALL-jai_imageio.html#Linux](http://download.java.net/media/jai-imageio/builds/release/1.1/INSTALL-jai_imageio.html#Linux)
Replace $JRE by /usr/lib/jvm/java-6-sun/jre
I suppose you have to run the  "$downloaddir/jai_imageio-1_1-lib-linux-$ARCH-jre.bin" command with sudo prefix to allow writing to $JRE.

P.S. You need to restart JAlbum to make it recognize the additional file types.

---

