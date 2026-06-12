---
title: "Remove applications + terminal"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-04-28
Hi all....

Perhaps a simple question for the more experienced, I am attempting to remove a Brother scanner driver.

I find the driver in synaptic, however when selecting to remove, the removal process spits out the following error:

> E: brscan2: subprocess post-removal script returned error exit status 1

can this be removed some other way perhaps?

Thanks!

---

### Post by zvacet on 2007-04-28
```
sudo apt-get remove --purge file_name
```

---

### Post by TURNER on 2007-04-28
thanks for the feedback; I encountered the same problem, heres the output:

```
turner@turner-desktop:~$ sudo apt-get remove --purge brscan2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sun-java6-plugin liboggflac3 gstreamer0.10-plugins-ugly-multiverse
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  brscan2
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 90308 files and directories currently installed.)
Removing brscan2 ...
rmdir: /usr/local/Brother/sane/GrayCmData/ALL: No such file or directory
rmdir: /usr/local/Brother/sane/GrayCmData/AL: No such file or directory
rmdir: /usr/local/Brother/sane/GrayCmData: No such file or directory
rmdir: /usr/local/Brother/sane: No such file or directory
dpkg: error processing brscan2 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan2
E: Sub-process /usr/bin/dpkg returned an error code (1)
turner@turner-desktop:~$ 
```

---

### Post by Sef on 2007-04-28
How did you install the driver through synaptic, dpkg, terminal, or other?

---

### Post by TURNER on 2007-04-28
Hi Sef, I installed via a shell script provided in the link below

[http://ubuntuforums.org/showthread.php?p=2277190#post2277190](http://ubuntuforums.org/showthread.php?p=2277190#post2277190)

---

### Post by TURNER on 2007-04-29
The plot thickens!

I tried to install updates this morning, and receive the error:


> It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

running: ```
sudo apt-get install -f
``` in the terminal provides the following:

```
turner@turner-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sun-java6-plugin liboggflac3 gstreamer0.10-plugins-ugly-multiverse
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  brscan2
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 90308 files and directories currently installed.)
Removing brscan2 ...
rmdir: /usr/local/Brother/sane/GrayCmData/ALL: No such file or directory
rmdir: /usr/local/Brother/sane/GrayCmData/AL: No such file or directory
rmdir: /usr/local/Brother/sane/GrayCmData: No such file or directory
rmdir: /usr/local/Brother/sane: No such file or directory
dpkg: error processing brscan2 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan2
E: Sub-process /usr/bin/dpkg returned an error code (1)
turner@turner-desktop:~$ 
```

I am also unable to update or install via synaptic, whilst attempting I receive an error:

> E: brscan2: subprocess post-removal script returned error exit status 1

seems that this brother driver is taking over my pc...:o #-o 

any help would be appreciated.

---

### Post by TURNER on 2007-04-29
Ok I've been playing a little and have established that the dpkg is locked by another process, this process is the  brscan2 which I was attempting to remove.

Synaptic will NOT allow me to uncheck the brscan2 item from inside synaptic....

running ```
apt-get install -f
```

results in ```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied
```)

and attempting

```
sudo rm /var/lib/dpkg/lock
```

does not provide an error, however after running this command and subsequently running

```
sudo apt-get install -f
```

iam again informed
```

rmdir: /usr/local/Brother/sane/GrayCmData/ALL: No such file or directory
rmdir: /usr/local/Brother/sane/GrayCmData/AL: No such file or directory
rmdir: /usr/local/Brother/sane/GrayCmData: No such file or directory
rmdir: /usr/local/Brother/sane: No such file or directory
dpkg: error processing brscan2 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan2
E: Sub-process /usr/bin/dpkg returned an error code (1)
turner@turner-desktop:~$ 
```

any ideas?

---

### Post by rawpigeon on 2007-04-29
Hi,

I've been having the same problem! I found this though:

[http://www.linuxquestions.org/questions/showthread.php?t=517308]("http://www.linuxquestions.org/questions/showthread.php?t=517308")

and it solved the problem! I created folders:

/usr/local/Brother/sane
/usr/local/Brother/sane/GrayCmData
/usr/local/Brother/sane/GrayCmData/ALL
/usr/local/Brother/sane/GrayCmData/AL

and for good measure I created a couple of files in /usr/local/Brother/sane/GrayCmData/ALL and /usr/local/Brother/sane/GrayCmData/AL.

Then I did:  sudo apt-get remove --purge brscan2

and it uninstalled! Now I've just got to remove the files I added.

Hope this helps.

---

### Post by TURNER on 2007-04-29
rawpigeon thanks a million, that did the job!!

---

