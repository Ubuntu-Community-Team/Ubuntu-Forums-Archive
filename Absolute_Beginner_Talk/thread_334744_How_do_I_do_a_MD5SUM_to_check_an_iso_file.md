---
title: "How do I do a MD5SUM to check an iso file?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Handssolow on 2007-01-09
I know it's easy when you know how but when you don't know there's a brick wall in front.
I want to know how to do a checksum test on some iso files I have downloaded onto my Ubuntu desktop but I'm not getting very far. They could be Ubuntu ones next time but for the moment its Puppy Linux that they are and I have also saved into office the checksum lines.
This is one place I found some information-
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

MD5SUM on Linux

Most Linux distributions come with the md5sum utility, so there is usually no need to install it. To check an iso file, first go the correct directory:

      cd download_directory

Then from within the download directory, run the following command.
      md5sum md5sum_file

Compare the hash (string on left), with the corresponding hash at UbuntuHashes. If they match, you're good to go. If they don't, try re-downloading the image file from another mirror.



In the terminal I've navigated so I'm in the Desktop directory
What do I enter next if for example I've got "ubuntu-6.10-desktop-i386.iso" sitting there?
How do I get an MD5 checksum?

---

### Post by taurus on 2007-01-09
Applications -> Accessories -> Terminal
```
cd ~/Desktop
md5sum ubuntu-6.10-desktop-i386.iso
```

---

### Post by Handssolow on 2007-01-09
Many thanks Taurus. [http://ubuntuforums.org/images/smilies/icon_razz.gif](http://ubuntuforums.org/images/smilies/icon_razz.gif)

---

### Post by Handssolow on 2007-01-09
Whoops

---

