---
title: "apps without internet"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by mynmiseman on 2007-05-29
i have downloaded a bunch of apps onto my removable disc and have tried to install them but 
cannot figure out how

the INSTALL readme files all talk jibberish to a newb like me but i think it has to do with the 
terminal?????? mabey?
 
any help... helps : ) 

also if you have any tips on using the terminal to do tasks i want to learn all i can about 
linux and ubuntu so any random facts help!

---

### Post by mynmiseman on 2007-05-29
ps. i don't have internet on the comp w/ linux i download them from my school

---

### Post by GrueTamer on 2007-05-29
[LinuxCommand]("http://linuxcommand.org") is a really helpful site for learning how the terminal works and stuff.  Plus, you can download the contents of the website in full, put them on your linux machine, and learn about the terminal without even having to use the internet.  If the install files still don't make sense, I would be willing to help out.

---

### Post by deadgobby on 2007-05-29
What kind of disc, HD, Flash, or CD? What type of apps? You do not need to list them all, just name a few. Are these apps in a Deb package formate, RPM, or Tar balls? You CD has apps on them and you can go to Synaptic and select add CD ROM. It will read off the CD for some apps. 
Gobby

---

### Post by mynmiseman on 2007-05-29
thanks! how do i get back to you if i don't get it? i'm new to the forums too

---

### Post by mynmiseman on 2007-05-29
adoura? i think is the one that's giving me crap and it's my mp3 in removable disk form and it's a tarballs type file

---

### Post by mynmiseman on 2007-05-29
no it's not adoura it's a music app

---

### Post by mocqueanh on 2007-05-29
You can download Debian package (the file with tail: .deb) a file you can install like Windows setup file, just double click on it.

Why apps on Linux must install with the command, not like Windows ?
Because there are many Linux distro, so many software companies dont pack source of apps for you like a Windows, you must use the command to install it from source.

Read the readme me file in the source of app (if the app you download is compress, decompress first).


open terminal and go to the folder contain the source (depend on where you store all your software source)

cd /home/cuong/Desktop/Softwarez/theApp

And type the command which intro in readme file, usually is:
sudo ./configure
sudo make
sudo make install


Some sources willl have other way to install, but the way above is often.

The tech behind the way to install from source is GCC, this will compile your source, by default, Ubuntu has it when you install Ubuntu, you can go to Synaptic and search gcc to know whether you Ubuntu had it or doesnt had.

---

