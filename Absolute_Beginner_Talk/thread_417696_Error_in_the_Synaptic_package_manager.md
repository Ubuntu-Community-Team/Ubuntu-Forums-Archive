---
title: "Error in the Synaptic package manager"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by chaits on 2007-04-21
Hi,

I installed ubuntu 7.04 yesterday in my laptop (i'm complete newbiee to linux)

I'm getting an error while trying to install a software(in fact any software) using synaptic package manager.

The error is as follows:

An error occured 
The following details are provided:

E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

I'm inserting the screnshots of the error windows.

Some one plzz help me out

---

### Post by leibowitz on 2007-04-21
You have three broken packages. You need to fix or delete them and you won't see the errors messages anymore.

Please try like this. Go to System menu > Administration > Synaptic Package Manager.

Click on the bottom left button of the screen called "Filters". Now click on the "Broken" line that appears on the left. Remove every package you see there by going on each one and click with the right mouse button. Select "Delete" (or delete totally, that will work aswell).

Now click on the "Apply" button in the toolbar. And continue the process. 

Wait till it's finished and click on the "Reload" toolbar button.


Please report any issue you have during the procedure.

---

### Post by chaits on 2007-04-22
Thank You Leibowitz  for the quick reply.. but it dint work:(

There is no button called Filters ..there is Custom Filter though(May be 'coz it's 7.04)...and when clicked on broken no packages are shown :((

What do I do now??

I have one more question...if at all I find them is it OK to delete the the broken packages...is there any way to fix them ..'coz i'm afraid they may affect other packages

Thanks

---

### Post by leibowitz on 2007-04-22
It should be no problem to delete them, but just to be sure it's preferable you paste their name here when you find those broken package.

Anyway, to fix that, go to the Applications Menu, Accessories > Terminal. And type those commands in it.
```
sudo apt-get -f install
sudo apt-get check
```

Please paste here the output you get.

---

### Post by chaits on 2007-04-22
**This is the output i got after running the command "sudo apt-get -f install"**

chaits@ChaitsPraviSahi:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)
chaits@ChaitsPraviSahi:~$ 
[B]
and this is the output of "sudo apt-get check"
[/B]
chaits@ChaitsPraviSahi:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
chaits@ChaitsPraviSahi:~$ 

I think even the problem is not fixed now :(

---

### Post by leibowitz on 2007-04-22
> Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information

You seems to have three package cross-dependant related to LVM cluster thing.. I don't know what it is, but do you installed this manually, or just have configured your linux installation to use LVM.

You can delete them with no prob as they are not configured nor used anyway.

> Errors were encountered while processing:
clvm
redhat-cluster-suite
system-config-cluster

Try copying this in a terminal:
```
sudo apt-get remove clvm redhat-cluster-suite system-config-cluster
```

Edit: and paste the output here.

---

### Post by chaits on 2007-04-23
I havn't installed any thing manually

**This is the output:** for the command "sudo apt-get remove clvm redhat-cluster-suite system-config-cluster"

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  clvm redhat-cluster-suite system-config-cluster
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1651kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 105247 files and directories currently installed.)
Removing system-config-cluster ...
Removing redhat-cluster-suite ...
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--remove):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Cypher on 2007-04-23
It looks like APT is almost done removing the prorgams, but is choking because the packages are broken, so take **leibowitz ** command a bit further and add the "--force" to hopefully clean up..

```
sudo apt-get remove [COLOR="Red"]--force[/COLOR] clvm redhat-cluster-suite system-config-cluster
```

Regards

---

### Post by chaits on 2007-04-23
This is the output after using
 $sudo apt-get remove --force-yes clvm 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  clvm
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 492kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 106841 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--remove):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

I dont know if this is creating problems or not but,i'm not able to execute a simple c program using openGL...when I check in the synaptic package manager it shows that g++ is installed but i'm not able to execute the programs

---

### Post by leibowitz on 2007-04-23
The openGL thing is another story. Please paste your error message in here, because I don't know what you mean by "not able to execute". Anyway, that will be resolved later.

First thing is to find a way to delete your clvm broken package. It will be hard. Because it needs to start a script to remove it, and this script is what's broken.

Please execute the following command to see if dpkg suggest anything first.

```
dpkg -C
```

Anyway, did you install the desktop or the server version of Ubuntu. Because clvm and redhat cluster thing should definitely _not_ be in the desktop version. So I don't get what if you did something wrong or just installed the server version. Can you explain why you have such package installed and broken.

---

### Post by chaits on 2007-04-23
I'm pretty sure that I installed desktop version.

after installing ubuntu 7.04 ...  i started installing the packages using synaptic package manager ...in the list of packages marked, by mistake i marked clvm also without knowing its usage :(

and this is the output after using the command [code]dpkg -C[code]

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 clvm                 Cluster LVM Daemon for lvm2

---

### Post by leibowitz on 2007-04-23
That's ok. Please join the **/var/log/syslog** file and **/etc/init.d/clvm**

Alternatively you can try to execute **sudo /etc/init.d/clvm** to see what you get as an error message. 
If you see an output with "restart/reload/start/stop" etc. then try to execute it with start, then with stop. Or the other way round.

```
sudo /etc/init.d/clvm start
sudo /etc/init.d/clvm stop
```

And paste everything in here.

We are going to try to fix this clvm script to be able to delete the clvm package. 

Note: that's not an easy task.

---

### Post by chaits on 2007-04-23
I don't know how to join those files.. i tried the alternative way u suggested

The output:

 $sudo /etc/init.d/clvm start
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information

$ sudo /etc/init.d/clvm stop
Stopping Cluster LVM Daemon

---

### Post by leibowitz on 2007-04-24
Please backup your clvm file.

```
sudo cp /etc/init.d/clvm /etc/init.d/clvm_backup
```

Then download the attached file and go to the directory where it is.

```

tar -xvzf clvm.tar.gz
sudo cp clvm_new /etc/init.d/clvm
```

And try to remove the broken package again.

```
sudo apt-get remove clvm
```

---

### Post by su_cooldude on 2007-04-26
i dunno where this guy went without thanking u man!
but thank u!!
been fighting with this darn thing since quite sometime

---

### Post by chaits on 2007-04-28
I'm extremely sorry Leibowitz, inspite of you working so hard to fix my bug i couldn't respond immediately..i got struck with some other work...and din't find to try what you u have suggested.

I'll try now and let you know the status...

Thanks a LOTTTTTT
Chaits

---

### Post by chaits on 2007-04-28
Thank You very much Leibowitz...thanks a lot

i downloaded the clvm tar file u sent and did as u said....now my synaptic package manager works fine and even my add/remove programs..i dont get clvm error any more

Being a newbie I dint follow every thing you said..but understand something at least....I thank especially for your patience in resolving the bug i'm getting

---

### Post by muito_fofinho on 2007-10-11
Hi, i'm with just the same problem, but i couldn't understand what to do when you say:

*Then download the attached file and go to the directory where it is.*

and where or how to execute the following:
[B]
tar -xvzf clvm.tar.gz
sudo cp clvm_new /etc/init.d/clvm[/B]

Thank You!

---

### Post by muito_fofinho on 2007-10-11
Sorry, i just found the solution to my problem.

This is what i've done:

sudo rm /etc/init.d/clvm
and then
sudo apt-get remove clvm

thank you anyway :)

---

### Post by forestpixie on 2007-10-11
the instructions are in post 14, the file is also attached to that post.

the commands need to be executed in terminal, which is in accessories

---

### Post by liwei2000 on 2007-10-20
Thank you so much! I followed the thread as I encountered the exactly same problem.
and found you have done wonderful works to fix this problem. thank you!

> **leibowitz said:**
> Please backup your clvm file.

```
sudo cp /etc/init.d/clvm /etc/init.d/clvm_backup
```

Then download the attached file and go to the directory where it is.

```

tar -xvzf clvm.tar.gz
sudo cp clvm_new /etc/init.d/clvm
```

And try to remove the broken package again.

```
sudo apt-get remove clvm
```

---

