---
title: "sudo knoppix-installer : command not found"
date: 2012-06-22
forum: Any Other OS
---

### Post by tech291083 on 2012-06-22
Hi,  I have just downloaded and burned Knoppix 7.0.1 to a DVD and it works fine. But when I boot my pc with the DVD in the DVD drive and open a terminal and issue the following command as root to install it to my hard drive there is an error.

```

root@Microknoppix:/home/knoppix# sudo knoppix-installer
sudo: knoppix-installer: command not found
root@Microknoppix:/home/knoppix# sudo knx2hdd
sudo: knx2hdd: command not found
root@Microknoppix:/home/knoppix# 

```

Please help me with this. I have read people's views saying it is possible to install it to a hard disk even though it is meant to be a live DVD. I want to install it as the only OS on my 500 GB SATA hard drisk. Thanks.

---

### Post by Karlchen on 2012-06-22
Hello, tech291083.

_Reason:_
The executables files **knoppix-installer** and **knx2hdd** cannot be found by following the lists of folder given in the search PATH variable.

_Solution:_
Find out where these two files have been stored.
Change to the corresponding folder.
Launch them from this folder like this: ```
./knoppix-installer
``` and ```
./knx2hdd
```Sorry, cannot be more precise at the moment, because I have not got any Knoppix live system at hand.

_Note:_
As you are **root** already there is no need to prefix any **sudo** the commands. 

Kind regards,
Karl

---

### Post by sudodus on 2012-06-22
Recently I installed Knoppix 6.4.4 to a very old computer (Compaq Presario, CPU 400 MHz). After adding some RAM from another oldie, it was straight-forward to follow the instructions in the installer. No fiddling around with hidden commands.

The result was a 'very debian' installed system with the basic things working quite well including internet, audio and video.

---

### Post by tech291083 on 2012-06-22
> **Karlchen said:**
> The executables files **knoppix-installer** and **knx2hdd** cannot be found by following the lists of folder given in the search PATH variable.
 
_Solution:_
Find out where these two files have been stored.
Change to the corresponding folder.
Launch them from this folder like this: ```
./knoppix-installer
``` and ```
./knx2hdd
```Sorry, cannot be more precise at the moment, because I have 
 
Many thanks for your reply, but can you please help me further as to how I can find out the path to these two commands. Please let me know the exact steps. I also tried the other method which meant using the Start menu and selecting Knoppix then selecting Knoppix hard drive install, something like that, but there was one process that went on forever and I had to abort it midway. It was the copying files process. Thanks.

Here what I get in a terminal being root. What to do next? Thanks.


```

root@Microknoppix:/home/knoppix# whereis knoppix-installer
knoppix-installer:
root@Microknoppix:/home/knoppix# whereis knx2hdd
knx2hdd:
root@Microknoppix:/home/knoppix# 

```

---

### Post by sudodus on 2012-06-22
> **tech291083 said:**
> Many thanks for your reply, but can you please help me further as to how I can find out the path to these two commands. Please let me know the exact steps. I also tried the other method which meant using the Start menu and selecting Knoppix then selecting Knoppix hard drive install, something like that, but there was one process that went on forever and I had to abort it midway. It was the copying files process. Thanks.

1. Maybe you were not patient enough, because the copying process takes long time.

2. Try
```
sudo find / -name knoppix-installer
sudo find / -name knx2hdd
```

3. Or try an older version 6.4.4, 6.7.1 or the newest version today, 7.0.2.

---

### Post by tech291083 on 2012-06-23
> **sudodus said:**
> 1. Maybe you were not patient enough, because the copying process takes long time.



Well, you are right. First time I ran it for 45+ mins and aborted. Today I ran it for almost 2 hrs, but it looked to me that it will never end so again I aborted. So can you please tell me as to how long it take actually.

> 
Try an older version 6.4.4, 6.7.1 or the newest version today, 7.0.2.Well, I would love to try the new version. I always do. I tried to look for torrents for the latest version ie 7.0.2, but i could not find any, can you please help me? Thanks.

[http://torrent.unix-ag.uni-kl.de/](http://torrent.unix-ag.uni-kl.de/)

This page has the torrent for a previous version 7.0.1, but not for the latest ie 7.0.2. Where do I look now? Thanks.

---

### Post by sudodus on 2012-06-23
> **tech291083 said:**
> Well, you are right. First time I ran it for 45+ mins and aborted. Today I ran it for almost 2 hrs, but it looked to me that it will never end so again I aborted. So can you please tell me as to how long it take actually.

Well, I would love to try the new version. I always do. I tried to look for torrents for the latest version ie 7.0.2, but i could not find any, can you please help me? Thanks.

[http://torrent.unix-ag.uni-kl.de/](http://torrent.unix-ag.uni-kl.de/)

This page has the torrent for a previous version 7.0.1, but not for the latest ie 7.0.2. Where do I look now? Thanks.

I think two hours should be enough but I am not sure. Was it only copying from the DVD or also downloading via the internet?

Did you check the integrity of the downloaded file with md5sum?

Try [[COLOR="Red"]_ftp://ftp.uni-kl.de/pub/linux/knoppix-dvd/_[/COLOR]]("ftp://ftp.uni-kl.de/pub/linux/knoppix-dvd/")

---

### Post by tech291083 on 2012-06-23
> **sudodus said:**
> I think two hours should be enough but I am not sure. Was it only copying from the DVD or also downloading via the internet?
It was not connected to the net at the time of HD installation and was only copying files.

> 
Did you check the integrity of the downloaded file with md5sum?

Try [[COLOR=Red]_[ftp://ftp.uni-kl.de/pub/linux/knoppix-dvd/](ftp://ftp.uni-kl.de/pub/linux/knoppix-dvd/)_[/COLOR]]("ftp://ftp.uni-kl.de/pub/linux/knoppix-dvd/")I am not sure about checking the integrity of the iso. I have already written it to a DVD. I no longer have the iso file. Can I still do the checking? If yes, then how? Thanks. I am still looking for torrents for 7.0.2

> **sudodus said:**
> 
Did you check the integrity of the downloaded file with md5sum?

Try [ftp://ftp.uni-kl.de/pub/linux/knoppix-dvd/](ftp://ftp.uni-kl.de/pub/linux/knoppix-dvd/)

Ok,

I did the following after inserting the 7.0.1 DVD into the DVD drive and  opening the terminal as root. As far as I know i have not got the right  results for both the md5sum and sha1sum. Have I done everything right  here? Thanks.


```

[root@localhost john]# df -h
Filesystem                    Size  Used Avail Use% Mounted on
rootfs                         46G  7.1G   37G  17% /
devtmpfs                      2.0G     0  2.0G   0% /dev
tmpfs                         2.0G  180K  2.0G   1% /dev/shm
tmpfs                         2.0G   42M  2.0G   3% /run
/dev/mapper/VolGroup-lv_root   46G  7.1G   37G  17% /
tmpfs                         2.0G   42M  2.0G   3% /run
tmpfs                         2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs                         2.0G     0  2.0G   0% /media
/dev/sda2                     497M   78M  395M  17% /boot
/dev/mapper/VolGroup-lv_home   23G  4.1G   18G  19% /home
/dev/sr0                      3.9G  3.9G     0 100% /media/KNOPPIX

``````

[root@localhost john]# md5sum /dev/sr0
d7efbea95a5d35068a35eee41e6ab1c3  /dev/sr0

``````

[root@localhost john]# sha1sum /dev/sr0
6d5f3a259ca89d822380851b2303bfc15dec76f3  /dev/sr0

```

---

### Post by sudodus on 2012-06-23
> **tech291083 said:**
> Ok,

I did the following after inserting the 7.0.1 DVD into the DVD drive and  opening the terminal as root. As far as I know i have not got the right  results for both the md5sum and sha1sum. Have I done everything right  here? Thanks.


```

[root@localhost john]# df -h
Filesystem                    Size  Used Avail Use% Mounted on
...
/dev/sr0                      3.9G  3.9G     0 100% /media/KNOPPIX

``````

[root@localhost john]# md5sum /dev/sr0
d7efbea95a5d35068a35eee41e6ab1c3  /dev/sr0

``````

[root@localhost john]# sha1sum /dev/sr0
6d5f3a259ca89d822380851b2303bfc15dec76f3  /dev/sr0

```
I think you need to run md5sum on the iso file in order to do a correct checksum test. The iso file is expanded on the CD/DVD. But there might be a list in a file on the CD/DVD containing the md5sums for each of the files.

> **tech291083 said:**
> ...
I am still looking for torrents for 7.0.2

I found an FTP page. It's not a torrent, but you can use it, and it contained links to 7.0.2 iso files earlier today.

---

### Post by tech291083 on 2012-06-25
I have decided to download the latest 7.0.2 only and still looking for torrents for that version as it suits my slow net speed. Hope to get an anwser soon. It is really surprising that it is not available for download yet via torrents. Why the delay if any? Thanks.

I have tried a lot to look for 7.0.2 torrents, but in vain. Can anyone please help me? Thanks.

Ok,

I have just downloaded the latest Knoppix 7.0.2 DVD English version from here using the Gwget Download Manager. 

[http://mirrors.kernel.org/knoppix-dvd/](http://mirrors.kernel.org/knoppix-dvd/)

[KNOPPIX_V7.0.2DVD-2012-05-30-EN.iso]("http://mirrors.kernel.org/knoppix-dvd/KNOPPIX_V7.0.2DVD-2012-05-30-EN.iso")   

Here is the official list of mirrors, which I have used in the past with success.
But the iso after having been written to a brand new DVD does not seem to work. Even the checksum is incorrect, can you please tell me a more reliable mirror to download from? I have a slow net connection and there are no torrents available for version 7.0.2 as far as I know and thus I have to use this Gwget download manager. Thanks.

I am now downloading the latest 7.0.3 DVD English edition from the below mirror using Gwget download manager.

[http://ftp.uni-kl.de/pub/linux/knoppix-dvd/](http://ftp.uni-kl.de/pub/linux/knoppix-dvd/)

I hope this will work well. Thanks.

Hi,

I have successfully downloaded the latest Knoppix 7.0.3 and burned to a DVD. I have also installed it to my HDD without any problems whatsoever this time with this latest version. I am at last very happy that I have been able to install it to my hard drive after having thought about it many days ago. Thanks a lot guys. I used the Gwget download manager to download it and it took me around 25 hrs, but its all worth it now, thanks again all of you.

---

### Post by sudodus on 2012-07-13
Congratulations :KS

I'm happy to help :-)

And if you feel that your problem is solved, please click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

### Post by juliodepolo on 2012-08-23
I know that this issue has been solved but, just wanna share... . . I bought Linux Magazine and Knoppix 7.0 comes with it. I was curious to install it on the HD. So I was checking on related forums about Knoppix HD Installation but seemed to be not working for me. Then, was going through the Preferences and found an icon KNOPPIX HD Install... . . Btw, at this very moment that I am posting this message my Knoppix installation is at 50%. Will post some more info if its successfully installed.

---

