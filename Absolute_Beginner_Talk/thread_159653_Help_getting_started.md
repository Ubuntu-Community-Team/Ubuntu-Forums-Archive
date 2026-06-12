---
title: "Help getting started?"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by iplgecko on 2006-04-13
Hi im really new to linux and im trying to understand the basics of how every works, how things run, install etc. But when I read turorials on how to's for installs and other things I just don't get. So I was wondering if anyone here who has a basic amount of knowledge of linux could add my msn and help me step by step now and again with anything? edit: [email]jjsnax@hotmail.com[/email] , I'd enourmously appreciate it.

- Jason.

---

### Post by Sef on 2006-04-13
I would start by looking at what you want or need to install and start that way.  Start a thread saying "I want to install x. How do I do it?"

Three ways to install:

1) Add Applications (under Applications)

2) Synaptic Package Manager (under System > Administration)

3) The Terminal (Applications > Accessories > Terminal)  
     a) With the Terminal, you would do sudo apt-get install (program name).  For apps in the respositories.
     b) dpkg -i  (program name).  For .deb apps  For applications that end in .deb.
     c)  source a.k.a. compiling (configure, make, make install) For when you can't do the other two.

---

### Post by frodon on 2006-04-13
[http://ubuntuforums.org/showthread.php?t=153118](http://ubuntuforums.org/showthread.php?t=153118)

---

### Post by helgez on 2006-04-13
When I was new to Ubuntu I had great help from 

[http://easylinux.info/wiki/Ubuntu]("http://easylinux.info/wiki/Ubuntu")

And now ther's of course Automatix. To install type the following lines in the terminal window, each followed by <enter>:

sudo apt-get install xterm
wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb]("http://beerorkid.com/automatix/automatix_5.7-3_i386.deb")
sudo dpkg -i automatix_5.7-3_i386.deb

Then choose

 Applications -> System Tools -> Automatix

In Automatix you can choose to for example install mp3 playback capability.

Good luck!

---

### Post by iplgecko on 2006-04-13
Ok ill give them a shot , thanks for your help and thanks for your super quick replys guys :D.

---

### Post by iplgecko on 2006-04-13
Also one other thing and im sorry if it's off topic but on my desktop theres a shortcut called "hda1" and im guessing that my 1st partition (windows xp) but I cannot access it which is fair enough, it says I do not have permissions necessary  but nor can I delete the shortcut. It just says I have to unmount it the volume.

---

### Post by taurus on 2006-04-13
In your /etc/fstab, you may want to add "umask=0222" after the "defaults" if you want to read it so it would look something like
```

/dev/hda1  /media/hda1  ntfs  defaults,umask=0222  0  0

```

---

### Post by iplgecko on 2006-04-13
Ok ill give that a try and thanks very much for the fast replys.

---

### Post by iplgecko on 2006-04-13
I tried to install automatix but when I pasted this following command in the terminal "sudo dpkg -i automatix_5.7-3_i386.deb" I get " cannot access archive: No such file or directory".

EDIT: Nvm I fixed it, I had to put "cd Desktop" first. Im learning already :D

---

