---
title: "NERO LINUX downloaded to desktop"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by Linuxmyatuk on 2006-01-07
Hello.. I have NERO Linux trial version downloaded and it is on my desktop. I am extremly new to linux and Ubuntu. I  NeroLinux-2.0.0.4-x86.deb on my desktop,  I found a how to and all it said was to download and run a sudo command.  Getting an error when running sudo command.  What do I need to do???? to get Nero to work properly.. In step by step details Please. 

Thanks in Advance
:p :p :p

---

### Post by bluefrog on 2006-01-07
you'd be better off installing k3b from synaptic. not using nero, can't help with it.

for sudo if your user is the one created at the install it should work with your password.

james

---

### Post by lothar_m on 2006-01-07
try this

```

sudo dpkg NeroLinux-2.0.0.4-x86.deb

```

then just enter your pass and let it roll

good luck

---

### Post by Linuxmyatuk on 2006-01-07
this command:
sudo dpkg NeroLinux-2.0.0.4-x86.deb

needs an action..

Will a command work with the program on your desktop??

---

### Post by bluefrog on 2006-01-07
sudo dpkg -i NeroLinux-2.0.0.4-x86.deb

james

---

### Post by Linuxmyatuk on 2006-01-07
michael@ubuntu:~$ sudo dpkg -i NeroLinux-2.0.0.4-x86.deb
dpkg: error processing NeroLinux-2.0.0.4-x86.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 NeroLinux-2.0.0.4-x86.deb

Does it matter that the file is on my desktop???  When running this command

---

### Post by s6dalane on 2006-01-07
cd /home/<user>/Desktop

And then run the command.

---

### Post by aysiu on 2006-01-07
I'm with Bluefrog on this ```
sudo apt-get install k3b
```

---

### Post by Perfect Storm on 2006-01-07
Open the terminal:

```

cd Desktop
sudo dpkg -i nerolinux-2.0.0.4-x86.deb

```

I both uses Nero and Gnomebaker ^^

Make sure you write it right, linux is case sensitive. So small "l" and small "n"

---

### Post by TimelessRogue on 2006-01-07
No, it shouldn't ... assuming that the file on your desktop is the downloaded Nero file, which you can move off to your downloads folder or delete it if you want.  You should find Nero listed as System Tools/NeroLINUX ... at least that's what I ended up with.

---

### Post by binks on 2006-01-07
slightly topic hijacking but what does nero offer that k3b doesnt

---

### Post by Linuxmyatuk on 2006-01-07
Artifical Intelligence thanks for reminding me that Linux is case sensetive..

Artifical and S6dalance here are some error messages that I received.. What do I do next??

michael@ubuntu:~/Desktop$ sudo dpkg -i nerolinux-2.0.0.4-x86.deb
Selecting previously deselected package nerolinux.
(Reading database ... 57381 files and directories currently installed.)
Unpacking nerolinux (from nerolinux-2.0.0.4-x86.deb) ...
dpkg: dependency problems prevent configuration of nerolinux:
 nerolinux depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 nerolinux depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
dpkg: error processing nerolinux (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nerolinux
michael@ubuntu:~/Desktop$

---

### Post by Perfect Storm on 2006-01-07
```

sudo apt-get install libgtk1.2 libglib1.2
```

---

### Post by s6dalane on 2006-01-07
sudo apt-get install libglib1.2 libgtk1.2

Then it installs the necessary package.

---

### Post by Linuxmyatuk on 2006-01-07
EXCELLENT...  KUDOS to ARTIFICAL and S6dalance..

Thank You..

---

### Post by Cesium on 2006-01-07
[QUOTE=binks]slightly topic hijacking but what does nero offer that k3b doesnt[/QUOTE]

I have the same question as Binks.

---

### Post by nalmeth on 2006-01-07
> Originally Posted by binks
slightly topic hijacking but what does nero offer that k3b doesnt

When I saw the new nero in action on my buddies windows laptop, and remembered you could get it for linux, I ran right home and installed...

only to find that it sucks, and is nothing like the windows version, which comes with a media player, and can go fullscreen to look like a dashboard. I was less than impressed. K3B is killer, gnomebaker is killer, nerolinux sux. My opinion.

---

### Post by Bone Down on 2006-01-16
well I was all for nero until I came across this post only to find out that it is not any different than K3B or GnomeBaker, I was hoping that it would offer dvd9 to dvd5, but it appears that in my windows version that is actually nero recode and not just nero itself so this is no good for me now... deleting the DL now.

---

### Post by nim278 on 2006-02-04
How about burning .NRG images?

---

