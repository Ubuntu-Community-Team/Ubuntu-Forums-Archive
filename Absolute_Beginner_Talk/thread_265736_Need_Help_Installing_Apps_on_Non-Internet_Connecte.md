---
title: "Need Help Installing Apps on Non-Internet Connected Computer"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Stervyatnik on 2006-09-26
Hello, all! I am a new user to Linux, and an enthusiastic one! I converted a 600 MHz Pentium III with 20GB Hard Drive and 258 MB RAM to an Ubuntu (6.06) box, and I absolutely love it! The Gnome Destop is nice, the apps that were installed run great, and I am looking forward to adding more.

The problem I have is that the Ubuntu apparently uses an application called "Apt" (or Apt-Get?) to install new software. The computer I converted doesn't have a modem, so - right now - it's "isolated." I would like to download Linux apps from my Internet-connected computer, burn them to a CD, then install on my Ubuntu box.

How can I do it? I'm pretty good with Windows software, but like I said, Linux is new for me. Do I download tar.gz files, and use some shell scripting to accomplish the installs? Or is there some other file type specifically for Debian (and derivatives) distros?

One side-note occurs: I'd like to add a modem. How do I get Ubuntu to "recognize" it and install "drivers" (or the Linux equivalent) so that it's usable? I looked at a USRobotics 56K V.92 FaxModem PCI (Model 5699B) at the local Walmart, and would get it except I'm REALLY unsure of how to install new hardware. Any help in this arena would be appreciated.

I'd like to load Apache, MySQL and PHP, plus some other graphics and HTML WYSIWYG apps which I'm investigating now. If I get one install "under my belt," I'll probably be good to go on others. Again, any help is appreciated! Thanks in advance!

---

### Post by whizbaby on 2006-09-26
> **Stervyatnik said:**
> The problem I have is that the Ubuntu apparently uses an application called "Apt" (or Apt-Get?) to install new software. The computer I converted doesn't have a modem, so - right now - it's "isolated." I would like to download Linux apps from my Internet-connected computer, burn them to a CD, then install on my Ubuntu box.

Packages can be downloaded manually from
[http://archive.ubuntu.com/ubuntu/pool](http://archive.ubuntu.com/ubuntu/pool)
They have a .deb ending and can be installed with dpkg (**sudo dpkg -i *package_name***) . The problem is that for one package you need to download and install all packages it depends on first, dependancies can be found somewhere on [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
(you'll have to look for package lists)
> 
One side-note occurs: I'd like to add a modem. How do I get Ubuntu to "recognize" it and install "drivers" (or the Linux equivalent) so that it's usable? I looked at a USRobotics 56K V.92 FaxModem PCI (Model 5699B) at the local Walmart, and would get it except I'm REALLY unsure of how to install new hardware. Any help in this arena would be appreciated.

You'd enjoy to use *wvdial*, this guesses how to talk to your modem, so no driver download. Just make sure the modem you buy works well with linux (e.g. is not a WinModem)
You do
**sudo wvdialconfig**
then edit /etc/wvdialconfig to configure username, password and phonenumber to dial and then
**sudo wvdial**.

---

### Post by bluefrog on 2006-09-26
u'd better add a network card to your puters and connect them. > small network.

It will be simpler in the end.
James

---

### Post by Bachstelze on 2006-09-26
Yep, getting a WinModem to work can quickly become really tedious... Getting a network card and sharing the internet connection will be far easier as almost all NICs work OOTB.

---

### Post by whizbaby on 2006-09-26
This way the one computer only has internet with the other turned on, though. Depends on what you want. There are also combinations router/modem so that both computers are plugged in that via ethernet, but this usually makes sense with more than two computers (expensive).

---

