---
title: "VMware Tools in Ubuntu 6.10 Edgy"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-08
I am using:
Ubuntu 6.10
VMware Workstation with VMwareTools-5.5.2-29772.tar.gz

I am using this site as reference:
[http://www.thoughtpolice.co.uk/vmware/howto/ubuntu-server-6.10-edgy-eft-vmware-tools-install.html](http://www.thoughtpolice.co.uk/vmware/howto/ubuntu-server-6.10-edgy-eft-vmware-tools-install.html)

have extracted the files as directed by the page i am following but:
shoaibi@saber-rider:~/Desktop$ /tmp/vmware-tools-distrib/vmware-install.pl
Please re-run this program as the super user.

Execution aborted.

shoaibi@saber-rider:~/Desktop$ 

gives the provided error, i am member of Administartor, and my Main Group is root, what should i do? should i try it in root account? or something else can be done?


EDIT:

i tried sudo but due to keyboard problem the enter kept pressed and here is the problem now:

shoaibi@saber-rider:~/Desktop$ sudo /tmp/vmware-tools-distrib/vmware-install.pl
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

Unable to copy the source file ./installer/services.sh to the destination file 
/etc/init.d/vmware-tools.

Execution aborted.

shoaibi@saber-rider:~/Desktop$ sudo /tmp/vmware-tools-distrib/vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

shoaibi@saber-rider:~/Desktop$ sudo /tmp/vmware-tools-distrib/vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

shoaibi@saber-rider:~/Desktop$ sudo /tmp/vmware-tools-distrib/vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

shoaibi@saber-rider:~/Desktop$ /tmp/vmware-tools-distrib/vmware-install.pl
Please re-run this program as the super user.

Execution aborted.

shoaibi@saber-rider:~/Desktop$ sudo /tmp/vmware-tools-distrib/vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

shoaibi@saber-rider:~/Desktop$ sudo /tmp/vmware-tools-distrib/vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

shoaibi@saber-rider:~/Desktop$ 


also tell me the directories to give in when it asks

---

### Post by glenm on 2007-02-08
Hi
I'm new to Linus as well.  I'm using Kubuntu 6.10 (Edgy) and I had a similar problem to your "previous installation of VMware software has been detected" when I tried to install VMWare Server.  What happens is that the install script creates a directory to put the binaries in and when the install fails the directory is not removed.  The next time you try the install the scripts checks for the directory and when it finds the directory it assumes that there is an existing installation.

I can't tell you the name of the directory ( it may be different for you ) but I found it by reading the install script.  Open it in Kate and search for the error message and then try to work out what  directory its looking for.  When you have found out what the name of the directory is then rename that directory and try the install again.  The directory in my case was "/etc/vmware/locations"

Sorry but I can't help you with the other part of your problem.:(

---

### Post by shoaibi on 2007-02-10
Anybody else with some ideas over this?

---

### Post by mcduck on 2007-02-10
I'm not sure,but I think you might need kernel headers & build-essential to install wmware tools.

---

### Post by shoaibi on 2007-02-10
i have done both things....

---

### Post by luckylucky on 2007-02-10
These two lines are very important.  Copy & paste them into shell:
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`


This stuff might help...

******************** 

sudo apt-get remove vmware-player-kernel-modules
(it might uninstall all the dependencies)

sudo dpkg --purge vmware-player
(It might yell about a non empty dir that it can suppress )

sudo rm -rf <path to the dir>
(you may verify that there is only vmware concerned about that dir )

apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
wget
[http://download3.vmware.com/software...1-19317.tar.gz](http://download3.vmware.com/software...1-19317.tar.gz)
tar xzvf VMware-player-1.0.1-19317.tar.gz
cd vmware-player-distrib
sudo ./vmware-install.pl

---

### Post by shoaibi on 2007-02-10
what <path to the dir>?

---

### Post by shoaibi on 2007-02-11
Problem still UnResolved!

---

### Post by Jussi01 on 2007-02-11
> **shoaibi said:**
> what <path to the dir>?

I think he is talking about any vmware directory that you have. BTW, if you just need simple virtualization, not necessarily vmware, you could try [www.virtualbox.org](www.virtualbox.org) - it is simpler to install than vmware (a .deb) and simpler to make a virual machine, and IMHO runs faster. so maybe worth a look for you.

---

### Post by shoaibi on 2007-02-11
@LUCKYLUCKY
i rna your commands but the file wasn't found, i got another .tar.gz file and extratec that, here is the thinsg afetr that:

```

shoaibi@saber-rider:~/Desktop$ cd vmware-tools-distrib
shoaibi@saber-rider:~/Desktop/vmware-tools-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

shoaibi@saber-rider:~/Desktop/vmware-tools-distrib$ 


```

---

### Post by RudolfMDLT on 2007-02-11
Try reconfiguring VMware?

sudo /usr/bin/vmware-config.pl

It's just a shot in the dark really...

---

### Post by Pollywoggy on 2007-02-11
I set up my machine so that I can su to root.  I used kuser to do that.  You don't have to do it, but that is what I do.

To fix that error you are getting,

cd ~/vmware-distrib/bin

in the bin directory, you will find vmware-uninstall.pl

Execute that file:  ./vmware-uninstall.pl


Now you should be able to install VMware in the usual manner.

---

### Post by Pollywoggy on 2007-02-11
BTW you will need to install the kernel headers for the running kernel before you can install VMware.

uname -a    will give you the name you need.

For example, uname -a  shows on my system:

Linux slider 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux

so I did
sudo apt-get install linux-headers-2.6.17-10-386

I also installed the linux-source of the same version but I don't know if that is necessary.
It can't hurt.

then I did

cd /usr/src
ln -s linux-source-2.6.17 linux
cd linux
cp /boot/config-2.6.17-10-386 .config
make prepare-all

Then I installed VMware.
Just be sure that you get the proper headers for the kernel you are running, or VMware will not install correctly.

---

### Post by praxis22 on 2007-02-12
If it still gives you the error at that point do the following (on Edgy at least)

sudo rm -R /etc/vmware

This will then allow you to install vmware server.

worked for me :)

---

### Post by nuclearj on 2008-07-19
> **praxis22 said:**
> If it still gives you the error at that point do the following (on Edgy at least)

sudo rm -R /etc/vmware

This will then allow you to install vmware server.

worked for me :)

Thanks!  Worked like a charm.  I am installing the latest server edition as of 08-19-07 on Gutsy

---

