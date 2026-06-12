---
title: "Installing Apache2 on Ubuntu"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by rbradshaw on 2007-02-17
I am relatively new with Linux - just downloaded and installed the Ubuntu with desktop environment last month, however, I do like it! Now, I want to install Apache2, MySQL and PHP (I think they call it LAMP) on my Linux system. When I looked on Apache.org, I did not find any Linux specific software (I found Windows and Unix). For Linux, is the Unix version of Apache2 installed. I have not been able to find some good documentation. Any help would be appreciated. Thanks.

---

### Post by mcduck on 2007-02-17
No need to search web sites for packages, Ubuntu's package management does all the work for you: [How to install ANYTHING in Ubuntu]("http://cutlersoftware.com/ubuntuinstall/")

---

### Post by Tilex on 2007-02-17
These applications can be directly downloaded/installed via the "Synaptic Package Manager" in the menu->System, for they are very popular.
There are what you call "repositories" (a list of them can be found in your /etc/apt/sources.list file) where lots of programs are "stored" and waiting for you to download them.

You choose the packages, click "install", and everything will be up and running in a few minutes.

---

### Post by nhandler on 2007-02-17
You can also install it from a terminal with either of the following commands:
sudo apt-get install apache2
sudo aptitude install apache2

Either of the above commands will install apache2. You might want to make sure you have all your repositories enabled. That will give you access to all the packages you might want.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

---

### Post by rbradshaw on 2007-02-19
The Synaptic software package is great. I was able to download Apache 2. I then tested is using [http://localhost](http://localhost), however, now I want to configure Apache2. So, I downloaded documentation using Synaptic software package, but I don't know where the Apache2 document was placed on my filesystem.

Cheater told me to make sure repositories are enabled. What are repositories? Are they folders within the filesystem? Why do they have to be enabled? Why would I need to create more? Sorry for the beginner level questions. - Randy

---

