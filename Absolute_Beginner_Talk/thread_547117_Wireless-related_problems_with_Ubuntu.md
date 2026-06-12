---
title: "Wireless-related problems with Ubuntu"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Theshooter7 on 2007-09-09
Hello, I've just installed Ubuntu 7.04 and am very interested with it.

However, I have problems with obtaining a wireless connection. I have a Linksys WUSB11 V2.6 adapter. I've followed several links from Google about this issue, and tried to install Wireless Tools and ndiswrapper. However, when I go to make them (sudo make install) I receive a ton of errors. Anyone know what is wrong? (The errors are really long, so I have included the file as an attachment. Just open it in Ubuntu or use Notepad in windows to see it) Also note that I have not installed anything more than Ubuntu and what came with Ubuntu, so if there is something I need, please, by all means post a link. Also, I've read some steps about compiling the Kernel, and all of them require internet connections, which I don't have other than Wireless (which means no apt-get) so if it is possible, post instructions that don't require internet access. :P

Thanks for any help given.

---

### Post by SOULRiDER on 2007-09-09
Could you post a link to the websites you used for information? Are you sure you followed all the steps correctly?

---

### Post by Theshooter7 on 2007-09-09
Certainly. Here it is. It is another forum topic about a problem similar to mine.

[http://www.linuxforums.org/forum/linux-networking/40165-newb-seeking-help-linksys-wusb11-v-2-6-a.html](http://www.linuxforums.org/forum/linux-networking/40165-newb-seeking-help-linksys-wusb11-v-2-6-a.html)

I also just discovered this:
[http://ubuntuforums.org/showthread.php?t=225206&highlight=javajake](http://ubuntuforums.org/showthread.php?t=225206&highlight=javajake)

Would this perhaps work for a WUSB11 2.6? Also,

> **javaJake said:**
> 
**_Step 1 - Install the essentials_**
If you haven't compiled anything before using "make", then you'll probably need to run this command. Open the terminal and run this:

```
sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)
```

I thought you needed an internet connection for apt-get. Does that HOWTO assume you have a wired connection, or am I wrong about it?

---

### Post by SOULRiDER on 2007-09-09
Sort of, you need to install some packages formt he repositories, you do that with an internet connection. If you have internet on another computer you can manually download the packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) If you have another linux installation with a working internet connection you can chroot into your Ubuntu installation and apt-get those files.

If you ahve a friend with an internet connection and ubuntu you can askt hem to download those packages and giove themt o you using APTonCD, that will handle the dependencies.

---

### Post by Theshooter7 on 2007-09-09
Thanks, Soulrider. I have a working internet connection on my Windows OS (I'm dual booting with Ubuntu on several partitions) so that won't be a problem.

[EDIT] on a side note, I'm not sure which packages I am to get. :/

---

### Post by SOULRiDER on 2007-09-09
You will need to get **build-essential** and **linux-headers-???** where ??? is the output of **uname -r**. The problem is that you will need to download the dependencies what are not currently installed and dependencies of dependencies and so forth... it can be a pain in the butt my friend, thats why the APTonCD option is better IMHO. I would select and send you the packages but im running gutsy at the moment, so unless you are running gutsy you will have to ask a person with feisty or whatever youre running.

---

### Post by Theshooter7 on 2007-09-09
O_O

You're right. There is a lot of things to get. this could take a while...But at least I've been pointed in the right direction. Thanks again. I'll report back once I've managed to download and install everything.

---

### Post by SOULRiDER on 2007-09-09
I may be able to boot witht he Live CD (if I have any) and fetch those packages for you, but I will have to do ti tomorrow. I have a slow connection though so its a bit insane if its over 20mB

---

### Post by Theshooter7 on 2007-09-11
If you could be so kind, that would be of great help. I understand if you can't, though.

---

### Post by Theshooter7 on 2007-09-12
Sorry for double posting.

I downloaded all the dependencies, and got ndiswrapper and wireless tools installed. However, I'm not sure what to do now. I edited etc/network/interfaces to find my hidden network and use the WEP Key (Entered in the format AA:BB:CC etc), but still no dice.

---

