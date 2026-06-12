---
title: "How to install a downloaded program?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by jfh on 2006-07-30
I have downloaded Opera 9, but when I click on it to try to install it, I get this message:
Could not open "opera_9.0-20060616.5-shared-qt_en_i386.deb"

Archive type not supported.

I'm not sure what this means.  Can anyone tell me how to get Opera 9 installed.  I have Opera 8.54, and I'm sure that I have installed things before, but I guess Linux (Ubuntu) is like a foreign language - if you don't use it frequently, you lose it quickly.

---

### Post by Vlatko on 2006-07-30
> **jfh said:**
> I have downloaded Opera 9, but when I click on it to try to install it, I get this message:
Could not open "opera_9.0-20060616.5-shared-qt_en_i386.deb"

Archive type not supported.

I'm not sure what this means.  Can anyone tell me how to get Opera 9 installed.  I have Opera 8.54, and I'm sure that I have installed things before, but I guess Linux (Ubuntu) is like a foreign language - if you don't use it frequently, you lose it quickly.
hi! i am new to linux as well. i think the answer to your package can be found here in this ubuntu desktop guide [https://help.ubuntu.com/pdf/ubuntu/C/desktopguide.pdf](https://help.ubuntu.com/pdf/ubuntu/C/desktopguide.pdf)

from what i saw a lot of people don't know about this guide, that is really sad cause it has a lot of essential tips newbies like you, and me, can use.

this is from the guide:

**Install/uninstall .deb files**

These files are Debian packages. The package files associated with Ubuntu have the .deb suffix because of Ubuntu's close relations with the Debian GNU/Linux distribution. You will need administrative privileges to install a .deb file (see the section called &#8220;Root And Sudo&#8221;). 

To install a .deb file, simply double click on it, and then select Install Package

Alternatively, you can also install a .deb file by opening a terminal and typing: 
```
sudo dpkg -i package_file.deb
```


To uninstall a .deb file, deselect it in your package manager, or type: 
```
sudo dpkg -r package_name
```

hope, I, finally helped someone out, not the other way around.:)

---

### Post by kadymae on 2006-07-30
You are going to have to go to the command line to get it installed.

But first open up Synaptic and make sure you have libstdc++5 files installed, or else it won't work.

After you have installed the libstdc++5 files or verified that they are already installed, open up the terminal and navigate to the directory where you have the Opera file downloaded.

Then, at the prompt, type:
> 
sudo dpkg -i opera_9.0-20060616.5-shared-qt_en_i386.deb


(Actually, you don't need to type out that whole opera file name.  Type the first 3 letters and then hit the tab key and it will auto complete the name.  Or you can just copy and paste that line into the terminal.)


Hit enter.

You'll be promted to type your admin password.

The install should go through at that point.

---

### Post by mscman on 2006-07-30
> **kadymae said:**
> 

You'll be promted to type your admin password.

The install should go through at that point.

Just to clarify, your 'admin password' is just your user password (assuming you're the user created during installation). Also, the above command only works if the .deb file is in your home directory. If it is on your desktop, when you open the terminal you need to run the command:
```
cd Desktop
``` before running the above command. This will change your working directory to the desktop.

---

### Post by kadymae on 2006-07-30
> **mscman said:**
> Just to clarify, your 'admin password' is just your user password (assuming you're the user created during installation). 

Yes, I should've been clearer about that.  I have 2 accounts on my machine.  My "everyday" account and my "admin" account.  I've run as the admin long enough to create my "everyday" account.

> 
[Also, the above command only works if the .deb file is in your home directory. If it is on your desktop, when you open the terminal you need to run the command:
```
cd Desktop
``` before running the above command. This will change your working directory to the desktop.

I told the OP to "navigate to the directory where you have the Opera file downloaded" before I said what to type at the command line to get the program installed, since I wasn't sure where Firefox defaults downloads to, or if the OP (like me) has created a special downloads directory.

However, I should've mentioned the cd (change directory) command.  ~sigh~

---

### Post by aysiu on 2006-07-31
Opera is in the Commercial repositories. Once you enable this set of repositories, you can easily install it and keep it up-to-date through point-and-click (Synaptic Package Manager or Adept).

Just do this: ```
sudo nano -B /etc/apt/sources.list
``` Paste (Shift-Insert) this line at the end ```
deb http://archive.canonical.com/ubuntu dapper-commercial main
``` Save (Control-X, Y, Enter) ```
sudo aptitude update
sudo aptitude install opera
```

---

