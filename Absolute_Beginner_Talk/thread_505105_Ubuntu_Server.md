---
title: "Ubuntu Server"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by jsphrcross on 2007-07-19
Hello;

I am brand new to Linux and Ubuntu. Yes I am looking to leave the evil empire Microsoft. I have been experimenting with Ubuntu Server 7.04 tonight. I have installed it twice and when it boots after installation, it goes to a text interface. I was hoping for a GUI interface. Does the server version contain a GUI interface like the desktop version?

Thanks in advance.....

---

### Post by freebeer on 2007-07-19
I don't have any experience with the Server version, but, no... the server doesn't include a GUI in order to keep the installation as light weight as possible.  A GUI can be installed, but you'll be better off getting the regular Live CD, I believe.  (The Live CD version of Ubuntu will give you Gnome by default.)  You can still load server software (FTP, Apache Web Server, etc.) in the GUI version.

---

### Post by FleetAdmiral74 on 2007-07-19
I agree. If you need the server CD, you should not need the GUI. It's just not a requirement for a server, and would only serve to slow down the machine. You can always install the server stuff in Ubuntu, start out with a GUI, and then start testing the command line interface version while in ubuntu, and when you are ready make the switch. 

 It can be installed, I forget the actual command. Probably something like sudo apt-get install gnome-desktop, but i forget.

---

### Post by machoo02 on 2007-07-19
```
sudo aptitude install ubuntu-desktop
```is what you are looking for to install a GUI desktop.  replace ubuntu with kubuntu if you want KDE, or xubuntu if you want XFCE.

---

### Post by jsphrcross on 2007-07-19
Not the answer I was hoping for. How about switching to Edubuntu server? I am looking to test thin client technology and the GUI interface would really help me proceed faster. Or can I add the the LTSP server software on to Ubuntu Desktop??

Thanks again for your replies.  :confused:

---

### Post by machoo02 on 2007-07-19
You could add the LTSP to Ubuntu, but you would probably be better off installing Edubuntu since the brunt of the installation and configuration has been done for you.

---

### Post by jsphrcross on 2007-07-19
Thanks machoo02. I think I will give that a shot. Luckily I have other systems available as I am enjoying my Ubuntu 7.04 desktop version.

---

