---
title: "How do I install stuff?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by soundsystem00 on 2007-03-08
How to I install new programs?

---

### Post by aidanr on 2007-03-08
[installing software]("https://help.ubuntu.com/community/InstallingSoftware")

---

### Post by MikeEnIke on 2007-03-08
The easiest way, for me at least, is to go to Applications->Accesories->Terminal and simply type > sudo apt-get install firefox
or
sudo apt-get install amarok
Another way to do so, is to use Synaptic Package Manager (that name may be off, unfortunately i'm on my windows laptop at the moment). This is located in System->Administration->Synaptic ...

Synaptic is supposed to be more newbie friendly, however I find it to be far to bulky and time consuming to use/

---

### Post by aysiu on 2007-03-08
Brief overview (terminal-based):
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Detailed instructions (point-and-click):
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by chroniker on 2007-03-08
> **aysiu said:**
> 
Detailed instructions (point-and-click):
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
I'm trying to install Firefox 2.0.0.2, which I have downloaded, and following the instructions found in the above link I get the following - 

user-ubuntu:~/firefox$ ./configure
bash: ./configure: No such file or directory
user-ubuntu:~/firefox$ sudo make install
Password:
sudo: make: command not found
user-ubuntu:~/firefox$ sudo checkinstall
sudo: checkinstall: command not found
user-ubuntu:~/firefox$ run-mozilla.sh
bash: run-mozilla.sh: command not found
user-ubuntu:~/firefox$ firefox-bin
bash: firefox-bin: command not found

The run-mozilla.sh and firefox-bin files are present in the directory created when I extracted firefox-2.0.0.2.tar.gz.

This is my first attempt at installing a downloaded program and obviously I'm missing something.

Edit - I'm running 6.06 LTS

---

### Post by AtrejuT on 2007-03-08
I'm pretty sure (though I'm not on Dapper) that firefox should be in the repositories. You can then just install using synaptic as suggested above.
Otherwise you might have to install a package called build-essential first, also using synaptic or apt-get etc.

good luck

atreju

---

### Post by chroniker on 2007-03-08
ver 1.5.0.10 is.

---

### Post by undertakingyou on 2007-03-08
Another quick way is to go APPLICATIONS => ADD/REMOVE PROGRAMS

All the suggestions are good though. :KS

---

### Post by chewearn on 2007-03-08
Firefox 1.5 is in Dapper repositories, but not version 2.0.

Here is the guide to install ver 2.0 in Breezy/Dapper:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by chroniker on 2007-03-08
> **AstalaVista said:**
> Firefox 1.5 is in Dapper repositories, but not version 2.0.

Here is the guide to install ver 2.0 in Breezy/Dapper:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

I think I'll just stay with my current version of Firefox. Should I want or need to install a program not found in the Unbutu repositories, am I going to have to go through similar steps as found in this link?

---

### Post by chewearn on 2007-03-08
I'm not aware of any plan from ubuntu dev but, Firefox 1.5 support/updates from Mozilla will stop pretty soon, so version 2.0 will probably be added into Dapper repo sooner of later.

As for the link, the steps are pretty specific to Firefox.  How to install other apps will depends on many things (my limited knowledge tells me there is no one general method).  You will have to search for the specific steps, or ask this forum for help.:)

---

### Post by aysiu on 2007-03-08
This script automates the installation of Firefox 2.0:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Motoxrdude on 2007-03-08
> **chroniker said:**
> I'm trying to install Firefox 2.0.0.2, which I have downloaded, and following the instructions found in the above link I get the following - 

user-ubuntu:~/firefox$ ./configure
bash: ./configure: No such file or directory
user-ubuntu:~/firefox$ sudo make install
Password:
sudo: make: command not found
user-ubuntu:~/firefox$ sudo checkinstall
sudo: checkinstall: command not found
user-ubuntu:~/firefox$ run-mozilla.sh
bash: run-mozilla.sh: command not found
user-ubuntu:~/firefox$ firefox-bin
bash: firefox-bin: command not found

The run-mozilla.sh and firefox-bin files are present in the directory created when I extracted firefox-2.0.0.2.tar.gz.

This is my first attempt at installing a downloaded program and obviously I'm missing something.

Edit - I'm running 6.06 LTS

You downloaded the tar.gz right?
Extract it somewhere and go into the terminal.
Use the "cd" command to navigate to it. For example
```
cd /home/USERNAME/Desktop/firefox
```
Remember, the terminal is cap sensitive.

Then go ahead and do what it says in the tutorial.

---

### Post by chroniker on 2007-03-08
I went to a web page that required me to install the java plugin. Downloaded and installed with no problem. However creating the symbolic link is a different story. When I checked the permission of "/usr/lib/mozilla-firefox" I'm told I can't change permissions because I'm not the owner so I use "su" and enter my password to which I get - 

su: Authentication failure
Sorry.

Since I only set one pw during the installation I'm a little confused. If I'm not the owner, who is?

---

### Post by Motoxrdude on 2007-03-09
> **chroniker said:**
> I went to a web page that required me to install the java plugin. Downloaded and installed with no problem. However creating the symbolic link is a different story. When I checked the permission of "/usr/lib/mozilla-firefox" I'm told I can't change permissions because I'm not the owner so I use "su" and enter my password to which I get - 

su: Authentication failure
Sorry.

Since I only set one pw during the installation I'm a little confused. If I'm not the owner, who is?

Try```
sudo su
```
and enter the password in.

You can also just use ```
sudo
``` before any command to give you root access. 

Example:
```
sudo apt-get install firefox
```

---

### Post by chewearn on 2007-03-09
> **chroniker said:**
> I went to a web page that required me to install the java plugin. Downloaded and installed with no problem. However creating the symbolic link is a different story. When I checked the permission of "/usr/lib/mozilla-firefox" I'm told I can't change permissions because I'm not the owner so I use "su" and enter my password to which I get - 


I was bumbling around a while back trying to install java, found a few different howtos, but the one that worked for me is this:
Use synaptic, search for "sun-java".  Depending on which repositories you have enabled, you show see either sun-java5 or sun-java6.  Select the one with "-jre" postfix; this will automatically select "-bin" as well.  Also select "-plugin".  Install them, and you should have java when you restart Firefox.

---

