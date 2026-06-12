---
title: "Autostart Firewall, root login and script install"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by serafin630 on 2008-03-13
I just revived an old PC running XP with Xbuntu.  I know Windows pretty well but am new to linux (which is why I am here!) and have three probably very basic questions about getting this machine setup.

(1)  I assume I need a firewall and found one to install.  I have the OS auto-logging in but can't figure out how to get this firewall to load at every reboot.

(2)  I assume I need antivirus protection and found a program to install.  It doesn't have any virus definitions and says that only the root user can download them.  How do I log in as the root user so I can update this list.

(3)  I'd like to use this machine to connect to my work via Citrix Presentation Manager.  The citrix login page gives me links to a couple of linix clients to use (I don't know the difference between the two so I was going to try them both) but the install directions I download with the install files tells me to run the install "script".  There is a file included that has some version of the word INSTALL in its name, but trying to run it as I would have in Windows (ie double-clicking on it or using the RUN function off the Windows Start button) isn't installing.  How do I run an install script to install a new app?

Thanks in advance.

Bob Serafin

---

### Post by Oldsoldier2003 on 2008-03-13
> **serafin630 said:**
> I just revived an old PC running XP with Xbuntu.  I know Windows pretty well but am new to linux (which is why I am here!) and have three probably very basic questions about getting this machine setup.

(1)  I assume I need a firewall and found one to install.  I have the OS auto-logging in but can't figure out how to get this firewall to load at every reboot.

(2)  I assume I need antivirus protection and found a program to install.  It doesn't have any virus definitions and says that only the root user can download them.  How do I log in as the root user so I can update this list. if you need to login as root to update the definitions just sudo. If you are using clamav the command would be sudo freshclam

(3)  I'd like to use this machine to connect to my work via Citrix Presentation Manager.  The citrix login page gives me links to a couple of linix clients to use (I don't know the difference between the two so I was going to try them both) but the install directions I download with the install files tells me to run the install "script".  There is a file included that has some version of the word INSTALL in its name, but trying to run it as I would have in Windows (ie double-clicking on it or using the RUN function off the Windows Start button) isn't installing.  How do I run an install script to install a new app?

Thanks in advance.

Bob Serafin
1) actually you don't really need a firewall in Ubuntu unless you open ports by installing server software. if you feel you must use a firewall try installing firestarter (its a gui front end for iptables- the preinstalled firewall for Ubuntu)

```
sudo apt-get install firestarter
```
2) antivirus really isn't needed unless you exchange documents regularly with windows users. as for needing root to update the definitions, Assuming clamav is what you installed:
```
sudo freshclam
``` should do the trick 
3) if the app came in a tarball all you usually have to do is extract it, cd to the directory and type ./install

---

### Post by PeterJS on 2008-03-13
> **serafin630 said:**
> I just revived an old PC running XP with Xbuntu.  I know Windows pretty well but am new to linux (which is why I am here!) and have three probably very basic questions about getting this machine setup.

(1)  I assume I need a firewall and found one to install.  I have the OS auto-logging in but can't figure out how to get this firewall to load at every reboot.

You assume incorrectly. By default, Ubuntu has no listening services that would need a firewall to protect them. Furthermore the firewall (iptables) is loaded automatically at boot, but it doesn't have any rules by default, most configuration tools correctly setup their rules to be automatically loaded at boot even if the tool itself isn't loaded.

> 
(2)  I assume I need antivirus protection and found a program to install.  It doesn't have any virus definitions and says that only the root user can download them.  How do I log in as the root user so I can update this list.


Again you assume incorrectly. Antivirus is not needed,the only antivirus available for linux only checks for windows viruses, as there are no known linux viruses for the anti-virus to check for. Ubuntu security is based on an entirely different paridigm, rather than reacting to threats after they happen the security model is based on not letting nasty things get loose on the system in the first palce. The ubuntu security guide:
[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)

---

### Post by Paqman on 2008-03-13
> **serafin630 said:**
> 
(3)  I'd like to use this machine to connect to my work via Citrix Presentation Manager.  The citrix login page gives me links to a couple of linix clients to use (I don't know the difference between the two so I was going to try them both) but the install directions I download with the install files tells me to run the install "script".  There is a file included that has some version of the word INSTALL in its name, but trying to run it as I would have in Windows (ie double-clicking on it or using the RUN function off the Windows Start button) isn't installing.  How do I run an install script to install a new app?


I'm figuring you're looking at [this page](http://www.citrix.com/English/SS/downloads/details.asp?dID=2755&downloadID=3323&pID=186).

One of those is a .rpm file, the other is a tar.gz.

Linux has two main types of packages, rpm and deb. Ubuntu uses deb's. It is possible to convert an rpm to a deb using something called [alien](http://en.wikipedia.org/wiki/Alien_%28software%29).

The tar.gz is what's called a tarball. Tarballs are a bit fiddly to install, but have the advantage of not caring which packaging standard your particular distro uses. So they're fairly common for 3rd party software. 

Have a read of this for more info: [How to Install Anything in Ubuntu](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by (((X))) on 2008-03-13
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
Section 3.3 is probably everything you need + your custom script

---

