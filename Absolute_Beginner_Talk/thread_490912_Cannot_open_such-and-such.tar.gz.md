---
title: "Cannot open such-and-such.tar.gz"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Amablue on 2007-07-03
Whenever I download .deb or .tar.gz files archive manager acts funny. I go to open the file and I get this:

> The filename "bcm4318.tar.gz" indicates that this file is of type "tar archive (gzip-compressed)". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

Why don't my files just open like they should? This has been happening with all my files.

---

### Post by lisati on 2007-07-03
If it was a file you downloaded, the download might have failed.

---

### Post by GeeZor on 2007-07-03
might want to try the save as function to make sure you use the BIN mode (on FTP-servers) 
also maybe you have to chmod the file to make it executable

rwx
421

chmod 777 <downloadedfile>

good luck

---

