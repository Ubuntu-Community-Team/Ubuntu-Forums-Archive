---
title: "problems with upgrade &amp; sleep"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Jalazmi on 2008-02-27
hi everyone..

first problem..
i have some problem with my computer.. i have ubuntu 7.10 and when i hibernate it then reopen my computer  they show me this notation which i attached it in hibpro,jpg  


and the other problem when i try to upgrade my system they tell me there are some problem and the error is

```
jalazmi@Jalazmi:~$ sudo aptitude safe-upgrade 
[sudo] password for jalazmi:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libxine1 libxine1-console libxine1-ffmpeg libxine1-gnome 
  libxine1-misc-plugins libxine1-plugins libxine1-x 
The following packages have been kept back:
  amsn ekiga kaffeine 
The following partially installed packages will be configured:
  linux-image-2.6.22-14-generic 
0 packages upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done    
```

so there someone can help me..?

---

### Post by JoshuaRL on 2008-02-28
Is there any specific reason you're using aptitude instead of APT?

And could you try:
```

sudo apt-get install --reinstall linux-image-2.6.22-14-generic

```

---

### Post by Jalazmi on 2008-02-28
thx JoshuaRL for your reply 

i try your code and i don`t think it make anything 

```
jalazmi@Jalazmi:~$ sudo apt-get install --reinstall linux-image-2.6.22-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

estell i can`t upgrade :)

just for remember you  or anyone can help me i have 2 problem one of them on the hibernate and i attach some picture to show you what the problem, and other one with upgrading 

i wait for your help..:)

---

### Post by JoshuaRL on 2008-02-29
With hibernate, I'm not sure I can help there.  But with the other thing, try:
```

sudo apt-get -f install
sudo dpkg-configure -a

```

---

### Post by Jalazmi on 2008-02-29
Joshua, 
same error with
```
sudo apt-get -f install
```

and with other command  i don`t found it

```
jalazmi@Jalazmi:~$ dpkg
dpkg                 dpkg-genchanges      dpkg-scanpackages
dpkg-architecture    dpkg-gencontrol      dpkg-scansources
dpkg-buildpackage    dpkg-name            dpkg-shlibdeps
dpkg-checkbuilddeps  dpkg-parsechangelog  dpkg-source
dpkg-deb             dpkg-preconfigure    dpkg-split
dpkg-distaddfile     dpkg-query           dpkg-statoverride
dpkg-divert          dpkg-reconfigure     dpkg-trigger
jalazmi@Jalazmi:~$ sudo dpkg-configure -a
[sudo] password for jalazmi:
sudo: dpkg-configure: command not found

```

---

### Post by Jalazmi on 2008-02-29
i try this command
```
 sudo dpkg --configure -a
```

and i got same error.. so please how to solve this problem cuz i dono what to do

---

### Post by Jalazmi on 2008-03-02
no one can help me ..?

---

