---
title: "No way to remove Java"
date: 2012-02-12
forum: Any Other OS
---

### Post by spiralciric on 2012-02-12
I'm using Mint 11, but since it is ubuntu based, it should be a same thing.
sun-java is preinstalled and I want to remove it. However, it is determined to install openjdk, so I get no free space by trying to purge it.
I even tried apt-get purge --no-download and --no-install-reccomends, but it always wants to install openjdk.
I tried even that and than trying to remove openjdk, but it then wants to install sun-java.
Any ideas how this annoyance can be solved?

---

### Post by winh8r on 2012-02-12
Have a look here:


[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

this might help you.

---

### Post by Perfect Storm on 2012-02-12
Moved to Other OS/Distro Talk.

---

### Post by spiralciric on 2012-02-12
Thanks winh8r but that does not work. Any other ideas?

---

### Post by Gremlinzzz on 2012-02-12
> **spiralciric said:**
> I'm using Mint 11, but since it is ubuntu based, it should be a same thing.
sun-java is preinstalled and I want to remove it. However, it is determined to install openjdk, so I get no free space by trying to purge it.
I even tried apt-get purge --no-download and --no-install-reccomends, but it always wants to install openjdk.
I tried even that and than trying to remove openjdk, but it then wants to install sun-java.
Any ideas how this annoyance can be solved?

what is the purpose to get free space?
what do you mean it wants to install one or the other>are you talking about updates

---

### Post by spiralciric on 2012-02-12
Purpose is preparing mint for asus eee 2G with only 2GB of SSD. There is also another benefit in speed with removing all the vms that I don't need.
No updates. Do in mint 11 sudo apt-get purge sun-java, and it will go and install openjdk instead. Do that, and do sodu apt-get purge openjdk, and it will install sun-java. Its catch22. I dont want to, but I might go to bin and do rm -rf on any java I see.

---

### Post by Gremlinzzz on 2012-02-12
Does mint 11 have Synaptic Package Manager if so use that to remove Java
or 
sudo apt-get remove sun-java6-jre sun-java6-plugin

:popcorn: I think that Medibuntu repository is the one that has sun Java packages,so you might try un checking it

---

### Post by spiralciric on 2012-02-12
Synaptic nor remove work. There must be something somewhere ubuntu or debian based that does not allow this to happen.

---

### Post by winh8r on 2012-02-12
java is needed by some process on your system and when you remove a functioning instance of java , the system looks for it , cannot find it and therefore update manager or whatever locates Java for installation in order to keep system functioning.


If you are looking for a very small installation then use Ubuntu minimal install from here:

[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")


I know it is not Mint, but it is Ubuntu.

---

### Post by spiralciric on 2012-04-05
That is hardly a solution. I would like to know more about Ubuntu, and I am not clear why it must have some version of java installed, and where it tells it to. The other thing is that this is opposite of linux philosophy which is: you can customize however you want. Does anyone has a clue why is this happening?

---

### Post by spiralciric on 2012-04-05
There are a lot of examples like this one: one would be try to uninstall mplayer, in installs mplayer2. I dont want mplayer!

---

### Post by Pjotr123 on 2012-04-06
> **spiralciric said:**
> Thanks winh8r but that does not work. Any other ideas?

It *does* work. Simply do exactly what the how-to says.
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I know, because I wrote that how-to and have applied it myself dozens of times, on dozens of different computers. Both in Ubuntu and in Linux Mint. 

Nothing to it; simply copy/paste a bunch of terminal commands. Easy as can be.

If you don't like using the terminal, then there's also the Duinsoft solution: [http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

---

### Post by spiralciric on 2012-04-06
Well, I thanked you first time, but there is no /opt/java on Mint. I will go and manually delete every java and jvm on hdd, that should do the trick. Still that does not answer the question, where is config file that requests something other to be installed if one thing is chosen for removal.

---

