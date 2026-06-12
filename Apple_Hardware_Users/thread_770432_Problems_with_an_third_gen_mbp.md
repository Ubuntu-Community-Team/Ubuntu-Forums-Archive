---
title: "Problems with an third gen mbp"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by mSii on 2008-04-27
I installed Ubuntu on my third generation macbook pro and have been having serious video issues with it since the install.  The driver for the GeForce 8600M GT card in the computer refuses to install. I've tried downloading it from NVIDIA's website(doesn't work, the file won't run despite numerous different attempts from the terminal), Envy crashes, and I'm not sure what else to do.  Does anyone have any suggestions?

---

### Post by sunbird on 2008-04-27
Which flavor of Ubuntu? Have you followed the [install guide]("https://help.ubuntu.com/community/MacBookPro")? Also should look at the [Macbook 3,1 wiki]("https://wiki.ubuntu.com/MacBookPro/SantaRosa") which has some more info on the video card. I have 7.10 x64 running fine on my MBP 3,1 with the same video card.

Envy worked for me. What specific error are you getting on crash?

---

### Post by mSii on 2008-04-27
I'm using 8.04 and GNOME.  I checked out the install guide, and the 3.1 wiki but had no luck with the suggestions in either.  The problem has existed since 7, so I don't think it's an 8.04 issue.  When I run Envy I get

E: Couldn't find package nvidia-new-kernel-source
Traceback (most recent call last):
  File "pulse.py", line 77, in <module>
    choice(sys.argv[1], sys.argv[2])
  File "pulse.py", line 29, in choice
    objects.maninstall3('nvidia', 'latest')
  File "/usr/lib/python2.5/site-packages/Envy/objects.py", line 156, in maninstall3
    task.nvidiaInstall()
  File "/usr/lib/python2.5/site-packages/Envy/classes.py", line 1076, in nvidiaInstall
    check.checkntry(packages)
  File "/usr/lib/python2.5/site-packages/Envy/classes.py", line 306, in checkntry
    raise Exception(error)
Exception: ('\nEnvyNG ERROR: The following packages cannot be installed:',)
root@michael-laptop:/usr/share/envy# 

in the terminal window it pops up.  When I tried to install the driver from NVIDIA it worked fine under X, but I had to exit X to install it, and then it wouldn't run.

---

### Post by sunbird on 2008-04-27
Looks like this is Hardy-related. There's a [bug report]("https://bugs.launchpad.net/envy/+bug/216303") of your exact issue. It looks like the solution reported in the bug report works.

---

### Post by mSii on 2008-04-27
I tried the fix suggested on that page and still no luck, here's the full output of the crash.

python pulse.py nvidia 
root@michael-laptop:/usr/share/envy# python pulse.py nvidia 
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
EnvyNG - Version 1.1.1
Ubuntu Hardy 32bit
Your graphic card has been detected as a GeForce 8600M GT
Your graphic card is supported by the latest driver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
EnvyNG: Updating the packages list
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Reading package lists... Done
EnvyNG: Ubuntu stock kernel detected (2.6.24-16-generic)

OK: All the packages are installed

OK: All the packages are installed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
EnvyNG: The following packages are not installed:
nvidia-new-kernel-source
nvidia-glx-new
nvidia-glx-new-dev

EnvyNG: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-new-kernel-source
Traceback (most recent call last):
  File "pulse.py", line 75, in <module>
    autoChoice(sys.argv[1])
  File "pulse.py", line 15, in autoChoice
    objects.nvidiainstallg(data1)
  File "/usr/lib/python2.5/site-packages/Envy/objects.py", line 84, in nvidiainstallg
    task.nvidiaInstall()
  File "/usr/lib/python2.5/site-packages/Envy/classes.py", line 1076, in nvidiaInstall
    check.checkntry(packages)
  File "/usr/lib/python2.5/site-packages/Envy/classes.py", line 306, in checkntry
    raise Exception(error)
Exception: ('\nEnvyNG ERROR: The following packages cannot be installed:',)

---

