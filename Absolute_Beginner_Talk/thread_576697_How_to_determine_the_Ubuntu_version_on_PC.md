---
title: "How to determine the Ubuntu version on PC"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by beno4433 on 2007-10-15
I downloaded Ubuntu 6.06 LTS on my Dell Dimension 4550 and am very slowly learning how to use the OS within a dual boot(with XP Home) configuration.

Given that I'm a completely green when it comes to Ubuntu, I have numerous questions to ask.  But I will keep this posting to a minimum.

First, how can I tell which version of Ubuntu I downloaded on my machine.  I downloaded Ubuntu using the live CD from the "Official Ubuntu Book" and have performed a few updates which the system asked for.  The disk says it's Ubuntu 6.06 LTS, but I'd like to know how to find the actual version I'm using.

Secondly, if this is an outdated version, should I upgrade to a more recent version. And if so, how would I do it.

I used the following command to get the kernel version:

uname -r
Ubuntu Kernel 2.6.15-29

Other than finding the kernel version, I have no idea what OS version I'm using or whether I should upgrade to a newer version.

For those that choose to respond, thanks for you patience.  I have several Ubuntu books that I'm reading.  However, I know I have a long way to go before I'll understand the OS and can quit using XP Pro.

---

### Post by Dr Small on 2007-10-15
If you installed 6.06, then the version you are running is 6.06. You should be able to check the version by:
```
cat /etc/issue
```

Or System > About Ubuntu (And it should tell you the version on that page.)
To upgrade to the newest version, you would have to upgrade to Edgy Eft, then to Fiesty Fawn and then finally to Gusty Gibbon.

If you do not have alot of stuff on your system, you might find it easier to download the newest version from the Official Website: [http://ubuntu.com](http://ubuntu.com) and reinstall your operating system.

Dr Small

---

### Post by LowSky on 2007-10-15
in terminal ```
sudo nano /etc/apt/sources.list
```

---

### Post by vishzilla on 2007-10-15
System->Administration->System Monitor is another way to find out

---

### Post by haldean on 2007-10-15
Chances are you're using either Dapper (6.06) if your kernel is v2.6.15; Fiesty (7.04) comes with 2.6.20 and Edgy (6.10) comes with 2.6.17

As Dr Small said, you can check this by running

```
cat /etc/issue
```

---

### Post by FredB on 2007-10-15
> **beno4433 said:**
> [...]

Secondly, if this is an outdated version, should I upgrade to a more recent version. And if so, how would I do it.

6.06 is a long time support version. It will be supported until april 2009. But you can upgrade to feisty fawn (7.04) or gutsy gibbon (7.10) which will be released in 3 days.

> I used the following command to get the kernel version:

uname -r
Ubuntu Kernel 2.6.15-29

Other than finding the kernel version, I have no idea what OS version I'm using or whether I should upgrade to a newer version.

It is dapper drake aka 6.06.1 LTS

> For those that choose to respond, thanks for you patience.  I have several Ubuntu books that I'm reading.  However, I know I have a long way to go before I'll understand the OS and can quit using XP Pro.

Just take your time. But upgrading to feisty - in order to get younger software and better support of your hardware in kernel could be a good idea.

---

### Post by beno4433 on 2007-10-16
Thanks to everyone for your responses.  I'd like to try and upgrade my machine since I only use it for Test purposes. Plus, I think I'm experiencing compatibility issues with this version recognizing my video adaptor.  I'm unable to play any video using the Totem Movie Player.

I will have to do some more research before performing any upgrades since I've never done this before.

Does anyone know of any links that describes how to perform an upgrade from dapper drake to fiesty fawn?

---

### Post by maybeway36 on 2007-10-16
You have to upgrade to edgy, then to feisty. Kinda silly, but I guess that's how it works.

---

### Post by FredB on 2007-10-16
Yes. It will be better to do this... Or even simpler : backup your data, and install Gusty cleanly ;)

---

### Post by twiceasworn on 2007-10-16
Speaking as someone who has upgraded from 6.06LTS to 7.10, I will say, just back the data up and install 7.04 or 7.10 cleanly, if you have that option.  It is much easier.

---

### Post by beno4433 on 2007-10-16
Ok - It seems the best choice is to perform a clean install of the new version that's being released on the 18th.

Since I'm new to Ubuntu, I'm not sure what I should do to perform a clean install.  Plus, I currently have a dual boot configuration with XP Home on a separate partition which I want to keep intacted.

To perform a clean install, do I have to uninstall the current version I have(Dapper Drake), or can I just download the new version from the official Ubuntu website on top of the version I currently have?

I'm sure there's got to be more indepth steps than I just described.  I'm trying to find a posting on performing a clean installation.

I've only had the Dapper Drake version on my machine for about a month and basically have no files that need to be saved.  Plus, I don't even know how to backup the small amount of files I have and then return them to the OS once I've installed the new version.  As you can tell, I have a long way to go in learning how the OS works, but I have the desire to learn.  But for now, I know my questions seem very simplistic.

---

### Post by haldean on 2007-10-16
You can just go ahead and install Gutsy (the new version) over your old system. Just tell the installer to install Ubuntu to the same partition that Dapper is on now.

Just make sure you back up anything important, because everything will be gone after you reinstall.

---

### Post by beno4433 on 2007-10-17
Halean - 

I would like to perform the clean install as you described.  However, I'm having a difficult time finding any posts or how to's on performing clean installations.

Do you or anyone else know of any links that outline the steps to perform a clean installation of Ubuntu, especially installing 7.10.  Having some instructions would really help someone like me who is very new to this or any Linux distro.

I've created several Linux discs, including Knoppix, DSL, and Ubuntu 6.06 LTS.  So, would it be better for me to create my own 7.10 installation disc instead of just downloading 7.10 directly from the website?

Plus, I assume there will be a live CD version that includes the actual 7.10  installation.  Is this a better route to take?

Again - I think it would be of great help if anyone knows of links or posting that answer these questions.

Thanks

---

### Post by Brucevdk on 2007-10-17
> **beno4433 said:**
> I would like to perform the clean install as you described.  However, I'm having a difficult time finding any posts or how to's on performing clean installations.
A clean installation basically means downloading the ISO and then installing the system as usual but overwriting your current installation. The opposite would be a system upgrade where the system in place is upgraded towards the latest version.

Like others have said, you'll need to backup any important files before doing a clean install. The most important would be your home directory (/home), though you'd still lose any modifications made as a system administrator. If you want to keep your Windows partition make sure you choose to manually partition the hard disk, do not format the whole disk.

When doing a clean install it might be handy to place /home on a different partition, that way you can easily share it between distros and won't have to backup when reinstalling.

> **beno4433 said:**
> I've created several Linux discs, including Knoppix, DSL, and Ubuntu 6.06 LTS.  So, would it be better for me to create my own 7.10 installation disc instead of just downloading 7.10 directly from the website?
Download the ISO from the official website and burn it to cd-rom.

> **beno4433 said:**
> Plus, I assume there will be a live CD version that includes the actual 7.10  installation.  Is this a better route to take?
The normal desktop installation ISO from the website is indeed a LiveCD, you'll be fine grabbing the LiveCD if your system meets the requirements.

---

### Post by AtrejuT on 2007-10-17
Hi!

installing ubuntu is really very simple. All you have to do is download the LiveCD, burn it, put it into your drive and boot the computer. (If you have boot from that drive enabled in your BIOS).

Ubuntu Live will come up, and you are free to play around with it. Once you are ready to install just double-click the 'install'-icon on the desktop. A wizard will come up which can guide you through the installation.

More information can be found here:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

good luck!

---

### Post by beno4433 on 2007-10-17
Thanks again for the comments and suggestions.  They will definitely come in handy when I perform the clean installation once the new version comes out on the 18th.

As for backing up important files, I really don't have any other than a few openoffice documents.  But they are not that important.  I've really just been spending time getting a feel for the operating system.  Nevertheless, I make an attempt to back up what little files I have.  The important thing is that I want to still keep my XP Home installation.  So I'll be performing a dual boot installation.

I thought about just wiping the disk and installing only Ubuntu.  Which, I guess, is the easier way to perform the installation.  However, I also have a Dell M70 laptop with XP Pro.  This is my main machine and I want to eventually put Ubuntu on it in a dual boot configuration as well.  But I'm very apprehensive about doing this, since I'm still new to Ubuntu.  Even though I perform regular backups on the Dell M70 using Acronis True Image Home 10, I'm still wary that something will go horribly wrong with the installation and I will not be able to restore my machine to it's original state using the image restore function from Acronis.  Hopefully, one day I'll have the confidence to intall Ubuntu on the Dell M70.  Right now, though, I'm just too inexperienced to have the confidence to  do it.

Thanks again to everyone for you kind suggestions and support.

---

### Post by Duck2006 on 2007-10-17
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by jbierlein on 2008-05-09
cat /etc/lsb-release.....

root@qadb03:/etc# cat lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.2 LTS"

That gives the most information I have seen.

---

### Post by Butthead on 2008-05-09
lsb_release -a (in terminal).

---

