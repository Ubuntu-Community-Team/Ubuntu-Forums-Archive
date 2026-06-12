---
title: "Installing Sunbird, ./configure: no such file or dir"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Zeke73SG on 2006-10-14
This is my first post here. I am still in the first month of using Linux over Windows and things are going well, but this is just beyond me. I am trying to install mozilla sunbird from a tarball. I unpacked it, and then when I run ./configure, from inside the sunbird directory, i get "bash: ./configure: No such file or directory". Is there a script in the sunbird directory that I am supposed to be running instead of ./configure? The readme that came with it isn't really telling me anything, it seems to just be generic instructions for installing mozilla. I have installed build-essential. If anyone knows of an installer for sunbird that would allow me to circumvent this issue for the time being, that would be awesome. I do feel the need to figure this out though. Thanks.

---

### Post by NeoLithium on 2006-10-14
If you're in the directory that you unpacked the tarball in; try 
```

sudo ./configure

```

It probably requires superuser as it installs system-wide

---

### Post by Beggar Su on 2006-10-14
I don't think sunbird has an installer, you just launch sunbird from its folder by typing

(if downloaded to your home folder):

```
/home/$usr/sunbird/sunbird
```

---

### Post by Zeke73SG on 2006-10-14
I just decided to run it as is out of the folder in my home directory. I don't really like it there but I don't know what else to do with it. The important thing is it works. Thanks!

---

### Post by taurus on 2006-10-14
If you don't like having it in your $HOME, then move it to where you want it to be and link to it!!!

---

### Post by Perfect Storm on 2006-10-14
You could hide it (by putting a . infront of the folder name) and making a launcher pointing to sunbird.

eg. /home/<username>/.Sunbird

---

