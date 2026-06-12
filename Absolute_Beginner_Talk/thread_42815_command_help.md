---
title: "command help"
date: 2005-06-19
forum: Absolute Beginner Talk
---

### Post by mcflyxc23 on 2005-06-19
I am new to all of this and am using one of the linux guides to navigate myself through this amazing language.  I am trying to navigate in terminal to my /home/user/Desktop folder and I keep getting errors when trying to cd.

ryan@networkryan:/$ /home
bash: /home: is a directory
ryan@networkryan:/$ cd /home
ryan@networkryan:/home$ ls
ryan
ryan@networkryan:/home$ cd /ryan
bash: cd: /ryan: No such file or directory
ryan@networkryan:/home$


Does anyone have any advice for me?  ALso, is there information or more help on installing my programs?  Thanks.

---

### Post by TheRealEdwin on 2005-06-19
I think its because you start the terminal in your home directory and not in your root (c:\ for windows term) that is confusing you. Try this:

```
cd ~/Desktop
```

That should take you to the desktop no matter where you are. To break it down ~ means start from the home folder then inside the home folder look for another folder called "Desktop" and then open it. You obviously already know what cd is so I wont explain it.

---

### Post by tread on 2005-06-19
> 
bash: /home: is a directory
ryan@networkryan:/$ cd /home
ryan@networkryan:/home$ ls
ryan
ryan@networkryan:/home$ cd /ryan
bash: cd: /ryan: No such file or directory

Also, the problem above is, when you cd /ryan, you are starting again from the root. What you want to do there is 

cd ryan

since ryan is in home, and you are in home too.

Does that make sense?

---

### Post by estel on 2005-06-19
Basically, if you start a path with a / , it's always taken as an absolute path, rather than a relative path...

---

### Post by mcflyxc23 on 2005-06-19
yes thank you very much....how do i go about installing applications now?  Lets say I am in the directory I wanted now and want to install winrar 

ryan@networkryan:/home$ cd ryan
ryan@networkryan:~$ ls
132102865_l.jpg
Desktop
Gilmore.Girls.-.The.Ultimate.Soundtrack.Vol.1.(2CD-45Tracks).[kmn-music.de]
Kingdom.Of.Heaven.-.Soundtrack.-.2005.[[www.mixermusic.net].rar](www.mixermusic.net].rar)
One.Tree.Hill.-.Enhanced.Soundtrack.Vol.1.(2CD-36Tracks).-.by.KMN.-.[[www.lokitorrent.com]](www.lokitorrent.com])
rarlinux-3.5.b5.tar.gz
rp8_linux20_libc6_i386_cs1_rpm
space_report.txt
TransGaming_Drive
ubuntu5.04.tar.gz
usr.tar.gz
usr.tar.gz_FILES
ryan@networkryan:~$ file usr.tar.gz
usr.tar.gz: gzip compressed data, was "fr.8761.0.usr.tar", from Unix
ryan@networkryan:~$

this is what's on the desktop, how do I go about unzipping and installing realplayer or itunes or winrar?  Any more help would be greatly appreciated.

---

### Post by tread on 2005-06-19
Mostly, windows programs will not work on Linux, but you will find their equivalent.
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=33183](http://ubuntuforums.org/showthread.php?t=33183)

---

### Post by estel on 2005-06-19
tread: I think that that was the Linux build of winrar (oxymorons indeed). Well... not Winrar, but it's a package available from their site.

You won't really need it, Ubuntu comes with a good enough extracter thing that will handle pretty much all zipped things. 

If you want to install it, then bear in mind that it's command prompt only.

You can install it by opening it, extracting the files (if the GUI doesn't work, then there's the command ```
gunzip
``` that will work (read the info page ```
man gunzip
```) that will unzip the installation. I don't know that the installation thing is like....

---

