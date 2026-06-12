---
title: "read/write support for NTFS partition in Ubuntu 7.04, how?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-04-22
Hi
Thank you for reading my post.
can you please explain how i can have NTFS read/write support in Ubuntu 7.04 ?

Thanks.

---

### Post by jiminycricket on 2007-04-22
Enable the universe repository, I don't think you need multiverse though [https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

Then type in a terminal:  sudo aptitude install ntfs-config

Then go to applications->System Tools->NTFS Config and make sure the checkboxes for external and internal device are ticked off.

---

### Post by RobsterUK on 2007-04-22
Also here's a good howto:

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by b0ng0 on 2007-04-22
Is it safe to enable NTFS read/write support in Feisty? I know before in Edgy people warned against it if your data was important as things could go wrong.

---

