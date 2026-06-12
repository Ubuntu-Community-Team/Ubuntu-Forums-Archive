---
title: "Ubuntu on VMware- vmware tools help!"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by rotwiler97 on 2006-08-16
I've installed the ubuntu on vmware and im having alot of trouble installing vmware tools. I'm new to this and I've downloaded all the updates and whatnot, and extracted the .tar and tried to mount it through the terminal but it doesnt work. I used sudo and my password but everytime i type vmware-install.pl it says command not found.. ive tried alot of things ive found on google but nothing has helped. Can anyone help me?

---

### Post by rbmorse on 2006-08-16
try

./vmware-install

note the "./" preceding the file name

---

### Post by pdub on 2006-08-16
It would help if you specified what version of VMware you are using, i.e. VMWare Workstation 5.5.2 or VMware Server 1.0, etc. Also, what is your host operating system, i.e. Window XP?

Let's assume Windows XP and VMware Workstation 5.5.2. 

There are .iso files located in a folder in the program files\vmware folder. You can use this .iso file as a CD-ROM drive inside you Ubuntu Virtual Machine by changing the setting for the CD-ROM and point it to the .iso. When your Ubuntu virtual machine is turned off, goto the VM menu and choose settins, then choose the CD-ROM and set it to use linux.iso. The CD will automatically mount when you load Ubuntu. Open a terminal, change to the newly mounted virtual CD and run the installer. Remember to type ./ as noted in the above comment.

---

### Post by rotwiler97 on 2006-08-16
yes i have added that, but no matter what it doesnt work. I've tried this guide that i found-

For the benefit of those who could use it. Below is a transcript of the session history showing successful installation of vmware tools on ubuntu guest.


myself@ubuntu:/$ cd /media
myself@ubuntu:/media$ ls
cdrom cdrom0 floppy floppy0
myself@ubuntu:/media$ cd cdrom
myself@ubuntu:/media/cdrom$ ls
VMwareTools-5.5.1-19175.i386.rpm VMwareTools-5.5.1-19175.tar.gz
myself@ubuntu:/media/cdrom$ sudo cp VMwareTools-5.5.1-19175.tar.gz /tmp
myself@ubuntu:/tmp$ sudo tar zxpf VMwareTools-5.5.1-19175.tar.gz 


it works up to the point, except once i get to sudo tar zxpf VMwareTools-5.5.1-19175.tar.gz       it errors out with going through all of the files and keeps saying that theres no such file or directory for every single file.    any help?

---

### Post by rotwiler97 on 2006-08-16
your right in your assumption, windows xp with ubuntu on vmware workstation5.5.2  ill try what you say and reply back with the results.

---

### Post by pdub on 2006-08-16
Try copying the file to your home folder instead.

Then use:

sudo tar xfz VMwareTools-5.5.1-19175.tar.gz 
change to the newly created folder
then run the installer

---

### Post by rotwiler97 on 2006-08-16
how do i change to the newly created folder (im guessing the home folder directory) i placed the extracted file into the home folder but i dont know what to enter in terminal to change to there. I'm not very experienced in using command lines (windows user.. duh)

---

### Post by pdub on 2006-08-16
Let's say your login name is joe, your home folder is likely /home/joe so

cd /home/joe

Make sure you copied the file to **your** home folder. Then use the tar command as shown above. Do an **ls** to see what the new folder name is, I cannot recall if it's VMwareTools-5.5.1-19175 or something else. Once you identify the folder just type **cd 'the name of the folder'** and hit **enter.**

i.e. **cd /home/joe/VMwareTools-5.5.1-19175**

Then do another **ls** and find the installer. Probably in green type.

Then use **./'the name of the install file'** and hit **enter.**

---

### Post by rotwiler97 on 2006-08-17
thanks alot, that was the exact thing i needed.

---

### Post by pdub on 2006-08-17
Cool.

I avoid the /tmp folder after having some problems of my own using it.

---

