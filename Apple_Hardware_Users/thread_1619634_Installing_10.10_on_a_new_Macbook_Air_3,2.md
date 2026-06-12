---
title: "Installing 10.10 on a new Macbook Air 3,2"
date: 2010-11-12
forum: Apple Hardware Users
---

### Post by OldAbe on 2010-11-12
Hi!
I'm traying to install Ubuntu 10.10 on a clean **Macbook Air 3,2. **
This is the step I have done at the time.
 
1. Installing Mac OS X Snow Lep 10.6.5 in all updates. 
2. Installd **rEFIt 0.1.4** on the same partition I have OS X on. 
3. Chages the repartitions the main drive to the folowing.
 
- Partition 1, 50GB Mac OS Extended (Journaled)
- Partition 2, 2GB MS-DOS (FAT)
- Partition 3, 30GB MS-DOS (FAT)
- Partition 4, 40GB MS-DOS (FAT)
- Partitoon 5, The rest MS-DOS (FAT)
 
4. Installing Windows 7 on partition 4, OK.
5. Installing Windows 7 drivers from Macbook Air 3,2 using (Boot Camp Assistant) in Mac OS X Snow Lep 10.6.5, OK.
6. Creting a Linux Live USB- boot installation using **LiLi USB Creator** [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) (**ubuntu-10.10-desktop-i386.iso**) 
7. Checking so the USB- Stick is working in my other comuters. OK
8. Traying to boot from the USB- stick. In the **rEFIt 0.1.4** boot manu choseing the Live USB- stick with Ubuntu 10.10 on.
 
Geting this error: Boot Error
End
 
More info: I see the Linux icon when I chose to start booting form the USB- stick for some sec and after some time the screen get black and the error.
 
Any sugestions?
Been reading on the forum for 3 days with out any luck.
 
Thanks 
Martin

---

### Post by Ryan L on 2010-11-16
I tried to install on my 11.6 inch MacBook Air.  There is one important trick.

I use CD to boot up instead.  After the language menu, press F6 and opt "nomodeset" and it will bring you to the screen for installation.  After the installation, you can install the Nivida drive to solve the resolution issue.

Hope this helps.

---

### Post by andresmh on 2010-11-16
Are there reports of people successfully running Ubuntu on a Macbook Air '10? If so, does all the hardware work (sound in/out, webcam, etc) and what is the battery life like?

---

### Post by npgall on 2010-11-16
See this thread: [http://ubuntuforums.org/showthread.php?t=1603365](http://ubuntuforums.org/showthread.php?t=1603365)

---

### Post by bean1233 on 2011-02-28
ty ryan that solved my problem

---

### Post by hippospark on 2011-03-16
here is an easy way to install 10.10 on new Macbook air, check it: [http://ivarptr.blogspot.com/2011/03/install-ubuntu-1010-on-macbook-air-31.html](http://ivarptr.blogspot.com/2011/03/install-ubuntu-1010-on-macbook-air-31.html)

---

