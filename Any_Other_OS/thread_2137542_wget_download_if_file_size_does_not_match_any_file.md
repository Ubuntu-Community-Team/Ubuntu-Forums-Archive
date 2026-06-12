---
title: "wget: download if file size does not match any file in folder"
date: 2013-04-21
forum: Any Other OS
---

### Post by Si1414 on 2013-04-21
I have the download link to pdf files, stored in links.txt

Some of the pdf files have same content (with different names, but same size). I do not want to download same content several times. That means I want to download all the files that have unique file size. 
Is it possible to do this with wget?

For example, 1.pdf is downloaded. Next, 2.pdf is checked for the size, if there is any file in the folder which is the same size of 2.pdf, then 2.pdf is not downloaded. Otherwise, it is downloaded to the folder, and 3.pdf is checked and so on.

Please let me know if you have any suggestions.

Thank you for your help.

---

### Post by Lars Noodén on 2013-04-21
I think the closest you might get to that with wget is [time-stamping](http://www.gnu.org/software/wget/manual/html_node/Time_002dStamping-Usage.html).  That will keep the date of the file the same locally as on the server.  It will then not download the file again if the timestamps match.

---

### Post by Si1414 on 2013-04-25
Thank you for your reply. Could you please explain more?

---

### Post by Lars Noodén on 2013-04-26
-N (or --timestamping) will prevent wget from downloading the file if the date and time match.  However, reading your post more closely you want to try to do that with files with different names.  Timestamping would only work with files that have the same name.

---

