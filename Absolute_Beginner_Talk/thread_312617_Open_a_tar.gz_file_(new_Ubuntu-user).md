---
title: "Open a tar.gz file (new Ubuntu-user)"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2006-12-04
Hi

I am just trying out the Ubuntu live cd 6.06. It works great. Now I want to try out a Flash game called N (Ninjagame). You can download it here:

[http://www.harveycartel.org/metanet/downloads.html](http://www.harveycartel.org/metanet/downloads.html)

Now the problem is: How do I open and play it?

I have tried [this guide ]("http://monkeyblog.org/ubuntu/installing/"). It says, that I go into the folder with the file, and I type "./configure" and then make.

"
ubuntu@ubuntu:~/Desktop/spil$ cd /home/ubuntu/Desktop/n_v1linux
ubuntu@ubuntu:~/Desktop/n_v1linux$ ./configure
bash: ./configure: Ingen sådan fil eller filkatalog
ubuntu@ubuntu:~/Desktop/n_v1linux$ make
bash: make: command not found
ubuntu@ubuntu:~/Desktop/n_v1linux$"

Aren't the program supposed to make an installer, when I type "make"?

Please, help this Linux newb!

---

### Post by Tomosaur on 2006-12-04
It's a flash game? I very much doubt you'll need to use make then. You do, however, need to unpack the .tar.gz file:
```

tar -zxvf myFile.tar.gz

```
this should unpack the contents into a new directory. Just cd into there and see what's what. A flash program will normally just run provided you have the flash player installed (which I don't the liveCD has btw)

---

### Post by Wikzo on 2006-12-04
Can't I just right click and "Extract to ..."? :)

Ok, if the live cd can't play Flash, that's the reason why nothing happens. Thanks :)

---

