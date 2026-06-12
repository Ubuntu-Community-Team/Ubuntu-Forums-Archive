---
title: "Apache problem"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by gn0m3 on 2005-11-21
I dont speak very well english i hope you will understand me ! :( 

I want to install Apache so i wrote (in terminal) 
**sudo apt-get install apache2**

But it said that i must install first 
[B]apache2-mpm-worker 
apache2-mpm-prefork 
apache2-mpm-perchild[/B]

I installed apache2-mpm-worker  but when i try to install other two (apache2-mpm-prefork / apache2-mpm-perchild)
It says : 
[B]The following packages have unmet dependencies: 
 apache2-mpm-perchild: Depends: apache2-common (= 2.0.53-5ubuntu5.3) but 2.0.54-5ubuntu2 is to be installed[/b]
I made **apt-get updat&#1077;** and try to install apache2-common but it says 
[B]apache2-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded[/B].
I saw in Synaptic apache2-common is  2.0.54-5ubuntu2
What i need to do ?? :(

---

### Post by matthewv on 2005-11-21
You should be able to do a ```
sudo apt-get install apache2
``` to download and install apache as well as all the dependancies. Make sure you right install in the command, (you don't have that written above) or you will get action not found errors. You might also need to have the extra repositories enable, but I don't think they are necessary.

---

### Post by gn0m3 on 2005-11-21
Srry i have typed apt-get install just forgot to write it now srry again 
I fixed it in the first post

---

### Post by gn0m3 on 2005-11-21
Here is all
> angelus@ubuntu:~$ sudo apt-get install apache2
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  apache2: Depends: apache2-mpm-worker (= 2.0.53-5ubuntu5.3) but it is not going to be installed or
                    apache2-mpm-prefork (= 2.0.53-5ubuntu5.3) but it is not going to be installed or
                    apache2-mpm-perchild (= 2.0.53-5ubuntu5.3) but it is not going to be installed
E: Broken packages
angelus@ubuntu:~$  sudo apt-get install  apache2-mpm-prefork
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  apache2-mpm-prefork: Depends: apache2-common (= 2.0.53-5ubuntu5.3) but 2.0.54-5ubuntu2 is to be installed
E: Broken packages
angelus@ubuntu:~$  sudo apt-get install  apache2-common
Reading package lists... Done
Building dependency tree... Done
apache2-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
angelus@ubuntu:~$


---

