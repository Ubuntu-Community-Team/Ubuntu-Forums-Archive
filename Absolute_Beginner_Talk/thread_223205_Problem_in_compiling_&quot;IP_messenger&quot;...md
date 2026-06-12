---
title: "Problem in compiling &quot;IP messenger&quot;.."
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-07-26
Hello everyone,
I want to install "IP messenger" in ubuntu. I have downloaded its source-code (i could not find any binaries/package). 
To install..i followed the ubuntu wiki guide.
./configure returns a long list of OKs followed by this error:

checking for gtk-config... no
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: GTK not installed

Im a linux noob, and i dont know what to do now.. Can someone please help me out on this? what am i supposed to do?

It would be fantastic if someone knows an alternative to IP-messenger (free) which is compatible with it.


Thanks in advance...

---

### Post by croak77 on 2006-07-26
Looks like you need libgtk1.2 and libgtk1.2-dev.

---

### Post by Sef on 2006-07-26
Have you downloaded build-essential?

To compile, build-essential needs to be installed.

Applications > Accessories > Terminal

sudo apt-get update

sudo aptitude install build-essential

---

### Post by kitt on 2006-07-26
Yes, i have installed build-essential.

Btw..isnt GTK something to do with Gnome environment?? So whats exactly the problem here..??

---

### Post by Sef on 2006-07-26
I found this: 

> Package: xipmsg (0.8088-1) [universe]
A pop up style message communication software

IP Messenger is a pop up style message communication software for multi platforms. It is based on TCP/IP(UDP). Xipmsg is the X11 version of IP Messenger. It can communicate with IP Messengers for Windows/MacOS. 

Is this what you are looking for?  

If so, (if universe is added, if not add it first)

1) open the terminal

2) sudo apt-get update

3) sudo aptitude install xipmsg

---

### Post by croak77 on 2006-07-26
You need the headers which are in the "***"-dev packages. 

"checking for GTK - version >= 1.2.0... no"

That means install libgtk1.2-dev.

---

### Post by kitt on 2006-07-26
> **Sef said:**
> I found this: 



Is this what you are looking for?  

If so, (if universe is added, if not add it first)

1) open the terminal

2) sudo apt-get update

3) sudo aptitude install xipmsg

Thanks a lot..i did as instructed..but im not able to find the program after installation...does that mean theres some problem with the installation..or am i not able to find it?

---

### Post by RajivNair on 2006-08-08
the executable is in /usr/bin/X11R6/xipmsg.u can make an shortcut menu by using alacarte.

---

### Post by kitt on 2006-08-16
Thanks everyone,
btw..where are the programs installed when i install them from source? i have make install'ed gipmsg ..

---

### Post by kitt on 2006-08-17
Someone please help me with this!

---

