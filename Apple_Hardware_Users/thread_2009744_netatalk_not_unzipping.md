---
title: "netatalk not unzipping?"
date: 2012-06-24
forum: Apple Hardware Users
---

### Post by ARhere on 2012-06-24
Hey All,

Trying to use a drive on my Ubuntu Server as a NAS Time Machine.  I am following [**these**]("http://www.ubuntugeek.com/getting-timemachine-to-work-under-ubuntu-10-04-lts-os-x-lion.html") instructions except I downloaded the latest stable release of Netatalk using...
```
wget http://sourceforge.net/projects/netatalk/files/netatalk/2.2/netatalk-2.2.3.tar.gz
```

When I try to open/extract the file I get...
```
gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors
```

gunzip also returns an error.  Anyone get similar or see something I am doing wrong?
I am posting in the Apple section hoping someone has an easier solution.  I am running 10.04 and Lion.

-AR

---

### Post by dgharmon on 2012-06-24
> **ARhere said:**
> When I try to open/extract the file I get...
[code]gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

That's because that's only a link to the real file. Open [http://sourceforge.net/projects/netatalk/files/netatalk/2.2](http://sourceforge.net/projects/netatalk/files/netatalk/2.2) in a browser and click on the download link.

---

### Post by codemaniac on 2012-06-24
Hello ARhere ,

Please post the exact name of the tarball(zipped and archived filename) and the commands you have used to extract the contents .

---

