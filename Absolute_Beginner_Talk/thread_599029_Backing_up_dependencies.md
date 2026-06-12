---
title: "Backing up dependencies"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by subferno on 2007-10-31
I am new to Ubuntu, hence my post in this thread. How do I back up drivers, programs, and dependencies onto another location for later usage?

Installing Ubuntu for the first time, I find myself going online to get wifi drivers for my MacBook Pro. I find useful programs like AWN and to use them, I was told to go through the terminal and download the dependencies, do apt-get, install, make, etc. To enable my graphics driver, I have to enable restricted drivers, wherever they are downloaded from.

What if I want to back all those files up so that next time, I don't have to download them. They should be readily available. I don't understand what all this apt-get, make, install, etc means.

Being a windows user for 10+ years, I understand what the typical files are. On Ubuntu, I don't understand what a program consists of anymore. What are these dependencies I am downloading? Why aren't they bundled with the program to make it accessible?

Thanks

---

### Post by Paul820 on 2007-10-31
Get yourself AptOnCD, it will make an ISO out of all the programs you have downloaded and even burn the disk for you. I use it and it saves loads of time. It **won't** reinstall them all for you when you write it back to your computer.  What i do is make a list of all the packages i have installed by doing this command in the terminal
> sudo ls /var/cache/apt/archives > packages.txt
so i know what i had installed.

EDIT: The packages.txt file gets put in your home folder.

---

### Post by subferno on 2007-10-31
Thanks for the response Paul. AptOnCD sounds like what I need. What about drivers? Do they get backed up as well?

---

### Post by oldos2er on 2007-10-31
Wecome to Linux. Suggested reading: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) and [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by Paul820 on 2007-10-31
It will only back-up those programs that have been downloaded though synaptic package manager and stored in the cache folder. Those other programs that you download from the net that are .deb files you will have to include them manually. AptOnCD gives you the option of adding more files to the list that it makes by selecting files from other places on your hard-disk. I don't think it will add anything other than .deb files so .tar or .zip files etc, you will have to keep safe by burning them to another cd or something.

---

