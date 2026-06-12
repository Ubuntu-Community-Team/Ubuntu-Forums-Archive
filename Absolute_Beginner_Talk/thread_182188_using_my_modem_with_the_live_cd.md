---
title: "using my modem with the live cd"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-05-25
Dear All,

Firstly, thankyou for being so helpful! It's amazing. You guys are great!

Now, my big problem. I live in the land of dialup. I don't know how to connect to the internet from the live CD. And I want to make sure everything works before I decide to partition my hard disk and install Ubuntu.

Also, when i save something when I'm working from the Live CD, where does it save it? Do I lose everything when I log out? 

Sorry for being so ignorant. First-time user I am :)

Cheers,
thanks in advance,

David K

---

### Post by [S|G] on 2006-05-25
Hello,

Well, I'm afraid I'm not really the person to help you with dial-up, but I'll try to explain a bit about using the live-cd :)

It creates a virtual ram disk that will be erased  when you reboot your computer, so the files you save won't be kept (unless you mount your local drive manually).

---

### Post by towsonu2003 on 2006-05-25
[QUOTE=dckirba]
Now, my big problem. I live in the land of dialup. I don't know how to connect to the internet from the live CD.[/quote]
have a look at the wiki dial up (second link in my signature) for that. It's the same for live and installed systems. the only difference: you reboot, you do it all over again in liveCD. Save that web site and the scanmodem tool to somewhere where you can access them in your liveCD (usb stick, floppy, a partition...)
[QUOTE=dckirba]
Do I lose everything when I log out? 
[/QUOTE]
Yes, you'll loose everything. Have a look at [https://wiki.ubuntu.com/LiveCDPersistence](https://wiki.ubuntu.com/LiveCDPersistence) for not loosing everything, but it requires some additional work :)
What I do is to have a small fat32 partition and save the contents of /etc/ (configuration files) and /home/yourusername/ (your own files) and /var/cache/apt/archives/ (files you apt-getted) from the liveCD session there so when I am using the liveCD, I just copy paste the files I need from fat32 to the live session file system and restart X (I have a custom xorg.conf).

---

### Post by dckirba on 2006-05-26
thankyou guys, I will try it out right now and hopefully be able to let you know it's working after I log on from the live CD!

cheers,
David K

---

### Post by dckirba on 2006-05-26
Hey guys,

Almost got there but didn't quiet make it:neutral: 

towsonu, I followed the instructions on the link you gave me.  scanModem found out that I had a conexant modem and I downloaded the driver. I was also asked to download the following packages:

    *      And, if you are using Ubuntu 5.10 (Breezy) then you will also have to get the gcc-3.4, gcc-3.4-base and cpp-3.4 packages:
    *      [WWW] [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/g++-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/g++-3.4_3.4.4-6ubuntu8_i386.deb)
    *      [WWW] [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb)
    *      [WWW] [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb)
    *      [WWW] [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb)

The instructions said to install these first before installing the driver for the modem. So I did, but two of them failed. One was the g++ file and the other one I didn't catch.

But I went ahead and installed the driver.

If I use the modem monitor, it allows me to dial, says I'm connected. But Firefox can't open any sites and the package manager can't update.

I tried configuring wvdial.conf and then running it but it says invalid number, username and password. ](*,) 

I know that the system is correctly detecting the modem and dialling out because I tried calling myself on my mobile and it rang. 

Help again!

David K

---

