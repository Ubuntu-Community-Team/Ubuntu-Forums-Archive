---
title: "Eclipse 3.0.1!?"
date: 2004-11-02
forum: Apple PPC Users
---

### Post by berndtj on 2004-11-02
So I found some instructions on recompiling some parts of the linux x86 version to get it to work on ppc.  I am getting tons of pango related errors on compilation.  I think I have pango installed correctly, but I may be wrong.

Has anyone gotten eclipse running on Ubuntu?  If you have, I would love to hear how it went.  Hell, maybe you can just send me the recompiled files.

Berndt

---

### Post by stereo on 2004-11-03
thats a really good idea. i bet we'll find a place for the eclipse-linux-ppc binaries. perhaps in a ubuntu-repository?  that would be nice, because no other ppc-distro has them.

---

### Post by khc on 2004-11-03
I was able to build it, I can probably look at my bash history to post a transcript of what I've done once I get home.
I can also upload my build somewhere if there's interest (I wasn't able to get swt-mozilla to compile, but I've never had a problem with it missing).

---

### Post by stereo on 2004-11-04
oh yes, there is interest ;o)

---

### Post by SyL on 2004-11-04
[QUOTE=][/QUOTE]
 You can find here a builded eclipse 3.1 :
[http://fdik.org/eclipse-ppc/](http://fdik.org/eclipse-ppc/)

It's not working for me, because of the IBMJava2-ppc-142

---

### Post by khc on 2004-11-04
Sorry I am a bit busy right now (have an exam tonight), for now I will include the link that I used, you will need to install some header packages for it to work, I will post those tonight after the exam.
[http://www.rexi.org/linux/eclipse-ppc.html](http://www.rexi.org/linux/eclipse-ppc.html)

---

### Post by khc on 2004-11-05
Here's a transcript of what I've done. Keep in mind that there's a lot of copying and pasting, so I might have missed something, but this and the link I provided earlier should get you a build. I am also uploading my build, and will post again when it's done.

You will want to subsitute some of the path here (/usr/src/khc, etc)

```
sudo apt-get install libgtk2.0-dev
sudo apt-get install libgnome2-dev
sudo apt-get install gcc
sudo apt-get install libxtst-dev
sudo apt-get install libgnomeui-dev
sudo apt-get install libxt-dev
sudo apt-get install csh

wget http://eclipse.mirrors.tds.net/downloads/drops/R-3.0.1-200409161125/eclipse-SDK-3.0.1-linux-gtk.zip
unzip eclipse-SDK-3.0.1-linux-gtk.zip
cd eclipse/
cd plugins/org.eclipse.platform.source.linux.gtk.x86_3.0.1/
cd src/org.eclipse.swt.gtk_3.0.1/ws/gtk
unzip swt-pisrc.zip
unzip swtsrc.zip
# change JAVA_HOME to point to your java installation.
# keep in mind that the first JAVA_HOME is for AMD64
vi make_gtk.mak
sh build.sh
cp -p *so /usr/src/khc/eclipse/plugins/org.eclipse.swt.gtk_3.0.1/os/linux/x86
cd /usr/src/khc/eclipse/plugins/org.eclipse.platform.source_3.0.1/
cd src/org.eclipse.platform_3.0.1/
unzip launchersrc.zip
cd library/gtk/
csh build.csh
cp -p eclipse /usr/src/khc/eclipse

```

---

### Post by khc on 2004-11-05
Actually the whole build turns out to be 80+MB compressed, and I don't really want to host such a big file. But if you follow the instructions, you should be able to build it yourself.

---

