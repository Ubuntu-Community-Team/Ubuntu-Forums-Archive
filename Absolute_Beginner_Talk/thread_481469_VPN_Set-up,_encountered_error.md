---
title: "VPN Set-up, encountered error"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-06-22
Hey there I'm new to linux and i'm learning it fairly fast and have grasped quite a few concepts so far and a co-worker who's knows alot about linux told me that a good project to learn from would be to set up a VPN.  I found a very straight forward guide [here]("http://builder.com.com/5100-6372_14-6038003.html") but i knew it was too good to be true.  I have encountered a problem at the first step.  i have all the files downloaded to a folder called VPN i switched to that directory and did 
> rpm --install dkms-1.12-2.noarch.rpm
and this is the output i got:
> 
alain@S15:~/Desktop/VPN$ rpm --install dkms-1.12-2.noarch.rpm
warning: dkms-1.12-2.noarch.rpm: Header V3 DSA signature: NOKEY, key ID b56a8bac
error: Failed dependencies:
        /bin/bash is needed by dkms-1.12-2.noarch
        /bin/sh is needed by dkms-1.12-2.noarch
        bash > 1.99 is needed by dkms-1.12-2.noarch
        cpio is needed by dkms-1.12-2.noarch
        findutils is needed by dkms-1.12-2.noarch
        gawk is needed by dkms-1.12-2.noarch
        grep is needed by dkms-1.12-2.noarch
        gzip is needed by dkms-1.12-2.noarch
        mktemp is needed by dkms-1.12-2.noarch
        sed is needed by dkms-1.12-2.noarch
        tar is needed by dkms-1.12-2.noarch
alain@S15:~/Desktop/VPN$ 


Just wondering what i should do now??  Any thoughts

Thanks, Alain

---

### Post by Skrynesaver on 2007-06-22
rpm is the Redhat Package Management software suite, it doesn't automaticcally resolve dependencies, (Redhat is an alternative distribution). 
What uou need is the debian package from here
[http://linux.dell.com/dkms/debian/dkms_2.0.16.1-1_all.deb](http://linux.dell.com/dkms/debian/dkms_2.0.16.1-1_all.deb)
Couldn't find it in the ubuntu repositries but clicking on the downloaded package should launch installation of it and it's dependencies

---

### Post by S15_88 on 2007-06-22
followed the link and installed it rebooted but still same error!

---

### Post by S15_88 on 2007-06-22
when installing an RPM is that the only way to do it? or can i make, make install it?

---

### Post by Skrynesaver on 2007-06-22
An RPM is a binary package, you can do a conversion using the alien package to produce a deb.

Perhaps taking the Ubuntu route would be a better way to go, particularly as you are stuck at the first step ;)
[https://help.ubuntu.com/community/VPNServer](https://help.ubuntu.com/community/VPNServer)

---

### Post by cwmoser on 2007-06-22
If you are wanting to VPN to a Windows XP PC or Server 2003 PC, you can use the Network Applet typically located to the left of the date/time at the top of the screen.

Two issues I found with this:

1- You might have to install the network applet -- see Synaptic
2- You will have to have a dynamic ip address -- I could not get it to work when my PC was set to static IP.

Carl

---

### Post by S15_88 on 2007-06-22
hey i got  openVPN installed but i'm wondering if you would be able to explain the walkthrough in a little more detail for example the part about generating a shared static key?? 
i got this output when i typed:cd /etc/openvpn/ && /usr/sbin/openvpn --genkey --secret static.key
> 
alain@S15:~$ cd /etc/openvpn/ && /usr/sbin/openvpn --genkey --secret static.key
Fri Jun 22 16:25:55 2007 Cannot open shared secret file 'static.key' for write: Permission denied (errno=13)
Fri Jun 22 16:25:55 2007 Exiting



so then i threw sudo infront and got this:
> 
alain@S15:/etc/openvpn$ sudo cd /etc/openvpn/ && /usr/sbin/openvpn --genkey --secret static.key
Password:
sudo: cd: command not found

and after that it jus jumped directories to:
alain@S15:/etc/openvpn$ 

so jus for fun i typed : --genkey --secret static.key and got this:
Usage: command-not-found [options] <command-name>

and i know in programming the // is to make a comment or /* */ for multiple lines but is that how u comment things out in linux?   Again i am quite new to linux but i have a good background in computing and i can pick things up fast.  But i could use a little bit more in depth walkthrough adn if possible to explain why one would do a certain step as i am primarily using linux as a learning platform to expand my computer knowledge and so far i am very pleased with everything i have learnt in such a small amount of time.  So if anyone could take the time to explain that walkthrough i would greatly appreciate it!

Thanks, Alain

---

### Post by Skrynesaver on 2007-06-22
OK, lets go through it, last post tonight though, it's late here.
> **S15_88 said:**
> hey i got  openVPN installed but i'm wondering if you would be able to explain the walkthrough in a little more detail for example the part about generating a shared static key?? 
i got thi s output when i typed:cd /etc/openvpn/ && /usr/sbin/openvpn --genkey --secret static.key

This is because you haven't write permissions for the file as an ordinary user (your default login)
> 
so then i threw sudo infront and got this:

and after that it jus jumped directories to:
alain@S15:/etc/openvpn$ 
The && can be read as AND in effect it means only do/test the second thing if the first returns true.  In this case it means cd, change to directory /etc/openvpn, hence the directory jump ;)
The second part of the command generates the key, this requires root permissions, as they are two different commands they both need to be authorized.
> 
so jus for fun i typed : --genkey --secret static.key and got this:
Usage: command-not-found [options] <command-name>
This is bash (the shell) telling you ther should be a command in front of the options
> 
and i know in programming the // is to make a comment or /* */ for multiple lines but is that how u comment things out in linux?   
in the shell you can comment things out using a #, this is only comes into play when writing scripts though.
> 
Again i am quite new to linux but i have a good background in computing and i can pick things up fast.  But i could use a little bit more in depth walkthrough adn if possible to explain why one would do a certain step as i am primarily using linux as a learning platform to expand my computer knowledge and so far i am very pleased with everything i have learnt in such a small amount of time.  So if anyone could take the time to explain that walkthrough i would greatly appreciate it!

Thanks, AlainNo worries Alain, for a more complete guide to the command line try this [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

