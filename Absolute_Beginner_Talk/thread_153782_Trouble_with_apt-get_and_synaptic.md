---
title: "Trouble with apt-get and synaptic"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by LissoSchwartzo on 2006-04-01
Just switched to Ubuntu 5.10, because i thought it would be easy to install and run Gnucash. Ubuntu was installed on an old laptop that has never been connected to the internet--the install was easy(from cd), no problems.  I downloaded the file: gnucash-common_1.8.10-18_all.deb, put it on a thumbdrive and transferred it to the laptop with Ubuntu.  If i use the command: sudo apt-get install gnucash..., i always get the same message: couldn't find package gnucash....

I have tried every variation on the package name with the apt-get install--gnucash, gnucash- common, gnucash-common_1.8.....etc and the resullt is the same. I have  edited  /etc/apt/sources.list, commenting out the universe/multiuniverse. I have tried to use synaptic--have gone into the software preferences and added Universe and Multiuniverse. The result has been that synaptic doen't recognize gnucash.  

I downloaded a source tarball of gnucash-1.8.9 and enter ./configure--it runs until i need a dependency, which i download, install and ./configure again until i find i'm missing another file. 

I'm a novice at this, but not a complete novice, I've used Slackware, Redhat and Mandrake. I liked Slackware the best, but i have been advised it is too difficult to install gnucash on Slackware, so i swithced to Ubuntu. What i need is gnucash on this old laptop to keep track of some part time business i have. I have no plans of connecting this old computer to the internet, so any software put on it comes from cd or thumbdrive. I have usually been able to install what i want on Slackware--i've wasted an afternoon trying to make this work, so far Ubuntu is less user friendly than Slack. Any advice would be appreciated.

thanks

---

### Post by Sutekh on 2006-04-01
You can't use apt-get that way, it needs a repository list to install software, just copying a file over doesn't work.  You'd have to create a local repository to install that .deb through apt-get, which is more work than neccessary

You *can* install that .deb file using
```
sudo dpkg -i gnucash-common_1.8.10-18_all.deb
```
However you will have to manually download and install any dependant packages aswell.

---

### Post by gpeck157 on 2006-04-01
[QUOTE=LissoSchwartzo]Just switched to Ubuntu 5.10, because i thought it would be easy to install and run Gnucash. Ubuntu was installed on an old laptop that has never been connected to the internet--the install was easy(from cd), no problems.  I downloaded the file: gnucash-common_1.8.10-18_all.deb, put it on a thumbdrive and transferred it to the laptop with Ubuntu.  If i use the command: sudo apt-get install gnucash..., i always get the same message: couldn't find package gnucash....

I have tried every variation on the package name with the apt-get install--gnucash, gnucash- common, gnucash-common_1.8.....etc and the resullt is the same. I have  edited  /etc/apt/sources.list, commenting out the universe/multiuniverse. I have tried to use synaptic--have gone into the software preferences and added Universe and Multiuniverse. The result has been that synaptic doen't recognize gnucash.  

I downloaded a source tarball of gnucash-1.8.9 and enter ./configure--it runs until i need a dependency, which i download, install and ./configure again until i find i'm missing another file. 

I'm a novice at this, but not a complete novice, I've used Slackware, Redhat and Mandrake. I liked Slackware the best, but i have been advised it is too difficult to install gnucash on Slackware, so i swithced to Ubuntu. What i need is gnucash on this old laptop to keep track of some part time business i have. I have no plans of connecting this old computer to the internet, so any software put on it comes from cd or thumbdrive. I have usually been able to install what i want on Slackware--i've wasted an afternoon trying to make this work, so far Ubuntu is less user friendly than Slack. Any advice would be appreciated.

thanks[/QUOTE]

You may want to look at this web site for an apt-get sources list that includes GNUCash. It's: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic). What you'll need to do is ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```
Then copy your generated list from source-o-matic to your apt-get sources.list (replace it completely), save and close. Then run ```
sudo apt-get clean
sudo apt-get update
``` Then GNUCash should be part of your synaptic with the dependencies there. Hope this helps...

Glen

---

### Post by Qrk on 2006-04-01
It can be difficult to install sofware without an internet connection.

Here is the site that has gnu cash and all of it's dependencies ready to download:

[http://packages.ubuntu.com/breezy/gnome/gnucash](http://packages.ubuntu.com/breezy/gnome/gnucash)

You should download the ones you don't have (check in synaptic with the "installed" filter for a list of everything you currently have. Download the ones that you don't have, and burn them to a cd or usb drive.

On your laptop, place all of the files you need on your desktop, and paste these two commands into the terminal.

```
cd ~/Desktop
sudo dpkg -i *.deb
```

Sadly, it seems like gnucash has a ton of dependencies.

---

### Post by gpeck157 on 2006-04-02
[QUOTE=Qrk]It can be difficult to install sofware without an internet connection.

Here is the site that has gnu cash and all of it's dependencies ready to download:

[http://packages.ubuntu.com/breezy/gnome/gnucash](http://packages.ubuntu.com/breezy/gnome/gnucash)

You should download the ones you don't have (check in synaptic with the "installed" filter for a list of everything you currently have. Download the ones that you don't have, and burn them to a cd or usb drive.

On your laptop, place all of the files you need on your desktop, and paste these two commands into the terminal.

```
cd ~/Desktop
sudo dpkg -i *.deb
```

Sadly, it seems like gnucash has a ton of dependencies.[/QUOTE]

Excellent resource...thanks!

Glen

---

