---
title: "Linux Equivalent of Sparse Image?"
date: 2008-12-18
forum: Apple Hardware Users
---

### Post by user12021 on 2008-12-18
Hello.
In Mac OS X, you can create a sparse image, which is a disk image that's the size of its contents, instead of its capacity.
[http://en.wikipedia.org/wiki/Sparse_image](http://en.wikipedia.org/wiki/Sparse_image)

How can I do something similar to this in Linux?

---

### Post by cyberdork33 on 2008-12-19
I don't know of many places that anything like this is done in linux. What exactly are you trying to do?

Just an idea, I think you can mount virtualbox disk images in ubuntu, so you might try creating an expanding hard drive image with virtualbox and see if it can use it the way you like.

---

### Post by user12021 on 2008-12-19
All I want to do is encrypt one folder. I tried using an encrypted zip, but you can still see the files inside, and you can't access the files inside from an external application.

---

### Post by cyberdork33 on 2008-12-19
> **user12021 said:**
> All I want to do is encrypt one folder. I tried using an encrypted zip, but you can still see the files inside, and you can't access the files inside from an external application.
I've used this. It is quite nice and cross-platform:
[http://www.truecrypt.org/](http://www.truecrypt.org/)

You can create an encrypted image file (with various types of encryption) and mount these images in the filesystem when you want to access the contents. Encryption occurs "on the fly". Not an exapnding image like you want, but will get the job done. It is also nice that it is cross platform so that you can take the image onto your mac or windows machine and open it there as well. You can even put the application on a thumbdrive to take it with you.

There is also this:
[http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html](http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html)

That just encrypts a folder on your Ubuntu System.

---

### Post by user12021 on 2008-12-19
Is the first one just an ISO image?

---

### Post by cyberdork33 on 2008-12-19
> **user12021 said:**
> Is the first one just an ISO image?
no, it is "truecrypt" format

---

### Post by evilempire on 2008-12-20
Truecrypt is really impressive stuff...

---

