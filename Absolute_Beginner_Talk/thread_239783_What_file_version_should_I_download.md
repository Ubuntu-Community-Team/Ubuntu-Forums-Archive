---
title: "What file version should I download?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by NorseDude on 2006-08-19
Every time I find something I want to download, I get the choice to download multiple versions like source, dab and what not. As I have no experience with Linux at all, what should I download and how do I install it? Thanks.

---

### Post by hopstah on 2006-08-19
go for deb every time.  you don't want to get into compiling from source yet (if ever) and ubuntu is a debian based system, so the .deb packages are best.

to install them through a terminal, type (sudo) dpkg packagename and you'll be all set

---

### Post by catlett on 2006-08-19
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) This will give you a good run down of installation procedures.

You should always search Synaptic Package Manager for a program first. Anything in there will install on your system without an issue. Go to the top and enter under System<Administration<Synaptic Package Mnager. Just select search and enter a keyword or a specific programs name.

If you do not find what you are looking for and go online to a site to get a program, look for .deb files. Ubuntu is Debian based and .deb's are debian packages. Those are installed with "gdebi" package installer. You can select open with gdebi from the download dialogue box or download and double click.

the last thing you want is source code. These are the .tar files. They are sopurce code that needs to go through a compiler to become a binary package. Sometimes there is no other option but all sourtce does not install on your system after compiling. It has do to with all the different versions of linux and the fact that they have different base libraries. So source that compiles and runs on one distro may not on another.
If you are going to try installing from a tar, you need the compilers first
```
sudo apt-get install build-essential
``` Then download the tar file to your desktop. Right click on the file and select "extract here". That will give you a folder.
Now is the "kinds of" complicated part. You must be in the folder virtually. You do this by changing directories with the cd command. So to be in the folder flashinstaller that is on your desktop enter 
```
cd Desktop/flshplayerinstaller
``` When you hit enter they terminal line will change from 
```
catlett@ubuntu:~$ 
```   to ```
catlett@ubuntu:~/Desktop/flshplayertinstaller$
``` Now that you are in the folder, there are 3 commands to issue for compiling
```
./configure
```
```
make
```
```
sudo make install
```

Don't get too discouraged about tars not installing. Synaptic is the best source for apps but debs are almost a sure thing as well.

The site I posted does a better job of explaining.

---

### Post by NorseDude on 2006-08-19
Thanks. But do I have to install everything in the root partion? I have three partions on the hard drive. One root, one swap and one for other things. I created the root and swap partions as small as they could be, so the root partion is already 95% full before I even installed anything on it. Can't I install something to the other partion? The root partion has a few hundred MB left, the other one about 30GB. :)

---

### Post by catlett on 2006-08-19
Yes you can but it has to be a linux compatable partition. You should use ext2 or ext3 for linux. Preferably ext3. You can't use ntfs and fat has issues. There are others less popular but for your purpose stick to ext3.
Do you have space for another partition? If not all apps will be installed to your root partition if you haven't made other partitions.

---

### Post by NorseDude on 2006-08-20
As I said, I have one for root, one for swap and one for everything else includig home directories. The root and swap partitions are as small as they had to be, so the root partition is almost full after the installation. The other partition (the home dir one) is of course ext3.

I have another partition with WinXP, and after some work I managed to make it recognize the linux partitions, so I could work with the linux partitions in windows just like any windows partition. I'm proud. ;)

---

