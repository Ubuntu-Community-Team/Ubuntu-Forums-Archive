---
title: "How do I run the IpodLinux installer?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2007-10-30
I have downloaded the IpodLinux installer for linux, and cant get it to run?

I have made et executable and still it wont run?

I have done as the guide says, simply double click or run it from terminal.. but nothing happens, and in terminal I get "command not found".

Anyone know how I can run this installer? Because now I installed IpodLinux  from OSX and the partition is still HFS+ and read Only, so I cant add mp3's to it anymore.

Any ideas?

---

### Post by jonobr on 2007-10-30
Im guessing your running from the wrong directory,

If its on your desktop and you open the terminal
cd Desktop

do an ls command and see its there,
execute it by typing ./ipodinstaller
If that fails, its probably permissions related 
get ls -l ipodinstaller 
and post results back here, someone will post a chmod for you then

---

### Post by Incense on 2007-10-30
Have you considered rockbox? Much better then IpodLinux IMO.

[http://www.rockbox.org/]("http://www.rockbox.org/")

---

### Post by aktiwers on 2007-10-30
Im in the right dir..  This I do know :) 
But the installer simply wont run?

```
aktiwers@HAL:~$ cd Desktop/ipodlinux-installer-2.2l/
aktiwers@HAL:~/Desktop/ipodlinux-installer-2.2l$ sudo ./installer.sh
[sudo] password for aktiwers:
sudo: ./installer.sh: command not found
aktiwers@HAL:~/Desktop/ipodlinux-installer-2.2l$ installer
bash: installer: command not found
aktiwers@HAL:~/Desktop/ipodlinux-installer-2.2l$ sudo installer 
sudo: installer: command not found
aktiwers@HAL:~/Desktop/ipodlinux-installer-2.2l$ /installer
bash: /installer: No such file or directory
aktiwers@HAL:~/Desktop/ipodlinux-installer-2.2l$ sh installer
installer: 1: Syntax error: newline unexpected (expecting ")")
aktiwers@HAL:~/Desktop/ipodlinux-installer-2.2l$ sh /installer
sh: Can't open /installer
aktiwers@HAL:~/Desktop/ipodlinux-installer-2.2l$ sh ./installer
./installer: 1: Syntax error: newline unexpected (expecting ")")
aktiwers@HAL:~/Desktop/ipodlinux-installer-2.2l$ sudo sh ./installer
./installer: 1: Syntax error: newline unexpected (expecting ")")
aktiwers@HAL:~/Desktop/ipodlinux-installer-2.2l$ ls
installer
aktiwers@HAL:~/Desktop/ipodlinux-installer-2.2l$
```

I will have al look at Rockbox, I did read about it and heard it sucks batteri..   I will have a look anyways.. does it run on 4gb Ipod Mini?

---

### Post by eapache on 2007-10-30
once in the directory, use```
sudo ./installer
```sudo for root, ./ to tell it that it's a script, and the filename which is installer, not installer.sh. Your first try of ./installer.sh was closest.

---

### Post by aktiwers on 2007-10-30
Thanks, but I did try that earlier.. just didn't remember.. but I overlooked this error message... 

```
aktiwers@HAL:~/Desktop/ipodlinux-installer-2.2l$ sudo ./installer
[sudo] password for aktiwers:
./installer: error while loading shared libraries: libcrypto.so.0.9.7: cannot open shared object file: No such file or directory
aktiwers@HAL:~/Desktop/ipodlinux-installer-2.2l$
```Though, I did search for the libs, but dont seam to be able to find them?

---

### Post by jonobr on 2007-10-30
Your missing the libraries that this installs with.

Ill try the install myself later (as Im interested in installing this myself now :-) )
If I get a success Ill post here including lib versions


Also , heres an interesting link
[http://mikesubuntu.blogspot.com/2007/09/how-to-install-ipodlinux-on-your-ipod.html](http://mikesubuntu.blogspot.com/2007/09/how-to-install-ipodlinux-on-your-ipod.html)

---

### Post by aktiwers on 2007-10-30
Haha thanks for the link.. sadly I already bin there before I posted this.
The problem is that I have an HFS+ filesystem on my Ipod.

Actually, Im already running Linux on it. I installed it through the OSX installer on my Mac, but for some reason the filesystem is only Read/write.

Not even Sudo kan change it, nor can he write to it. So all I have now is an Ipod, with Linux (yippy!), but no Mp3's. :(

Thats why I wanted to install it from Ubuntu, so I could use better filesystem.

Though I did try the script earlier today anyhow, but it quit doe to the filesystem.

Then I went to try RockBox, it really looks nice too. But the Rockbox installer cant find my Ipod (device path), and even though I give it the right path, it keeps telling me its not the right path... Argh!

Maybe because Im now runinng the Linux OS on it? 

But I look forward
to see how you progress, I can say even though I dont have my mp3's on it, there are still games and other stuff to do.. heh.. but oh well..

Let me know :)

---

