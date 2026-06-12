---
title: "help downloading..."
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-05-05
Is there a way of downloading this withouth being on Ubuntu? I mean download it through windows and then install the packages in ubuntu....

Step 3 - Prepare the Linux build environment

You will need to install the essential build files to compile the driver: 
user@ubuntu:~$ sudo apt-get update
user@ubuntu:~$ sudo apt-get install build-essential

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.) 
user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

---

### Post by Sef on 2007-05-05
Check out [http://packages.ubuntu.com]("http://packages.ubuntu.com")

---

### Post by Jorge32 on 2007-05-06
ok thanks!

---

