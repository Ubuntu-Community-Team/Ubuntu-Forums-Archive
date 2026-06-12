---
title: "Resuming a broken download"
date: 2012-07-02
forum: Any Other OS
---

### Post by tech291083 on 2012-07-02
Hi Friends,
 
 I have a very slow and unreliable internet connection at home which  often gets disconnected. I have to start downloading files particularly  large Linux distros all over again. I am not sure but is Archive Mounter  a  download manager that can help me download a large file even after I  leave it midway and resume it the next day or whenever I want? Or if I  loose power supply, I should be able to store the download upto that  point. I hope you have got my point here. Please help me chose a good  download manager for Ubuntu and Fedora. Thanks a lot.

---

### Post by kdane4 on 2012-07-02
Hi,

If you're downloading large distros, why not use a torrent client? You can safely resume any download you want and is guaranteed that your download wont be corrupt because it automatically fixes hash.. :)

---

### Post by tech291083 on 2012-07-03
> **kdane4 said:**
> Hi,

If you're downloading large distros, why not use a torrent client? You can safely resume any download you want and is guaranteed that your download wont be corrupt because it automatically fixes hash.. :)


Yes, I do use KTorrent almost all the time to download large distro with 100% success, but there are times when some distros are not available via torrents for example the latest Knoppix 7.0.2. Here is the official page as far as I know. Correct me if I am wrong here. Thanks.

Below link has no torrent for Knoppix 7.0.2 despite it being released already, do not know why.

[http://torrent.unix-ag.uni-kl.de/](http://torrent.unix-ag.uni-kl.de/)

Below link has onlt large files, for which I may need a good download manager. 

Thanks.
[http://www.knopper.net/knoppix-mirrors/index-en.html](http://www.knopper.net/knoppix-mirrors/index-en.html)

---

### Post by Simian Man on 2012-07-03
wget can resume a download that gets interrupted with the "-c" option.

---

### Post by tech291083 on 2012-07-03
> **Simian Man said:**
> wget can resume a download that gets interrupted with the "-c" option.

Hi,

I know that, read somewhere on the net today only. But I really do not know how to use that option. For example, I am downloading this files as shown in the screen shot attached to my post. Here is the url from where I am downloading it. 

[http://mirrors.kernel.org/knoppix-dvd/](http://mirrors.kernel.org/knoppix-dvd/)

Knoppix 7.0.2 DVD English version it is. I am downloading it as a regular file with the save file option. 

[KNOPPIX_V7.0.2DVD-2012-05-30-EN.iso]("http://mirrors.kernel.org/knoppix-dvd/KNOPPIX_V7.0.2DVD-2012-05-30-EN.iso")

---

### Post by Simian Man on 2012-07-03
Just run this in a terminal:
```

wget http://mirrors.kernel.org/knoppix-dvd/KNOPPIX_V7.0.2DVD-2012-05-30-EN.iso

```

Then, if something causes it to fail, and you only got half of the file, go to the same directory with the partial file and run:
```

wget -c http://mirrors.kernel.org/knoppix-dvd/KNOPPIX_V7.0.2DVD-2012-05-30-EN.iso

```
This will start downloading again where it left off.

---

### Post by tech291083 on 2012-07-03
> **Simian Man said:**
> Just run this in a terminal:
```

wget http://mirrors.kernel.org/knoppix-dvd/KNOPPIX_V7.0.2DVD-2012-05-30-EN.iso

```Then, if something causes it to fail, and you only got half of the file, go to the same directory with the partial file and run:
```

wget -c http://mirrors.kernel.org/knoppix-dvd/KNOPPIX_V7.0.2DVD-2012-05-30-EN.iso

```This will start downloading again where it left off.
Thanks a lot. I tried it and works now in a terminal. This means I need to keep the terminal open all the while that I am downloading it, right?

ok, I think I have got the anwser. I have closed down the terminal and opened the Gwget GUI. It is working fine right now. Thanks.

---

### Post by cipherboy_loc on 2012-07-03
For further reference, wget and wget -c do not need to be run in the same terminal (bash session). 


Cipherboy

---

### Post by raja.genupula on 2012-07-03
> This means I need to keep the terminal open all the while that I am downloading it, right?

yes you must .:D

---

