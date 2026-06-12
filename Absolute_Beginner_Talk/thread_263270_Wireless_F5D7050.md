---
title: "Wireless F5D7050"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by quickq111 on 2006-09-22
To start, I think Ubuntu is amazing. I used it in VMWare, and it was by far the best linux disto I have ever seen. However, VMWare makes everything easy, and when I deicded to try and install Ubuntu on my hard drive, it wasn't as smooth.

I do not have any Ethernet connection, so I use wireless. I have a Belkin F5D7050 version 3000 (Ralink drivers -- RT2500 I believe) USB. For some reason, when I put in the USB wireless reciever, nothing happens. And I can't install ndiswrapper, because "sudo make ndiswrapper" returns something basically that says it doesn't know what "make" is. And I can't just get online to find out without switching back to Windows.

Is there any way someone can instruct me on how to get Wireless Internet using the F5D7050 USB Belkin wireless adapter? I really want to use Ubuntu, but without internet it's just not worth it for me. 

Thank You.

---

### Post by Arevos on 2006-09-23
You can install ndiswrapper through the Ubuntu repositories with:
```
sudo apt-get install ndiswrapper
```
However, it might be an idea to build from source, as I have a Belkin F5D7050 and too much data transfer locks up my system. It doesn't happen often, but it is rather irritating when it does occur. Looking at the changelogs for ndiswrapper, it would appear that this is fixed in version 1.18, whilst Ubuntu Dapper ships only with 1.8.

To build from source, you'll need to install the build-essentials and kernel-headers packagaes.

---

### Post by wildseven on 2006-09-23
he is correct

also i beleive it is just

make
sudo make install


not make install <w.e>


good luck

---

