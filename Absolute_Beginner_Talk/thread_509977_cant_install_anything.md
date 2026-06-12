---
title: "cant install anything"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by wehttamb on 2007-07-26
i have been running ubuntu for a while now but i cannot install anything anymore
when i try to install something i get an error about it not being able to download the package files

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-common_2.0.18-16ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-common_2.0.18-16ubuntu2_i386.deb)
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-gtk_2.0.18-16ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-gtk_2.0.18-16ubuntu2_i386.deb)
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gftp/gftp-text_2.0.18-16ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gftp/gftp-text_2.0.18-16ubuntu2_i386.deb)
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gftp/gftp_2.0.18-16ubuntu2_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gftp/gftp_2.0.18-16ubuntu2_all.deb)
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)




what is wrong?

Thanks

---

### Post by heimo on 2007-07-26
That mirror doesn't seem to respond. Change every instance of "au." to some other two letter country code in /etc/apt/sources.list or choose another country in Synaptic Package Manager. You can try which one works by copy-pasting the urls in your post to browser.

---

### Post by wehttamb on 2007-07-26
ok i will try that

---

