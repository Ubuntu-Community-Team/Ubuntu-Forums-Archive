---
title: "instaling software"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Shelldon on 2006-09-17
I'v recently swicthed to linux, but on an old machine. Problem is the machine is not connected to the internet. How do i now instal software? I'v tried the wiki's ect.. but everywhere i go everyone assumes that everyone will have an internet connection. I like ubuntu and really don't want to go back to windows, but without the internet connection, it seems i might not have a choice! please help someone!!!

---

### Post by Kilz on 2006-09-17
> **Shelldon said:**
> I'v recently swicthed to linux, but on an old machine. Problem is the machine is not connected to the internet. How do i now instal software? I'v tried the wiki's ect.. but everywhere i go everyone assumes that everyone will have an internet connection. I like ubuntu and really don't want to go back to windows, but without the internet connection, it seems i might not have a choice! please help someone!!!

What would you do with a windows machine with no operating system? The same advice is here. Download it to a machine that has internet and put it on some removable media. Then sneakernet it to the linux box.

---

### Post by aysiu on 2006-09-17
You might be interested in this project:
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

---

### Post by Shelldon on 2006-09-17
That's what I'm planning to do. I'm on a windows machine on the net. I'm wanting to download some programmes to a flash, then take it over to the ubuntu machine. But what do i download? i read a lot about dependencies, do i download those seperate? where do i put them?

---

### Post by aysiu on 2006-09-17
Does the Ubuntu live CD work (does it detect the internet connection) on that Windows machine?

If so, you can pop in the live CD to make sure you get the dependencies. Let's say, for example, that you wanted to install Konqueror on Ubuntu.

You'd pop in the live CD and type these commands: ```
sudo aptitude clean
sudo aptitude update
sudo aptitude install -d konqueror
``` Then, drag all the .deb files from /var/cache/apt/archives to your flash drive, copy them to the desktop of your Ubuntu machine and do ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by Shelldon on 2006-09-17
didn't know u could do that so i'l try now. wat does the 'aptitude' do?

---

### Post by aysiu on 2006-09-17
*aptitude* is a program that installs programs and their dependencies.

Basically, what you're doing is simulating the installation of a program on the live CD in order to get the program and its dependencies. The *-d* option just downloads the .deb installation files without actually installing them.

---

### Post by Shelldon on 2006-09-17
thanx! i'l give it a bash now, ta.

---

