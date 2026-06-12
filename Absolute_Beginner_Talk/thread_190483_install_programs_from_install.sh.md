---
title: "install programs from install.sh"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2006-06-06
recently got vlc media player have tried the apt-get commands and whatever else.how do u make the install.sh for vlc media player execute so u can install it that way.sorry to  be such a pain.

---

### Post by Ubuntuud on 2006-06-06
in a terminal:

```
cd /dir/the/file/is/in
./install.sh
```

---

### Post by spacey on 2006-06-06
To install VLC via apt, you must enable the the universe repositories.
In a terminal type:

sudo gedit /etc/apt/sources.list

Find the lines with the universe repositories and uncomment them.
Save the file and exit gedit.
In the terminal type:

sudo apt-get update
sudo apt-get install vlc

---

### Post by aysiu on 2006-06-06
Listen to spacey. This is even what [the VLC website says](http://www.videolan.org/vlc/download-ubuntu.html).

---

