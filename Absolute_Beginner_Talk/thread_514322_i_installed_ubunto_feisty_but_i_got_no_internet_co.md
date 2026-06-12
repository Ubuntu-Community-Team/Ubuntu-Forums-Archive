---
title: "i installed ubunto feisty but i got no internet connection to update"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by SilverBridge on 2007-07-31
** i need ur help , i installed Ubunto feisty , i downloaded it from the main website ,but i got no internet connection  , i installed it with no internet connection ,so i can`t get any updates , i tried to download the required updated packages to enable Multimedia in my Ubunto , but always it tells me not enough dependicies , or library thing , so , i tried to update it through Third party device , but couldnt , so i need some help , if any of u can provide me with an updated version , updated packages , all updated and upload it so us over here , then we can download it and update it through third party device , so i need ur help  , will it work this way ? or is there any way to update my Ubunto without an internet connection ? **

---

### Post by jba6511 on 2007-07-31
are you trying to get a connection to the web? is that what you are asking? If so, how? wireless, wired, etc. How were you able to download the ubunut live cd?

---

### Post by mikewhatever on 2007-07-31
Unfortunately, there seems to be no option to install multimedia codecs nicely without internet connection. It looks like a how-to is in order for this.

---

### Post by dougfractal on 2007-07-31
" no internet connection"

What no internet connection as in does'n connect to dialup or  *dsl?
Or have no modem? and what a snapshot of the update repository.

Did you have internet with the livecd ?

---

### Post by SilverBridge on 2007-08-02
Thx for replaying all ...
  i meant by having no internet connection that i dnt have any sort of internet connection , neither wireless or dial up od DSL < I GOT NO CONNECTION AT ALL  , and i got the live CD by downloading the iso image in an internet cafe and burnt it into a CD and went home and put it it into my Cd reader and launched the installation ...
  Now after reading many threads about this issue ,it sounds a big problem to update my Ubunto without an internet connection ,and for sure non of the programms working ,cause when i try to add any of the programs through the ADD/REMOVE programms ,so , i figured out a way to overcome this , which is , someone using the same version of Ubunto feisty7.04 and updted it , then made a Live CD of the current updated packages or repositeries , and upload it for us so we download it and burn it into a CD , and use it as a Third party device to download all the packages needed ,i am not sure if this will work or not , so u better tell me ,,, and sorry if i am not explaining the problem i have in a right way , i am a totally biginner ,so i appreciate if u Can help .... Thx ...

---

### Post by dougfractal on 2007-08-02
I have a small group of ubuntu computers, what I do is use an nfs mount to 
/var/cache/apt/archives this is the cache for all the packages. Download once ready for all.
I may still need the internet to check dependences,
So you can copy the .deb's to there /var/cache/apt/archives .


**DVD**

Another approach is to get the DVD from [http://cdimage.ubuntu.com/releases/feisty/release/](http://cdimage.ubuntu.com/releases/feisty/release/) [http://cdimage.ubuntu.com/releases/feisty/release/ubuntu-7.04-dvd-i386.iso](http://cdimage.ubuntu.com/releases/feisty/release/ubuntu-7.04-dvd-i386.iso) 
you can then use this as a repo. 

```
sudo apt-cdrom add
sudo gedit /etc/apt/sources.list
```

comment out all network repos #

```
sudo apt-get update
```

all apt-get / synaptic will use the DVD

**UPDATES (Build your own repo)**
You can use your own mirror, mines gb.

another big download
from [http://wiki.africasource2.tacticaltech.org/post/main/02kq1ct2pXNBBsXY](http://wiki.africasource2.tacticaltech.org/post/main/02kq1ct2pXNBBsXY)
[http://ubuntuforums.org/showthread.php?t=255128](http://ubuntuforums.org/showthread.php?t=255128)
```
wget  http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz
wget  http://gb.archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz
zgrep '^Filename' Packages* | awk '{printf "wget  http://gb.archive.ubuntu.com/ubuntu/%s\n", $2}' | sh
dpkg-scanpackages ./ /dev/null | gzip > Packages.gz
```

Edit /etc/apt/sources.list . comment every repo out and added my repo to the top in this format.

```
deb file:/path/ ./
```


The end-user should be able to install the security updates from the
graphical interface.

**FROM FRIENDS**
```
cd /var/cache/apt/archives
dpkg-scanpackages . /dev/null | gzip > Packages.gz
```



Good luck

---

