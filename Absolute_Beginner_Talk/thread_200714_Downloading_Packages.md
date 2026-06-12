---
title: "Downloading Packages"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by jalfordvidman on 2006-06-20
I know that you can use apt-get to install programs and packages. I also know that this only works if you're connected to the internet (something I am working on). I want to know if I can download a package/program on an XP box, save it to my USB drive and then open it in Linux. Is this at all possible?

---

### Post by richbarna on 2006-06-20
Yes (Look at my sig "Install Anything")

---

### Post by givré on 2006-06-20
You could install package easyly by just double click them with gdebi, or use dpkg -i in a terminal

---

### Post by jalfordvidman on 2006-06-20
Well, I looked at the "Install Anything" in your sig, richbarna, but that doesn't exactly help me.....yet. I can connect to the internet through a Windows XP box. Therefore, I could theoretcially search for and download packages, correct? I've done some searching on my own, but I can't find any way to download a package, I think if I could do this, then I could do a little sneakernet action and get the package to my Linux box - which is *not* connected to the internet.

---

### Post by taurus on 2006-06-20
Yes, you can download whatever you want under XP, copy it to a USB memstick, transfer it to Linux.  Now, it depends on what type of file you are talking about.  If it is a .deb, then you just install it with
```

sudo dpkg -i <filename>.deb

```
But if it is a .tar.gz or tar.bz2, then you need to unpack it, build it, and install it as
```

tar xvzf <filename>.tar.gz
-or-
tar xvjf <filename>.tar.bz2
cd <filename>
./configure
make
sudo make install

```
If you can be a little more specific what file you want to do, the this whole thing would get much simpler!!!

---

### Post by jalfordvidman on 2006-06-21
Well, I'd like to install Wine, but when I go to the website to try and download it, I get to this page ([http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)) and am stuck......wait, oh, there's a little link at the bottom for the packages. My bad. But, how can I manually download from the repositories (under XP) in case I can't just go to a website and download?

---

### Post by woot on 2006-06-21
you're probably looking for this:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Has all the packages apt-get can give you (well those in the normal repositories)

---

### Post by jalfordvidman on 2006-06-21
I downloaded Wine and used the sudo dpkg command in the Terminal. It appeared to install, but now I can't find it. And about the Ubuntu packages URL, I found the download site for winesetuptk and it lists a couple dependencies. How can I find out if I have the other packages related to Wine?

---

### Post by rowanparker on 2006-06-21
You need to run ```
winecgf
``` after installing Wine.

Try running ```
wine notepad.exe
``` and see what happens.

Rowan.

---

