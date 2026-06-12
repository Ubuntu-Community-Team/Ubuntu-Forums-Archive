---
title: "&quot;not in zip format&quot; reaver-1.4.tar.gz on Backtrack 5R1"
date: 2012-02-25
forum: Any Other OS
---

### Post by davedaverson on 2012-02-25
Hi guys, this is my first post so be gentle ;)
I did research this question and did find somes suggestion, nothing helped me get past the error. I did run a "file reaver-1.4.tar.gz" and its listed as data, which doesnt seem right. I thought maybe the package was bad but i know it works. Im thinking im missing a step some where, i. Just really effing stumped on this one! 

Any help much appreciated. Ill try and update with the google code page.

---

### Post by josephmills on 2012-02-25
please open terminal 
then 
```
sudo apt-get --assume-yes
 install subversion 

```
```
svn checkout http://reaver-wps.googlecode.com/svn/trunk/ reaver-wps-read-only

```

then 
```
 cd reaver-wps-read-only/src/

```
then 
```
./configure 

```
then 
```
make
```
then 
```
sudo make install
```

that should do it. If you run into troubles paste the the error that you get thanks 

"on a side not maybee this thread should be moved to other distros ? "

---

### Post by davedaverson on 2012-02-25
Thanks for the response.
I ended up having to create a self-bootable USB stick so that I could use the apt-get features. My internet connection at this location puts me through web authentication, which uses Java; although java is enabled in firefox in Backtrack I cannot authenticate due to a java not being enabled error.

LONG STORY SHORT. I created the USB stick so I could follow the instructions and in the process solved my issue. I was able to successfully download reaver after updating the apt-get, using the CLI to launch the application.

 For some reason, maybe I didn't setup the live DVD properly. It seems to have some stability issues, could be my mistake. The USB is working great so far, and haven't run into any issues.

Thank you for the help tho Joeseph!

---

### Post by oldos2er on 2012-02-26
Thread moved to Other OS/Distro Talk.

---

