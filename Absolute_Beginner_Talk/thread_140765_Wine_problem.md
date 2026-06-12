---
title: "Wine problem?"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by evilc on 2006-03-06
Firstly I must say I just installed Ubuntu and it found everything and runs like a bird. (one happy chappy here)\\:D/ . 
I have installed bits/pieces with Synaptic but can't get Wine to install run keeps saying fault in recieving. What other way can I get it.:confused: 

Please remember I'm a newb and not familiar with Linux commands,
 thanks.

---

### Post by aysiu on 2006-03-06
Can you go to Applications > Accessories > Terminal and post back here the output of these commands? ```
sudo apt-get update
sudo apt-get install wine
```

---

### Post by evilc on 2006-03-07
Here it is I did the d/l the same before. Claims it's installed but I can't find it:confused: 

Thanks Clive


oops file has not been recieved ? sent it by attachement. The commands appeared to run without any hitch.

---

### Post by aysiu on 2006-03-07
It probably looked something like this, right? ```
evilc@ubuntu:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
evilc@ubuntu:~$
```

As to how to use it, this excerpt from the Ubuntu User Guide PDF may help: > A bit about Wine... I don't know how it works, but it does seem to work with a lot of simple Windows programs. I'll show you how I get Filezilla to work in Linux, as an example.

Assuming I've already enabled extra repositories, first, I install Wine:
sudo apt-get update
sudo apt-get install wine

Then, I download the setup.exe file for Filezilla. When I double-click on it, Wine will try to open the file. Then, the installer appears, just as if I were using Windows. Instead of installing Filezilla to C:\Program Files\Filezilla\, I'm going to override the default installation location and install it to z:\home\username\.wine\drive_c\Program Files\Filezilla. For some reason, z:\ is what Wine calls my Ubuntu partition.

Then, I set up a launcher (on the panel or in the menu) for the command wine &#8220;z:\home\username\.wine\drive_c\Program Files\Filezilla\Filezilla.exe&#8221;

That's it. Now when I click on that launcher, Filezilla will load up.

---

### Post by evilc on 2006-03-07
Thanks that's what I got will try it out when I get my other problem fixed, (see post  Nautilus fails to open)

Clive

---

