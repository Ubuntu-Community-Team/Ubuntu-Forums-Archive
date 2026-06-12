---
title: "Can't delete testphp.php"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by foy1der on 2007-03-20
Hi All,
I'm brand new to the forums and to Linux so I figured this is the perfect place for me. My problem is that I used [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_PHP5") guide to install php5. Everything worked out find except when it came to deleting testphp.php after I was finished with it. It tells me that I don't have permission to delete the file. 
Thanks in advance for the help.

---

### Post by etank on 2007-03-20
The file was created with root privileges. Just run```
sudo rm testphp.php
```in the directory where it is located.

---

### Post by foy1der on 2007-03-20
I'm not quite sure how to change directories. Would this work as well?
> sudo rm /etc/php/testphp.php

---

### Post by Paul41 on 2007-03-20
> **foy1der said:**
> I'm not quite sure how to change directories. Would this work as well?

Yes, this will work.

To change directories:
```
cd your_directory
```

---

### Post by foy1der on 2007-03-20
Thanks for all the replies. I didn't think that it would be this fast. I guess I am used to other slower communities.

---

