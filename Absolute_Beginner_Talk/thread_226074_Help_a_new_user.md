---
title: "Help a new user?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by darknesfallz on 2006-07-30
Hello everyone, well yesterday i decided to switch from Windows 98SE to Linux Ubuntu. I love the way it looks and operates but im sorta stuck lolz.

My Wireless Adapter: TrendNet 802.11g TEW-424UB wireless adapter won't function under Linux. 

My friend recommended me a program called NdisWrapper to activate the wireless card but i can't seem to figure out how to install it! :D I used the root terminal (By luck) and extracted all the files into a folder, but now i am stuck at the part that says:

> This will create ndiswrapper-version directory. Change to that
directory and run
  make uninstall
  make
Login as root and run
  make install


How do i change to that directory using the Terminal? I tried doing what i do in MS-dos and typed: ndiswrapper-2.11/ but that didn't do anything lolz. Also, how do i run make install and uninstall?

 Any help would be appreciated! 

I hope i can make this wireless card work soon lolz. 

Regards,
Darknesfallz

---

### Post by taurus on 2006-07-30
You can change to a directory by using the "cd" command...

```

cd <directory>

```

---

### Post by darknesfallz on 2006-07-30
Hey this will work without a CD right? Lol im such a newbie when it comes to linux :( . Haha, And how do i do those run commands up there such as make install, and make uninstall?

Thnx,
Darknesfallz

---

### Post by taurus on 2006-07-30
Once you are done installing Dapper, you don't need to use the CD anymore so no need to insert it (unless it asks you to).  Before you build anything, you need to install gcc and some other goodies first.  From a terminal, do

```

sudo apt-get update
(use the same password that you log in with...)
sudo apt-get install build-essential

```
Now, I assume you downloaded "ndiswrapper-version.tar.gz" to ~/Desktop.  Do

```

cd ~/Desktop
tar xvzf ndiswrapper-version.tar.gz 
(remember to replace ndiswrapper-version.tar.gz with the actual name of the file!!!)
cd ndiswrapper-version
./configure
make
sudo make install

```

---

### Post by darknesfallz on 2006-07-30
hey. Thanx for your quick response. i really appreciate that. But, i have no way of connecting to the internet on linux. This is what i did to download the ndiswrapper. I just booted up windows 98 where my drivers work and downloaded the program and put it on a floppy disk.

Also, i can't make the files, here is a pic of what i was doing can someone please help me out on installing this lolz? :

[http://img60.imageshack.us/img60/7057/screenshotob0.png](http://img60.imageshack.us/img60/7057/screenshotob0.png)

---

### Post by richbarna on 2006-07-30
[quote=taurus;1318696]Once you are done installing Dapper, you don't need to use the CD anymore so no need to insert it (unless it asks you to).  Before you build anything, you need to install gcc and some other goodies first.  From a terminal, do

```

sudo apt-get update
(use the same password that you log in with...)
sudo apt-get install build-essential

``` 


Probably a silly question, but, how can he apt-get if he hasn't got an internet connection?


ndiswrapper_source.deb is on the Dapper cd, I think you can open synaptic uncheck all the internet sources, add the cd as a source and then apt-get ndiswrapper and ndiswrapper-utils.

---

### Post by darknesfallz on 2006-07-31
hey everyone. So i have moved from that ndiswrapper thing and from the cd i installed the ndiswrapper utility. Now i got a icon under administration and wireless devices right, i put my driver in there and it also detected my wireless adapter which was great! Now how do i connect lolz?

Here is a picture where i am stuck at:
[http://img324.imageshack.us/img324/6738/screenshot5ob3.png](http://img324.imageshack.us/img324/6738/screenshot5ob3.png)

A picture is worth a thousand words so i hope someone can help me out by it lolz! when i type my information in and the wep keys, it says its activating but i can't connect to the internet still!

---

