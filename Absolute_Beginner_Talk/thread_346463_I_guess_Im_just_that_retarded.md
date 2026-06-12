---
title: "I guess Im just that retarded"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by mc.7winkie on 2007-01-25
Okay,  after my failed attempts to download network-manager-gnome I have now decided to try wifi-radar.  The problem is that I'm so stupid as to not know how to install software manually.  I have downloaded it and loaded it onto a flash drive and whenever I go into the add/remove software to install it it tries to download it from the the internet.  The only problem is that I can't get on th internet because I thats exactly what I'm trying to do (perfect Catch 22 eh?)  Could some one please help me???

---

### Post by ComplexNumber on 2007-01-25
stop calling yourself stupid! you're not stupid - _everyone_ has to start somewhere. 


anyway, wifi-radar is a good program, i think. it helped me to get set up wirelessly on fedora.

ok, you say that you downloaded wifi-radar. what exactly is the full name of the program (eg is it wifi-radar.tar.gz? or is it wifi-radar.deb? etc).

---

### Post by mc.7winkie on 2007-01-25
Thanks for the encouragement.  The entire file name is wifi-radar-1.9.6.tar.gz  Or something VERY similar to that.  I'm doing it off the top of my head.

---

### Post by Tomosaur on 2007-01-25
**YOU FIRST NEED TO DOWNLOAD THIS FILE:**  [http://gb.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3_i386.deb)

Put it on your flash drive, then go into Ubuntu and install it. The following instructions require it.

Ok, the .tar.gz extension means that file is a **compressed archive**. This is very similar to .zip and .rar files, which are common in Windows.

What you need to do is de-compress that file. You have two options. One is to just double-click the file and extract it like you would in Windows. The other is to use the command line (which I prefer). Since the double-click way is pretty self-explanatory, here's how to do it via the command line.

Click Applications, then Accessories, then Terminal.
Change to the directory where the file is saved. You said it's on a usb drive, so your command my look something like this:
```

cd /media/usb

```
If you're not sure what the name of your USB drive is, type 'ls /media' in the command line, and check the list of results. One should look obviously like your USB drive. Regardless, the command to change directory is 'cd'.

Once you're in your USB drive, you again need to change to the directory where the file is saved.  Once you find it, type:
```

tar zxvf ./wifi-radar-1.9.6.tar.gz

```
or whatever the actual filename is. This will extract the file into a folder called wifi-radar-1.9.6
```

cd ./wifi-radar-1.9.6

```

Now, it is VERY likely that you have download the source code for this program, so you need to type these commands, pressing enter after each:
```

./configure
make
sudo make install

```
The last one will ask you for your password. You won't see it being typed in, but it is working, so just type your password and hit enter. The middle command may take a little while to finish. Congratulations, you just compiled and installed your program :)

---

### Post by aysiu on 2007-01-25
**wifi-radar**
Installing *wifi-radar* is a lot easier than you'd think.

On your computer that has an internet connection, download the .deb for it from [the closest mirror](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fw%2Fwifi-radar%2Fwifi-radar_1.9.7-0ubuntu2_all.deb&md5sum=5034125e34ee2ccfbf6f40f3f48441d2&arch=all&type=main).

Transfer that file to the desktop of your Ubuntu computer. Then double-click the .deb file.

**network-manager**
Network-manager is a little trickier, as there are three dependencies you'd also need to install. You'd download [network-manager](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager_0.6.3-2ubuntu6_i386.deb&md5sum=522cade5b931785517c0fb2bb7035a1e&arch=i386&type=main), [dhcdbd](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fd%2Fdhcdbd%2Fdhcdbd_1.14-2ubuntu2_i386.deb&md5sum=f597e9322731e08b68815383d274bac2&arch=i386&type=main),        [libnm-util0](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Flibnm-util0_0.6.3-2ubuntu6_i386.deb&md5sum=35f0369504c376261c6cddc76e29c64d&arch=i386&type=main), and [libnl1-pre](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibn%2Flibnl%2Flibnl1-pre6_1.0~pre5%2Bsvn21-2ubuntu2_i386.deb&md5sum=0d836551f19893b6dbc34888b173d809&arch=i386&type=main). Transfer all those files to the desktop of your Ubuntu computer and then type these commands in the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

**Disclaimer**
By the way, this is all assuming you're not using 64-bit or PowerPC Ubuntu. I also am linking you to Edgy Eft (6.10) packages. Let us know if you're actually using Dapper Drake (6.06) instead.

---

