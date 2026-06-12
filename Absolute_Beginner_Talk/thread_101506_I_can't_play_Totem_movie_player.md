---
title: "I can't play Totem movie player"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by Singachea on 2005-12-09
Hi Experts,

I'm very quite new to Linux. I've installed Ubuntu; however i can't play some moive. It say:
[COLOR="Red"]
There were no decoders found to handle the stream in file "file:///home/threamy/Desktop/12the_reason.wma", you might need to install the corresponding plugins[/COLOR]

What should i do?

---

### Post by Qrk on 2005-12-10
Have you installed the non-free codecs? A very good How-to is in the Ubuntu Help 

System-->Help-->Starter Guide-->Applications-->Music and Movies

---

### Post by Singachea on 2005-12-10
[QUOTE=Qrk]Have you installed the non-free codecs? A very good How-to is in the Ubuntu Help 

System-->Help-->Starter Guide-->Applications-->Music and Movies[/QUOTE]


What is [COLOR="Red"]non-free codecs[/COLOR]? I know nothing about it since i'm quite new. I try to find some instruction in HELP, but I can't found the guide to install those codecs.

---

### Post by Qrk on 2005-12-10
Ubuntu only includes open source software in the CD you downloaded. Unfortunatly, many things, such as mp3, wma, etc are closed sourced file formats. So if ubuntu included them, it could possibly be illegal. 

You can read about them: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats).

Here is what you should do:

Paste into the terminal (applications-->accessories-->terminal)

```
sudo gedit /etc/apt/sources.list
```

In the window that pops up, remove the # from each line that includes an address (the single # rows, not ##)

Save that file. 

Now type into the termial:

```
sudo apt-get update
```

You are ready to install the codecs. Copy this command into the terminal:

```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
```

This should give you most file formats... however some will still not work. To get these last few, install win32codecs. 

You can download the package here:

[ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)

Now, use the command

```
cd /path/to/savelocation
```

For instance if you saved it in your desktop, use /home/username/Desktop or just ~/Desktop. (~/ is a shortcut to your /home directory)

Now you can install it with the command

```
sudo dpkg -i w32codecs_20050412-0.0_i386.deb
```

Thats it, you should be done.

---

### Post by Singachea on 2005-12-10
I try your method:

[COLOR="Red"]sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg[/COLOR]


But the result is:

[COLOR="Blue"]threamy@ream:~$ sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package gstreamer0.8-plugins has no installation candidate[/COLOR]

What should i do?

---

### Post by Gray. on 2005-12-10
Use [EasyBreezy]("http://dev.realistanew.com/easybreezy/easybreezy0.33-alpha.tar.gz") to install the non-free codecs and other things that you might find handy. Instructions on how to install it are included in the file.

---

### Post by Singachea on 2005-12-10
I'm using version 5.04

I don't understand what you mentioned above

---

### Post by prizrak on 2005-12-10
[QUOTE=Singachea]I'm using version 5.04

I don't understand what you mentioned above[/QUOTE]
I'd suggest upgrading to 5.10 there are some automated programs to get it running with the non-free codecs. This is the guide for upgrading without having to reinstall [http://www.ubuntuforums.org/showthread.php?t=100840&highlight=upgrading+hoary+breezy](http://www.ubuntuforums.org/showthread.php?t=100840&highlight=upgrading+hoary+breezy)
Then you can use the program that was suggested to you.
If you don't want to upgrade a great place to take a look at is [www.ubuntuguide.org](www.ubuntuguide.org) it helped me alot in the newbie days :)

---

### Post by Qrk on 2005-12-10
I'm sorry, I didn't realize you were using 5.04. My instructions were for 5.10, and 5.10 has the help in the help file. 

You can still get non-free codecs for 5.04 if you follow this link. 

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

Some things may not install correctly because its old. You have to get win32codecs yourself (use my previous post for these)

---

### Post by Singachea on 2005-12-11
Thank for your comments; now i already installed the verion 5.10. However, I still can't play movie even i followed your steps above.

It still say: 

[COLOR="Red"]There were no decoders found to handle the stream, you might need to install the corresponding plugins[/COLOR]

What should I do?
I'm abit upset with Ubuntu now coz i can't do anything.

---

