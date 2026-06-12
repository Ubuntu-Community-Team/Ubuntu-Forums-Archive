---
title: "Can't upgrade from Hoary"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by BlackMamba7 on 2007-08-03
I'm getting really really angry with Ubuntu at the moment because all I want to do is install a program for a Uni course I'm doing....but I've spent hours and hours trying to get it working.....with no luck at all...

Basically, I tried installing it at Uni, but I had to use a proxy there....which didn't even end up working anyway.....so now I'm at a friend's house, using the proxy-free internet.....thinking it'd take just a minute....
WRONG....

Now, I think I'm having troubles with stuff I changed previously for the proxy....I thought I worked it out....but apparently not.

Anyway, I'm trying to use:
sudo apt-get update

which gets
```

Err http://archive.ubuntu.com hoary Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hoary-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Ign http://archive.ubuntu.com hoary Release
Ign http://archive.ubuntu.com hoary-updates Release
Ign http://archive.ubuntu.com hoary/main Sources
Ign http://archive.ubuntu.com hoary/restricted Sources
Ign http://archive.ubuntu.com hoary-updates/main Packages
Ign http://archive.ubuntu.com hoary-updates/restricted Packages
Ign http://archive.ubuntu.com hoary-updates/main Sources
Ign http://archive.ubuntu.com hoary-updates/restricted Sources
Err http://archive.ubuntu.com hoary/main Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hoary/restricted Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hoary-updates/main Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hoary-updates/restricted Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hoary-updates/main Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hoary-updates/restricted Sources
  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

my /etc/apt/sources.list is
```

##deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu hoary universe

#deb http://security.ubuntu.com/ubuntu hoary-security main restricted
#deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

#deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse

```

and I can't upgrade from Hoary because of the problems I'm having with apt-get update and apt-get upgrade.

All I want is to have the ability to add programs easily.....which, as many other beginners on here have said, isn't a feature of ubuntu...or any linux for that fact....

How do I get apt-get working properly again? and how can I upgrade? and how I can get openGL and glut (the Uni stuff I need) working in Ubuntu?

In windows it only took a minute.....yet I've spent all day trying to get it right in Ubuntu.....

Thanks in advance

---

### Post by BlackMamba7 on 2007-08-03
Oh.....and with the proxy settings.....I've made sure its just using a direct connection to the internet when I go to System->Preferences->Network Proxy.....
so this should be working because I can ping websites and it works fine..

---

### Post by Hallvor on 2007-08-03
Why don`t you just install Ubuntu 7.04? I mean, support for Hoary ended in october 2006, and a clean reinstall is usually the best way to upgrade anyway.

---

### Post by synd7 on 2007-08-03
I don't think hoary is supported anymore, the repo's are probably closed
Why not install dapper or feisty?

---

### Post by mikewhatever on 2007-08-03
I think you can't upgrade, because the version that follows Hoary is not supported any longer. The earliest version now supported is 6.06 Dapper Drake. It seems your only option is to reinstall.

---

### Post by Tux Aubrey on 2007-08-03
What you have there, sir, is one dead hedgehog.

Backup your /home and anything else you need and install a more current version - or perhaps move to Windows if the frustration you have chosen to express here is directed at Linux in general.

---

### Post by dougfractal on 2007-08-03
Hoary came out april 2005, when ubuntu was still young.
It would be like judging Windows Xp by looking at Win95.

>  Backup your /home and anything else you need and install a more current version
I would recommend this approach


but if you what a more drawn out method....

**proxy**
check   synaptic>settings>preferences>network

**upgrade**
sudo apt-get dist-upgrade
or

---

### Post by BlackMamba7 on 2007-08-12
Thanks for the responses guys.....and I've taken your advice, but now I have a new problem.
When I install Feisty, I get a flickering screen which I can't see anything.
I got the alternate desktop CD, and installed through text mode....which completed....but now I have the same problem at the login screen....
I can hear Ubuntu's sounds when I'm ready to log in....so I know it got that far....but I can't do anything after that.

I'm guessing my video card isn't automatically supported....however I can get into recovery mode, and use the command line from there.
Is there a way to get my display working properly? Maybe by installing new nVidia drivers?

A problem I might have with that is that during installation, I wasn't connected to the internet, and therefore I didn't configure my network config.....

Please help.......a step by step guide would be much appreciated, as I really spend most of my time in Windows, and have little knowledge of linux in general....
Thanks

---

### Post by Jeremy23 on 2007-08-12
Okay. You might want to try installing the NVIDIA drivers. Go into recovery mode, and log on. Then, type this:

```
sudo apt-get install nvidia-glx
```

That should download the NVIDIA drivers from the internet. Now, do this to enable the drivers:

```
sudo nvidia-glx-config enable
```

Now, that should be all good. Reboot:

```
sudo reboot
```

...and start up Ubuntu like normal. Hopefully it'll work.

---

### Post by dougfractal on 2007-08-12
ethernet
> 
sudo dhclient eth0

---

### Post by BlackMamba7 on 2007-08-13
Awesome, thanks for the quick replies guys....I'm gonna try it later tonight...

Hopefully that's all that I'll need.....it seems like it, with dhclient eth0 enabling the internet.....no proxy settings to worry about...then those lines to download, install and enable the n-vidia drivers....

I just hope that it's not something other than the video drivers.....I really just want this to work.....

I'll let you know how it goes....
Cheers...

---

### Post by BlackMamba7 on 2007-08-13
Awesome, it worked....

Now I just hope I can get everything else working....

Thanks heaps guys.

---

