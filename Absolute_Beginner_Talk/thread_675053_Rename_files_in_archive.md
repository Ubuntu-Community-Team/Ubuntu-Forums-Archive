---
title: "Rename files in archive"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Blagomir on 2008-01-22
Hi, how can i rename files in the .zip archive without unzipping the original .zip file ?

---

### Post by Black_Heart on 2008-01-22
the only way i think you could do that is with a archive program like winrar or 7-zip. you can get them here:



winrar: [http://www.rarlab.com/](http://www.rarlab.com/)

7-zip:    [http://www.7-zip.org/](http://www.7-zip.org/)


just dl the trials unless you want to pay for it :) they only have windows versions, so you'll have to get wine to run them:guitar:

---

### Post by Paul820 on 2008-01-22
rar and 7zip are available from the repositories, no need to run them in wine.

---

### Post by Paul820 on 2008-01-22
If you have **file roller** installed, when you click on the archive file roller will open and then you can right-click on the file and choose rename.

---

### Post by stchman on 2008-01-22
> **Black_Heart said:**
> the only way i think you could do that is with a archive program like winrar or 7-zip. you can get them here:



winrar: [http://www.rarlab.com/](http://www.rarlab.com/)

7-zip:    [http://www.7-zip.org/](http://www.7-zip.org/)


just dl the trials unless you want to pay for it :) they only have windows versions, so you'll have to get wine to run them:guitar:

File Roller can easily pack and unpack .rar and .7z files with the proper packages.

```
sudo apt-get -y install rar unrar p7zip p7zip-full
```

You are good to go then.

---

### Post by rosegarden78 on 2008-01-22
I recall Windows XP having ZIP-folder browsing built-in.  Doesn't Ubuntu last time I checked?  I thought by definition to view a ZIP file (a form of compression) *requires* that the file be decrypted by a file manager to view and edit the contents.

---

