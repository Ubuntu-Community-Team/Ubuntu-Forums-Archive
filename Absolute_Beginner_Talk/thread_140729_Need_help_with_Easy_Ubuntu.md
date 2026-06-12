---
title: "Need help with Easy Ubuntu"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by Shoriminimoe on 2006-03-06
I've just downloaded Easy Ubuntu but I don't know how to install it. Can anyone help me out?

---

### Post by paulmilliken on 2006-03-06
What is the name of the file that you downloaded.  In particular, what is the file extension eg. ".tar.gz" or ".tar.bz" etc?

---

### Post by Shoriminimoe on 2006-03-06
it is tar.bz

---

### Post by paulmilliken on 2006-03-06
[QUOTE=Shoriminimoe]it is tar.bz[/QUOTE]
Then it's a zipped (bz) tape-archive (tar) file.  First you will have to unzip it.  Open a terminal and move to the directory in which your file is stored (using the "cd" command).
Then type "tar -xzvf filename.tar.bz" (insert the appropriate filename here).  This will unzip the file and extract the contents to a folder.
Once you've done that, look inside the folder for a file called README or INSTALL.  These files should contain instructions on how to install and use the software.
Paul
ps.  To learn more about the tar command type "man tar" for the manual page.

---

### Post by Shoriminimoe on 2006-03-07
It worked. Thank you.

---

