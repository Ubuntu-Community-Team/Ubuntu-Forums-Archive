---
title: "questions about installing/updating sw"
date: 2005-05-18
forum: Absolute Beginner Talk
---

### Post by waft on 2005-05-18
hi. i am completely new to linux and have some questions
1. how do i install deb package which i downloaded?
2. how can i convert rpm packages to deb? i just know alien can do that but i dont know how to do that
3. i have problems with updating. firefox1.0.1 is installed on my computer and ubuntu update manager says the new version ishoul update to is firefox 1.0.2. current version of fx is 1.0.4. i have the same problem with mozilla.

thx.

---

### Post by mostwanted on 2005-05-18
[QUOTE=waft]hi. i am completely new to linux and have some questions
1. how do i install deb package which i downloaded?
2. how can i convert rpm packages to deb? i just know alien can do that but i dont know how to do that
3. i have problems with updating. firefox1.0.1 is installed on my computer and ubuntu update manager says the new version ishoul update to is firefox 1.0.2. current version of fx is 1.0.4. i have the same problem with mozilla.

thx.[/QUOTE]

1. $ dpkg -i myDeb.deb

2. $ alien -i myRpm.rpm

3. I'm not sure what your problem here is, sry :) But Ubuntu doesn't officially release new versions of programs until the next release. The security fixes in FF1.0.4 are instead backported, which doesn't make much sense since it was a security update anyway. But that's how it is.

You can always add the Ubuntu Backports repositories (see tab on the top of the page) to get new versions of apps.

---

### Post by waft on 2005-05-18
thanks. you really helped me

---

