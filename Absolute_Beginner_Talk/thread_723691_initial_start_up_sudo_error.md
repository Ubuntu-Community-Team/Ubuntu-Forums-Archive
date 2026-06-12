---
title: "initial start up sudo error"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by McWave15 on 2008-03-13
how come the first time i try and turn my computer on after installing ubuntu, it asks about a sudo man-root code.  i have already entered my username and password successfully this is what immediately follows.  does anyone know the proper code or what i should try?

---

### Post by Tatty on 2008-03-13
it shouldnt be asking you for a sudo password on boot.

It will ask you to log in with your username and password but it shouldnt need to ask for root privilages.

What exactly happens?  can you explain in more detail?

---

### Post by McWave15 on 2008-03-13
i installed ubuntu from an ISO disk and went through the install process fine, it ejected the disk and rebooted and it went through all the [ok] screens and then asked for username and password which i entered and then immediately after is says" 
Linux Home 2.6.22-14-server #1 SMp Sun Oct 14 23:34:23 GMT 2007 i686

The programs included with the Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /user/share/doc/*/copyright.

Ubuntu comes with ABSOLUTLY NO WARRANTY, to the extent permitted by applicable law.

username@Home:~$

I have no idea what this means or how to get past it.

---

### Post by Tatty on 2008-03-13
I think you may have installed the Ubuntu Server Edition.

The server edition doesn't come with a graphical interface by default.  I would recommend downloading a Ubuntu Desktop install CD here [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download") and then re-installing with that.


Although if you just want to just get a GUI on the server edition You can install the standard ubuntu desktop with this command:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by McWave15 on 2008-03-13
i am fairly sure i downloaded the desktop version in 32-bit because my 64bit would no read.  i have already re-installed twice.  thanks

---

### Post by Tatty on 2008-03-13
> **McWave15 said:**
> i am fairly sure i downloaded the desktop version in 32-bit because my 64bit would no read.  i have already re-installed twice.  thanks

In that case:

a) did you download the Live or the alternate CD?

b) if you downloaded the Live CD then did it boot to a GUI correctly before you installed?

---

### Post by McWave15 on 2008-03-13
I downloaded from the same link you sent me and it did go to the GUI that asked how you wanted to install.  i clicked the first install option and went through the process.

---

### Post by Tatty on 2008-03-13
It sounds like something went wrong with your install.

try reconfiguring X:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Nythain on 2008-03-13
> **McWave15 said:**
>  
Linux Home 2.6.22-14-server #1 SMp Sun Oct 14 23:34:23 GMT 2007 i686

The programs included with the Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /user/share/doc/*/copyright.

Ubuntu comes with ABSOLUTLY NO WARRANTY, to the extent permitted by applicable law.

username@Home:~$

If thats exactly what it says when you boot up, word for word, you're runnin on a server install of some sorts...
"Linux Home 2.6.22-14-server" the -server at the end of the kernel name implies exactly that, its the server kernel... now that kernel generally, for the most part, unless told very specifically in other situations, only gets installed when you install ubuntu-server (maybe also if you install the lamp package later, or the server kernel after installing a full DE distro)

server is definately nto what you want, nto really for any reason other than it has no gui...
a quick
```

sudo nano /etc/apt/sources.list

```
and removing #'s from any lines that look like this
#  deb [http://whatever.ubuntu.com/whatever](http://whatever.ubuntu.com/whatever) yadda yadda
and
#  src [http://the.same.thing](http://the.same.thing)

then hit ctrl+x, y to save, enter to save as the current filename then
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```
will install the desktop software, reboot and you should hopefully be good to go

---

### Post by McWave15 on 2008-03-13
when i input that code it says not installed.  should i just re-download and then install again?

---

### Post by Tatty on 2008-03-13
ok the quick answer to get you a desktop is to do this:

```
sudo apt-get install ubuntu-desktop
```

**EDIT:** just re-read Nythains post and he is correct... you definitely have installed the serer edition.  Install the Desktop Edition

---

### Post by 3rdalbum on 2008-03-13
Download or request the Desktop Edition. The server edition does not have a GUI, that's why you're getting the command-line prompt that you describe.

---

### Post by McWave15 on 2008-03-13
Im in the middle of downloading it again and i will hopefully get it right this time. thank you both for all your help.

---

