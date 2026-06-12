---
title: "**HELP** How do you get RTL8187B Wireless card working?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-02-23
I've just installed Ubuntu 7.10 I don't know anything. (I used to have Vista) I don't know what to do. I've read things about it.. completey stuck. Don't know what they were going on about :S

I have RTL8187B Wireless LAN card built in my laptop.

How do you install the driver? Isn't it like Windows where you just click on an .exe?

So please please help me :)

Thanks in advance!

Tom

---

### Post by lncoll on 2008-02-23
Take a look at:
[This page]("http://danmarner.blogspot.com/2008/01/rtl8187b-linux-native-driver-works-on.html")

It is not easy, and I have not that card, but if you try and have problems post them and try to help you.

---

### Post by Tom--d on 2008-02-23
Thanks for the link.. 
but, as I don't know anything, nothing at all.. what is this and what does it mean?

3 run the script makedrv with sudo

sudo? Where is that? 

When I click on makedrv. What do I do? Run in terminal, or run? 

thanks

---

### Post by lncoll on 2008-02-23
Ok, start from the beginning.
  In Linux there is a special user know as root, this user is the system administrator and is the one that can modify system files.
  In Ubuntu ( a Linux distribution you know ) the user root is disabled, this is a way to get more security in the system, but now, what if a system file must be modified? there are some ways, the best is the command sudo, this command allows you to execute a command as root, the same that "runas" in other OS.
  Now to install a driver. Here drivers are called modules or mods. because are not really drivers, are modules that work with the kernel.
  The module must be copied in its place and enabled,  or many times compiled and installed, all this is done from console, not from the gui, and of course as root, with sudo.
  First download the driver in a folder, and then open a console Applications -> Accesories -> Terminal . Look for the downloaded driver, this can be done with ls , the same as dir in other OS, cd to the folder where is downloaded if not in your folder with cd, ej.  
```
user@host ~$ cd downloads
```
and uncompress it 
```
user@host ~/downloads$ tar -xvfz driverfile.tgz
```

If you are still reading stop for a while, and read some instructions with

```
user@host ~/downloads$ man ls
user@host ~/downloads$ man tar
user@host ~/downloads$ man sudo
```

In a few minutes I continue with a new post, my wife is calling me :p

---

### Post by Tom--d on 2008-02-23
Thank you for helping me :)

I'm starting to under stand it :)

---

### Post by lncoll on 2008-02-23
Ok, I'm back again.
Sorry if my answers are not fast, but my English is not good.

To execute a file in Linux from the console or a launcher you need two two things 
**1 - The file in in your path**.
Only files in the path are executed if you do dot say where the file is, ecexute:

```
user@host~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

And you see where the executables use to be, if the file to execute is not in the path but is in the actual folder you can do ./filename  the first two characters ./ say the shell you want to execute a file in the actual folder, this way does not need to be in the path

**2 - Execution attibute.**
In linux the extension does not say the filetype, so extensions like .exe or .com does not mean. Here you have attributes one of them is the executable attribute and says "this file is executable" does not mean if is a binary or a script.
The command chmod changes modes ( attributes ) with chmod +x filename a file is done executable.
More in :
```
user@host~$ man chmod
```

Hopefully the files you have uncompressed use to have attributes set, so when the page in the link i sent you says

```
sudo ./makedrv
```

Means: execute the file makedrv in your folder as root.

I hope this can help you to understand a little how to do thinks in Linux, and hopefully install the module for your wireless. When done you have the command ifconfig that shows the configuration for your network interfaces.

If you can install the module ( or not ) and have more problems, please post them.
And remember the man command helps a lot :)

---

### Post by Tom--d on 2008-02-23
Im stuck..

When I do this

sudo ./makedrv

This comes up

sudo: ./makedrv: commabd not found

:S

What does it mean?

---

### Post by lncoll on 2008-02-23
If you get command not found is because the file is not executable, try doing it executable with 

```
user@host~$ chmod +x makedrv
```

---

### Post by Tom--d on 2008-02-23
It comes up with..

chmod: cannot access 'makedrv': no such filr or directory

What am I doing wrong??

What do I need to do to make this work. Can you just tell me what to type. I dont mind if it dont make sense :P

Thanks!

---

### Post by lncoll on 2008-02-23
Well lets try, you must be in console in the same directory as the one where the downloaded file is.

Frist of all Linux is case sensitive so Makedev is not the same as makedev.

to be sure of this type:
```
luis@negro:~/downloads$ ls rtl*
rtl8187b-modified-dist.tar.gz

```
If the result is as the one shown it is ok.
now uncompress the file 
```
luis@negro:~/downloads$ tar -xvf rtl8187b-modified-dist.tar.gz 
rtl8187b-modified/
rtl8187b-modified/makedrv
rtl8187b-modified/ReadMe.txt
rtl8187b-modified/install
rtl8187b-modified/rtl8187/
rtl8187b-modified/rtl8187/r8180_rtl8225z2.c
rtl8187b-modified/rtl8187/install
rtl8187b-modified/rtl8187/copying
rtl8187b-modified/rtl8187/Modules.symvers
rtl8187b-modified/rtl8187/r8187.o
rtl8187b-modified/rtl8187/ieee80211.h
rtl8187b-modified/rtl8187/r8180_93cx6.h
rtl8187b-modified/rtl8187/.tmp_versions/
rtl8187b-modified/rtl8187/.tmp_versions/r8187.mod
rtl8187b-modified/rtl8187/ieee80211_crypt.h
rtl8187b-modified/rtl8187/.r8180_rtl8225z2.o.cmd
rtl8187b-modified/rtl8187/r8180_rtl8225.o
rtl8187b-modified/rtl8187/r8187.mod.c
rtl8187b-modified/rtl8187/r8180_rtl8225.c
rtl8187b-modified/rtl8187/.r8187.mod.o.cmd
rtl8187b-modified/rtl8187/tags
rtl8187b-modified/rtl8187/license
rtl8187b-modified/rtl8187/r8187.h
rtl8187b-modified/rtl8187/r8180_wx.o
rtl8187b-modified/rtl8187/r8180_93cx6.o
rtl8187b-modified/rtl8187/r8180_hw.h
rtl8187b-modified/rtl8187/r8180_rtl8225z2.o
rtl8187b-modified/rtl8187/r8180_wx.c
rtl8187b-modified/rtl8187/readme
rtl8187b-modified/rtl8187/r8180_93cx6.c
...
...

```

As you see this creates the directory rtl8187b-modified
cd to this directory, and do makedrv and wlan0up

```
luis@negro:~/downloads$ cd rtl8187b-modified/
luis@negro:~/downloads/rtl8187b-modified$ sudo ./makedrv 
luis@negro:~/downloads/rtl8187b-modified$ sudo ./wlan0up 

```

With this the wireless must start to work.

---

### Post by Tom--d on 2008-02-23
Got it :)

Thanks!!!!!!!!!!!!!!!!!!!!!!!!!!

but 2 more questions..

Do I need AVG free? If yes, how do I install it?

Also
I need a short cut to
sudo ./wlan0up

How do I create one? 
And can I get that to start up when ubuntu starts?  like a link. (Like startup on windows)

Thanks!! :)

---

### Post by Tom--d on 2008-02-24
:(

The driver is too buggy and doesn't allow WEP key. So I can use that.

I saw.. NDISwrapper + Windows 98 driver works. Don't really know what I'm doing. 

Do I have to uninstall the rtl8187B driver before I install NDISwrapper?

Thanks.
Tom

---

