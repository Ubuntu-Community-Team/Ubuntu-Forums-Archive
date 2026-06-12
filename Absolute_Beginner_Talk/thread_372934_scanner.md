---
title: "scanner"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by bratliff on 2007-02-28
What flat bed scanners does Ubuntu support? I can't find drivers for my HP 3970 scanjet.

bob

---

### Post by overdrank on 2007-02-28
> **bratliff said:**
> What flat bed scanners does Ubuntu support? I can't find drivers for my HP 3970 scanjet.

bob

Hi this may help you out!
[http://www.ubuntuforums.org/showthread.php?t=152762&highlight=scanjet+3970:](http://www.ubuntuforums.org/showthread.php?t=152762&highlight=scanjet+3970:))

---

### Post by bratliff on 2007-03-01
Thank you very much. THis is exactly what I am looking for. I installed sane, then downloaded the hp 3973 dep pakage and installed it. It finds the flatbed scanner. But when I run xsane image scanner I get this error msg: Failed to open device hp3900 Access to resource has been denied. Here is the dep install details. Is the DIdabling hp3900 backend in dll.conf a problem?

bob

bob@bobinpanama:/tmp$ sudo dpkg -i hp3900-sane_bin_0.7-1_i386.deb
Password:
(Reading database ... 116923 files and directories currently installed.)
Preparing to replace hp3900-sane 0.7-1 (using hp3900-sane_bin_0.7-1_i386.deb) ...
Disabling hp3900 backend in dll.conf
Unpacking replacement hp3900-sane ...
Setting up hp3900-sane (0.7-1) ...
Enabling hp3900 backend in dll.conf


bob

---

### Post by bratliff on 2007-03-03
ANYONE?

BOb

---

