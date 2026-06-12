---
title: "Installing software from source"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by randomthings on 2006-08-25
Hi 
I need help installing software from source , can somebody explain to me how to do it ( with an example on any software please )
Thanks in advance .

---

### Post by Bachstelze on 2006-08-25
For relatively simple stuff, it narrows down to this :

1. Download and extract the source package.
2. Open a terminal and browse to the dir you just extracted.
3. ./configure
4. make
5. sudo make install

---

### Post by meng on 2006-08-25
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

---

### Post by benfindlay on 2006-08-25
You download the files through your internet browser as you would any file. Save it to a set location, say /home/downloads

Let us say the file I downloaded was called 123.tar.gz (Theres a good chance your file will be a .tar.gz file, just with a different bit before it, where I've put 123)


Open terminal (Applications>>Accessories>>Terminal)

type the following: 
```
cd /home/downloads
```
This changes to the relevant directory where you saved the file

```
tar -xfvz 123.tar.gz
```
This extracts the file into a folder called 123 (whatever the bit before the tar.gz is called for you)

```
cd 123
```
This changes you into the relevant directory for your extracted files

```
./configure
```
configures it for install

```
make
```
makes it ready for install

```
make install
```
Installs it

Provided you've got the right dependencies installed already, that should be all you need!

---

### Post by randomthings on 2006-08-25
Thanks alot guys .

---

