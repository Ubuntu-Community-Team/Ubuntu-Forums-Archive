---
title: "PPTP Client Installation"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Pushhands on 2007-01-21
Hey All,

I am new to Ubuntu.  I am fairly new to Linux.  I have a lot of networking and Microsoft OS experience though.  Over a decade of heavy consulting experience.  I want to try and use ubuntu for the challenge and to add it to my consulting experience.  I remember the days when there was Novell Netware and there were 2 choices for your network OS for your company.  That was much better when there was a choice.  I would like to introduce ubuntu to my clients and be able to support it.  Vista is just way too expensive.  I need to get up to speed myself in order to do this though.

I just installed ubuntu and now I need to get the OS usable for my day-to-day tasks.  My first challenge is that I need to establish a VPN connection to my office.  How can I do this.  I have a Microsoft RRAS server on Windows 2003.  I use the built in Windows PPTP client.  Does ubuntu have a PPTP client that is compatible?  Is there one out there I can use?  What can I do?  I am a complete newbie to Linux for the most part, so telling me of a program and its website, will not help!  :)  How do I install it (in detail)?  Where do I get it?  Any help you all can provide would be greatly appreciated!  I have heard great reports about this community.  I would love to learn ubuntu and help give back.  Please help!  Thanks!

Pushhands

---

### Post by %hMa@?b&lt;C on 2007-01-21
crowell@opteron:~$ aptitude search PPTP
p   network-manager-pptp                                                     - network management framework (PPTP plugin)
p   pptp-linux                                                               - Point-to-Point Tunneling Protocol (PPTP) Client
p   pptpd                                                                    - PoPToP Point to Point Tunneling Server

any of those fit your needs?

---

### Post by Pushhands on 2007-01-21
Hey jeffc313,

Thanks so much for your reply!  I am not sure what you are saying though.  :)  Remember, I am a complete newby.  I think you were telling me to go to a Terminal and type "aptitude search PPTP".  Does that sound right?  I went and did that and got this reply...

gharris@Taoist-Ubuntu:~$ aptitude search PPTP
p   pptp-linux                      - Point-to-Point Tunneling Protocol (PPTP) C
p   pptpd                              - PoPToP Point to Point Tunneling Server    
gharris@Taoist-Ubuntu:~$ 

What does this tell me though?  I think it tells me the aptitude of my system?  Meaning whether I have PPTP software installed?  From what I see, I have a PPTP server and client installed.  Is that right?  How do I use it?  Please tell me there is a graphical interface to the software.  If not, How do I establish the connection and setup the software?  Will I have to manualy edit routing tables in order to access the remote network?  Please help!  I need detailed instructions though.  Or someplace to get them.  Thanks again for your reply!

Pushhands

---

### Post by dedmin on 2007-01-21
sudo apt-get install  pptp-linux network-manager-pptp network-manager-gnome
sudo nano /etc/network/interfaces
Before:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
After:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

```
Restart and in the tray is the answer.

---

### Post by Pushhands on 2007-01-21
Hey dedmin,

I followed your instructions but then got the following and don't know what it means or where to turn.  To be truthfull, your instructions were kind of unclear to me as I don't have much Linux experience.  How in the world did you ever learn this!  I am impressed.  Anyway, this is what I got...  Can you help!?

gharris@Taoist-Ubuntu:~$ sudo apt-get install pptp-linux network-manager-pptp network-manager-gnome
Password:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package network-manager-pptp
gharris@Taoist-Ubuntu:~$ 

What does this mean?  What should I do next?  Will the next instructions go smoothly?  Somehow I doubt it!  :)  That is why I have always been frustrated with Linux.  Please help!

Pushhands

---

### Post by dedmin on 2007-01-22
This means that you don't have the right repositories to find this files.You do from console:
> sudo nano /etc/apt/sources.list
and remove '#' in front of the lines with URL, like this:
> Before:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
After
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
Then do 
> sudo apt-get update
and follow my previous guide.

---

### Post by Pushhands on 2007-01-22
Hey Dedmin,

Thanks for your help here.  I am sorry to be dense but what you said didn't work.  Here is what I did.  I got into the "sources.list" file and did not see the following line to remove the comment on...

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

I saw two lines a little similar that I removed the comment from.  It went like this...

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

Just so you can see my source.list file, here it is below in its entirety...


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


So I then did the Sudo update command and it seemed to run fine.  So I went ahead with your next commands and got the same error as before.  So I must have removed the comment from the wrong line?  Which one should I use?  Here is what I got below...

gharris@Taoist-Ubuntu:~$ sudo apt-get install pptp-linux network-manager-pptp network-manager-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package network-manager-pptp
gharris@Taoist-Ubuntu:~$ 

Please help!  Sorry to be dense.  This Linux **** just doesn't make sense and I always seem to get **** like this happening.  I really want to make the switch but have no idea how to get beyond crazy stuff like this!?  Thanks!

Pushhands

---

### Post by dedmin on 2007-01-23
Take my sources.list and replace it. Try again.
> # 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

# Seveas Packages - imbrandon mirror
 deb [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas all
 deb-src [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas all

 # Seveas Packages - ubuntulinux mirror
 deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
 deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all

# Canonical Commercial Repository (Opera,Real Player10.. etc)

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

# Skype for linux

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

# Amarok
deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main

# Swiftfox
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

# WineHQ
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main



---

### Post by Pushhands on 2007-01-25
Hey Dedmin,

Man there are so many posts on this board, it is so active, this thread almost disappears!  Anyway, it looks like it worked!  Thanks so much for your help.  I feel I can really start to learn Linux now!  I see the VPN up in the tray.  I created my VPN connection and tried to connect but get the following error:  

VPN Connect Failure
Could not start the VPN Connection: "Connection Name".  Due to a connection error.
VPN Connection Failed

I can connect fine from a Windows PC so I know my account and the PPTP server are setup fine.  Any Idea what may be wrong?  Thanks so much for your help!

Pushhands.

---

### Post by munan on 2007-01-26
> **dedmin said:**
> sudo apt-get install  pptp-linux network-manager-pptp network-manager-gnome
sudo nano /etc/network/interfaces
Before:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
After:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

```
Restart and in the tray is the answer.

Perfect. You saved me days of work. Thank you!

---

### Post by Pushhands on 2007-01-26
Hey All,

I appear to have it all working.  The instructions were great Dedmin!  Thanks so much for your patient help!  I am still not getting totally connected though.  When I launch the VPN connection and put in my username and password I get the following error:

VPN Connect Failure
Could not start the VPN connection  '[connection name]' due to a connection error
VPN Connection Failed

I cannot get farther than that.  I have tried other PPTP servers that I have setup and confirmed working at other clients that I have.  These are Windows 2000-2003 RRAS PPTP servers.  Usually allowed in through a firewall to the server.  They use PPTP Exclusively.  The clients work fine from a Windows PC.  They connect with no problem and very fast.  From the Linux PC, it tries to connect slowly and then I get the following error.  

The only thing different in the instructions that I ran into is as follows.  When I run the following command...

sudo nano /etc/network/interfaces

I did not get the same exact one in the sample.  I have the one as follows and I edited it as you see below.  Could the problem be here or would it be some place else.  Please help!  Thanks.

Pushhands...


auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

