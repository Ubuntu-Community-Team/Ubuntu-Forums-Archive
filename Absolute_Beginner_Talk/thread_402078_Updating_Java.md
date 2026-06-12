---
title: "Updating Java"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by x-ray vision on 2007-04-05
According to [this](http://torrentfreak.com/how-to-install-limewire-on-ubuntu-610-edgy-eft/) guide on installing Limewire in 6.10, if I have a version of Java older than 1.5, it must be updated. 

I followed the instructions for updating and typed the following in to the terminal :sudo apt-get install sun-java5-jre sun-java5-plugin.

I got this message:  

[b]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  java-common libltdl3 odbcinst1debian1 sun-java5-bin unixodbc
Suggested packages:
  equivs sun-java5-fonts ttf-sazanami-gothic ttf-sazanami-mincho libmyodbc
  odbc-postgresql libct1
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  java-common libltdl3 odbcinst1debian1 sun-java5-bin sun-java5-jre
  sun-java5-plugin unixodbc
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory[/b]

How do I get this to work?

---

### Post by ThrobbingBrain66 on 2007-04-05
I usually get the error when I have Synaptic open and try to install  packages with the command line.  Make sure that Synaptic (or Adept if you use Kubuntu) and Add/Remove programs are closed.  Then do a ```
sudo apt-get update
``` and try to install the packages again.

---

### Post by x-ray vision on 2007-04-05
Well, I don't even know what Synaptic is, so I don't think I had it open, but I typed "sudo apt-get update" into the the command bar like you told me and then tried updating Java and it seems like it downloaded it. Now how do I accept the licensing agreement?

---

### Post by mikeyphi on 2007-04-05
> **x-ray vision said:**
> Well, I don't even know what Synaptic is, so I don't think I had it open, but I typed "sudo apt-get update" into the the command bar like you told me and then tried updating Java and it seems like it downloaded it. Now how do I accept the licensing agreement?

Look here for a good guide! [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_v5.0.11_for_Firefox32](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_v5.0.11_for_Firefox32)

---

### Post by ThrobbingBrain66 on 2007-04-05
If I remember right, you have to hit the Tab key to get the right focus, then you can accept the agreement.

btw, Synaptic is the GUI for installing packages: System > Administration > Synaptic

EDIT:  You also have to make your new java default by entering
```
sudo update-java-alternatives -s java-1.5.0-sun
``` in to a terminal.

---

### Post by x-ray vision on 2007-04-05
Damn! I closed the licensing agreement box thinking maybe that's all I had to do and now it won't let me start from scratch. Is there any way to do this over again?

---

### Post by x-ray vision on 2007-04-05
Now when I type in: "sudo apt-get update "   I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by x-ray vision on 2007-04-05
I guess that means type  'dpkg --configure -a'  into the terminal? When I do, I get this message:

requested operation requires superuser privilege

---

### Post by DougieFresh4U on 2007-04-05
> **x-ray vision said:**
> I guess that means type  'dpkg --configure -a'  into the terminal? When I do, I get this message:

requested operation requires superuser privilege

**sudo dpkg --configure -a**

---

### Post by ThrobbingBrain66 on 2007-04-05
> **x-ray vision said:**
> I guess that means type  'dpkg --configure -a'  into the terminal? When I do, I get this message:

requested operation requires superuser privilege

just add 'sudo' in front of the command:

```
sudo dpkg --configure -a
```

---

### Post by mikeyphi on 2007-04-05
> **x-ray vision said:**
> I guess that means type  'dpkg --configure -a'  into the terminal? When I do, I get this message:

requested operation requires superuser privilege

type
sudo dpkg --configure -a


sudo gives you superuser privilege.....you will be asked for your password

---

### Post by x-ray vision on 2007-04-05
Thanks guys! I don't know how you guys figured all this crap out!

I Googled for all of the beginners guides online, and they don't seem to be for beginner beginners. There's an "Ubuntu for Dummies" book coming out in May and I plan on getting that. Are there any other particular books you guys can recommend so I can start figuring out how to do these things on my own? I really appreciate all your help.

---

### Post by DougieFresh4U on 2007-04-05
> **x-ray vision said:**
> Thanks guys! I don't know how you guys figured all this crap out!

I Googled for all of the beginners guides online, and they don't seem to be for beginner beginners. There's an "Ubuntu for Dummies" book coming out in May and I plan on getting that. Are there any other particular books you guys can recommend so I can start figuring out how to do these things on my own? I really appreciate all your help.

**Beginning Ubuntu Linux** and** Ubuntu Unleashed**.      Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by ThrobbingBrain66 on 2007-04-05
Besides all the links listed above (psychotcats.net is beginner gold) just come around the forums and read peoples support posts.  You don't have to answer...just read and learn.  You'll be a pro in no time.

---

