---
title: "Expanding RAR files help"
date: 2007-02-14
forum: Apple PPC Users
---

### Post by maniacrobbins on 2007-02-14
I'm using ubuntu with a PPC PowerBook and I need to know a good program to unarchive files (especially RAR).  UnArchiver (or whatever program comes with Ubuntu) doesn't work along with XArchiver.  they both say tha the file format is not supporeted.  Can any suggest another RAR expanding program?

Thanx

Dave

---

### Post by renzokuken on 2007-02-14
sudo apt-get install unrar

then the right click "extract here" will work fine as will the default GUI archiver

---

### Post by maniacrobbins on 2007-02-14
thanx.  thats works

---

### Post by AGSzabo on 2007-02-16
there is no "unrar" package. its not free. there is only an "unrar-free" package but that cannot handle rar 3.0 archives.

btw, what to install so that even LHA files can be unpacked with "extract here"?

---

### Post by renzokuken on 2007-02-16
7-zip may be? i think its available for linux

---

### Post by AGSzabo on 2007-02-16
there is no such thing as 7-zip in the synaptic manager.

---

### Post by renzokuken on 2007-02-16
just because its not in Synaptic, doesnt mean it doesnt exist......

you can get it from [www.7-zip.org/download.html](www.7-zip.org/download.html) , you'll just have to install it yourself

there is a debian package available at the bottom, you can install it using

```
sudo dpkg -i name_of_file.deb
```

alternatively look here [http://www.linux.org/apps/AppId_476.html](http://www.linux.org/apps/AppId_476.html)

---

### Post by darrenm on 2007-02-16
```
sudo apt-get install rar
```

you need the multiverse repo enabled.

then type ```
rar e filename.rar
```

---

### Post by maniacrobbins on 2007-02-16
People.  I got this.  If you want to discuss in here, go ahead, but I HAVE FIGURED THIS OUT.  Renzokuken told me on the second post.  thanx anyway though.

---

### Post by maniacrobbins on 2007-02-16
People.  I got this.  If you want to discuss in here, go ahead, but I HAVE FIGURED THIS OUT.  Renzokuken told me on the second post.  thanx anyway though.

---

