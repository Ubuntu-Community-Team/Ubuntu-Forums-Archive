---
title: "Installing Java - JRE 5"
date: 2007-11-27
forum: Apple PPC Users
---

### Post by tgs1952 on 2007-11-27
Hello,

Need to install Sun JRE 5 in order to run software, oxygenxml, and use my Ubuntu install to update my online college course (requires jre 1.5).

I would also like Eclipse, which is installed, to use it.

Tried to do so via synaptic but ran into a dependency problem - found sun-java5-jre but dependency sun-java5-bin not available.

Any help would be greatly appreciated - I am new to Ubuntu.

---

### Post by Auria on 2007-11-27
Hi,

Sun does not release Java for PPC Linux. You can however install IBM Java or GCJ (I think both can use eclipse, but the IBM one is generally better i think) you can find more information on the PPC FAQ (it's a sticky)

---

### Post by tgs1952 on 2007-11-27
Thanks for the reply.

I followed the directions given for medibuntu and ran into problems:

Adding that repository breaks my synaptic completely:

Here is the output from the terminal:

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -o /etc/apt/sources.list.d/medibuntu.list
~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -o- | sudo apt-key add - && sudo apt-get update
gpg: no valid OpenPGP data found.
tom@tom-feisty:~$ sudo apt-get install ibm-j2rel.5
E: Type '--10:39:35--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

When I tried this before got the same problem and had to delete via the command line just to use synaptic again.

---

### Post by tgs1952 on 2007-11-27
I have managed to install ibm-j2re1.5_1.5.--Omedibuntu1_powerpc.deb manually.

However, I have no clue as to how to set it up from there. java -v in the terminal still shows 1.4.2

Thanks in advance for any help.

---

### Post by Auria on 2007-11-27
this probably means you still have GCJ. If you don't care about GCJ, you can just disable it. 

If you want to keep GCJ check [https://help.ubuntu.com/community/Java#head-81c3789bc76872336f69a7af90d1759ef38eeb64](https://help.ubuntu.com/community/Java#head-81c3789bc76872336f69a7af90d1759ef38eeb64)

It will be something like
sudo update-alternatives --config java

and there may be a bit more to it

---

### Post by tgs1952 on 2007-11-27
Thanks,

I have since managed to get the ibm.1.50 and install it, following the instructions at the link you posted.

When I run java -version I do see jre 1.5.

However, when I run the installer for the program I want to install, it can't find the new install.

Not sure where exactly it installed.

---

### Post by Auria on 2007-11-27
To help we would need to know which project, and also you can most probably find infromation about where it installs in the project's docs

---

### Post by tgs1952 on 2007-11-28
Thanks again, but a little searching around revealed that the software I wanted to install, the oxygen xml editor, not only requires jre 1.5 or higher, but the Sun jre 1.5 or higher.

Now, I am in the market for a good xml editor that will run on linux ppc - so far, it doesn't look good.

In any event, ibm jre 1.5 is working and Eclipse runs a good deal faster.

Now I need to figure out how to get Firefox to use the new plugin - the instructions at the ubuntu java page definitely do not work for my installation.

---

### Post by BLTicklemonster on 2008-01-23
I can't run frostwire because of this:

bill@bill-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
bill@bill-desktop:~$ 


go to the site, and read the installation instructions, they make no sense to me.

Help?

---

