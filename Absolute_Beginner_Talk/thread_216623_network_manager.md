---
title: "network manager"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Loki1989 on 2006-07-15
i found one but it comes as a tar biz file an dim wondering how to switch it over to .deb.

---

### Post by skale on 2006-07-15
Whatever the method is, it would be easier to just compile it yourself, 
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by catlett on 2006-07-15
When you see a tar file that means it is a compressed file.You need to extratc it and then install it. Usually tars need to be compiled but some have installers in them.
The first thing to do after downloading is to extratc the file. The easiest way is to right-click on it and select "extract here". Then you will have a folder. Open the folder and look for the "Read Me" or the "Install" text.
If you are lucky it will have an installer. Those are the easy ones. You just navigate to the folder in the terminal. That is done with the cd command.
A trick I use to make sure I enter the path to the folder correctly is, I enter cd in the terminal amd then hit space. Next I drag and drop the folder into the terminal. This will print out the folders path into the terminal. Hit enter adn you are virtualy in the folder.
If it is an installer you use ./ to run it. So if it is flashplayer_installer that you want to run you enter this```
 ./flashplayer_installer
``` If it says you need to compile it with configure and make then you first need the compiler package.
Install it with this ```
sudo apt-get build-essential
```
You will need to cd to the folder (just reiterating so you know you have to be in the folder to run configure etc). Then enter the 3 compiling comands 
```
./configure
```
```
make 
```
```
sudo make install
```There is no guarantee that a tar file will install. Your system may not have all the necessary libraries.
The only applications guaranteed to install are those in the repository. You can install them through the Synaptic Package Manager or through Apt-get in the terminal. The next best ones are debs. Thses usually do install but some don't since Ubuntu is a very modified debian system.
The least likely to install are tars so don't get discouraged if they don't all install.

---

