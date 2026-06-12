---
title: "Unable to install driver for Samsung CLP-510."
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by learningubuntu on 2006-03-15
Hi,

I had just installed Ubuntu 5.10 and was trying to install the driver for our network printer Samsung CLP-510. 

I was trying to install through the CD provided by Samsung and there was this error message

```
/home/choonhow/.setup11013: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

Tried finding the file using Synaptic Package Manager but to no avail. 

Greatly appreciate if anyone can advise me on how to overcome this problem.

Thank you.


Choonhow

---

### Post by aysiu on 2006-03-15
Download [this driver from the Samsung website](http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=UK&CttFileID=264040&CDCttType=DR&ModelType=N&ModelName=CLP-510&VPath=DR/200503/20050322102424156_lpp-1.1.4-19-i386.tar.gz) to your desktop.

Then go to (Ubuntu) Applications > Accessories > Terminal or (Kubuntu) KMenu > System > Konsole

A DOS-like window will appear with something like ```
choonhow@ubuntu:~$
```

At that prompt, type ```
cd Desktop
tar -xvvzf 2005*.tar.gz
cd image
sudo ./autorun
```

---

### Post by learningubuntu on 2006-03-16
Hi aysiu,

Thank you for your help.

I followed your link and your mentioned procedure, but I still encounter the similar error message on the terminal.

```
/home/choonhow/.setup13605: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

Is there something wrong with my version of Ubuntu version 5.10?

I had read a few topics on Samsung printers but it seems no one has encountered this problem.

Please help.

Thank you.


Choonhow

---

### Post by aysiu on 2006-03-16
You could try: ```
sudo apt-get update
sudo apt-get install libgtk1.2 libgtk1.2-common libgtk1.2-dbg libgtk1.2-dev
``` and then repeating the procedure.

---

### Post by learningubuntu on 2006-03-16
Hi aysiu,

Thank you for your help.

I tried the method you recommended and there was another error:

```
choonhow@ubuntu:~$ sudo apt-get update
Password:
Reading package lists... Done
choonhow@ubuntu:~$ sudo apt-get install libgtk1.2 libgtk1.2-common libgtk1.2-dbg libgtk1.2-de v
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk1.2

```

and after that i tried repeating the installation process and the same error message appeared.

```
/home/choonhow/.setup28366: error while loading shared libraries: libgtk-1.2.so.0: cannot ope n shared object file: No such file or directory
```

appreciate for all the help i had received here. please advise what other ways can i use to overcome this problem.

thank you.


Choonhow

---

### Post by aysiu on 2006-03-16
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by learningubuntu on 2006-03-17
Hi aysiu,

The result is as follows:

```
choonhow@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://sg.archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://sg.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced## after the final release of the distribution.
# deb http://sg.archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://sg.archive.ubuntu.com/ubuntu breezy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://sg.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://sg.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://sg.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://sg.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

thank you for your help in advance.


choonhow

---

### Post by aysiu on 2006-03-17
You have almost no sources enabled.

The # sign basically tells Ubuntu "Ignore the rest of this line."

To get an up-to-date sources.list, go here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by learningubuntu on 2006-03-19
Hi aysiu, 

Thank you for your advice.

I tried to get new updates using the information provided on the website you recommended. But I found out new error messages:

```
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com breezy-backports Release: Unknown error executing gpgv
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

I tried the ways provided on the website but just couldn't overcome the problems listed. 

After running the update, I went back to try to use sudo ./autorun command and the same error message appeared:

```
/home/choonhow/.setup7921: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

Appreciate if you can help me on this, grateful for all the help you have provided,

Cheers.

---

### Post by learningubuntu on 2006-03-27
Hi,

Anyone who is trying to setup network printing for the CLP-510, you might want to try visitng the link below:

[http://ubuntuforums.org/showthread.php?t=92747&highlight=samsung+printer](http://ubuntuforums.org/showthread.php?t=92747&highlight=samsung+printer)

the guys there came out with a solution which solved my problem on the network printing. 

Also, i would like to thank aysiu for his help.


cheers.

---

