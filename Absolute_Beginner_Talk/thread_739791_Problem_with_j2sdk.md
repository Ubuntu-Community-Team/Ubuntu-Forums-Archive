---
title: "Problem with j2sdk"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by subhamay on 2008-03-30
I am on Ubuntu 6.06. 
Every time I run apt-get I receive the following message :
```
Setting up j2sdk1.4-doc (1.4.2.02-1ubuntu3) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    j2sdk-1_4_2-doc.zip j2sdk-1_4_0-doc-ja.zip j2sdk-1_4_2-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/j2se/1.4.2/download.html

now and download.  The file should be owned by root.root and be copied
to /tmp.
```
And the I am forced to abort the compilation. The links and the download instructions are not clear to me. Can I run apt-get to install j2sdk ?
Please help
:confused:

---

### Post by leg on 2008-03-30
You need to go to the[ Sun site]("http://java.sun.com/") and [download]("http://developers.sun.com/downloads/") the packages you want first. I do believe this is no longer an issue with later versions as Sun put Java open source so this process shouldn't be needed then.

---

### Post by superprash2003 on 2008-03-30
all you need to do is download the zip files mentioned and place it in the /tmp file, then ubuntu would install from there

---

