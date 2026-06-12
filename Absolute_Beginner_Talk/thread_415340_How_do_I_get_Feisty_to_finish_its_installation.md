---
title: "How do I get Feisty to finish its installation?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-20
I was installing Feisty via terminal with **sudo apt-get dist-upgrade**. Most of it downloaded and then I received the message below. :(
1. What does it mean and what do I do with it to get the install to finish? 
2. Will I need to reboot after that is done?
Thanks for the help. :)
kh

Get:1004 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe unzoo 4.4-5 [19.3kB]                                             
Get:1005 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe xkeyboard-config 0.9-4ubuntu1 [21.7kB]                           
Fetched 733MB in 2h18m42s (88.1kB/s)                                                                                   
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/directfb/libdirectfb-0.9-25_0.9.25.1-5ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/directfb/libdirectfb-0.9-25_0.9.25.1-5ubuntu2_i386.deb)  Connection timed out [IP: 130.239.18.159 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-00-2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-00-2ubuntu2_i386.deb)  Connection timed out [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/console-tools/console-tools_0.2.3dbs-65ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/console-tools/console-tools_0.2.3dbs-65ubuntu3_i386.deb)  Connection timed out [IP: 130.239.18.159 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.8-0ubuntu8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.8-0ubuntu8_i386.deb)  Connection timed out [IP: 130.239.18.159 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sqlite2.0-cil_1.2.3.1-1ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sqlite2.0-cil_1.2.3.1-1ubuntu1_all.deb)  Connection timed out [IP: 130.239.18.159 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
How would I run the **--fix-missing?**

---

### Post by Nythain on 2007-04-20
try taking the us. off of your repository entries in your sources.list... basically it looks like the us repository either timed out or didnt contain the file you neeed... i would delete the us. at the beginning of each one and sudo apt-get update sudo apt-get dist-upgrade again, should hopefully do the trick

---

### Post by kittyhawk63 on 2007-04-20
> **Nythain said:**
> try taking the us. off of your repository entries in your sources.list... basically it looks like the us repository either timed out or didnt contain the file you neeed... i would delete the us. at the beginning of each one and sudo apt-get update sudo apt-get dist-upgrade again, should hopefully do the trick


They did time out. 
Does that mean another 2 hours of downloading?

---

### Post by zubrug on 2007-04-20
It will just install the missing stuff.

---

### Post by kittyhawk63 on 2007-04-20
> **zubrug said:**
> It will just install the missing stuff.

GREAT! On my way. Thanks for your assistance.
kh

---

### Post by Nythain on 2007-04-20
all the packages u got before those that timed out should still be in aptcache so hopefully no, but possibly

---

### Post by kittyhawk63 on 2007-04-20
> **Nythain said:**
> all the packages u got before those that timed out should still be in aptcache so hopefully no, but possibly

Well, let's hope not. If it does, I will just have to be patient and download again. Thanks guys.
kh

---

### Post by Seisen on 2007-04-20
Just type in ```
sudo apt-get dist-upgrade
``` and it will install the files it couldn't the first time. Then it will proceed to finish your upgrade.

---

### Post by kittyhawk63 on 2007-04-20
> **Seisen said:**
> Just type in ```
sudo apt-get dist-upgrade
``` and it will install the files it couldn't the first time. Then it will proceed to finish your upgrade.

I did this already and it told me that it would install the same number of GBs that the initial upgrade did. Do I ignore that and see if it will bypass those downloaded and just grab what's needed?

Edit: I did as you suggested and it is in the progress of downloading the"us" files right now. Only 10 minutes to go.
Thanks guys.
kh

---

### Post by zubrug on 2007-04-20
Hopefully you did backup your important files, I sometimes forget. Go for it.

---

### Post by Nythain on 2007-04-20
yeah, go ahead, because it still has to install the ones you already downloaded, that should be while its still reporting the same size

---

### Post by Seisen on 2007-04-20
That happened to me that why I said to do that, I thought the same thing you did that it would have to download all the packages again.

---

