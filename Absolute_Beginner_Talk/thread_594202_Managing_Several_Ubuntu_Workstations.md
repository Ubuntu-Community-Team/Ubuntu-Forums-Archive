---
title: "Managing Several Ubuntu Workstations"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by rtoobtoo on 2007-10-27
Hi!
We have 10 workstations in our office which will be migrated to Ubuntu next week ( Oct.29,2007).  

What i want to do is "pimp" or tweak one workstation and then copy the same settings to the other 9 workstations without doing the same thing over again manually. How can i achieve this

Here are some settings that i wished i could automatically copy over to the workstations:

**Configuring Evolution Preferences**

    Maybe i can assign a dummy email first and then specify the POP and SMTP servers 

**Add drivers for MP3, flash etc **

    In my experience, once i tried to play an .mp3 file, the codec is not available so i have to download it first, The same goes with flash.

**Add shortcut icons to desktop **

      Add common icons to desktop like Internet, Mail, OpenOffice etc.

** Add Programs **

      Auto install Skype (thats the only additional program i can think of as of now :) )

** Local Cache of Ubuntu Updates**
     Maybe i can try this.. 
     [Manage Workstation]("http://ubuntuforums.org/showthread.php?t=76950")
    
So there it is.. maybe a script will accomplish this things..

Thank you so much!

---

### Post by julian67 on 2007-10-27
Here's one way to manage multiple installs [http://www.howtoforge.com/ubuntu_pxe_install_server]("http://www.howtoforge.com/ubuntu_pxe_install_server")

and here's the link to official Ubuntu docs on the subject [https://help.ubuntu.com/7.04/installation-guide/hppa/automatic-install.html]("https://help.ubuntu.com/7.04/installation-guide/hppa/automatic-install.html")

---

### Post by rtoobtoo on 2007-10-30
The topics covered on the links you posted are somewhat advanced for a noob like me. Anyway, i noticed that all ubuntu package updates are downloaded from the internet. Is there some way to store this update files in a DVD so that when i do the installations on the other workstations, i will just use this DVD which is a collection of updates? 

thanks

---

### Post by julian67 on 2007-10-31
[APTonCD]("http://aptoncd.sourceforge.net/")

> What is APTonCD?

APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you've downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers.
APTonCD will also allow you to automatically create media with all of your .deb packages located in one especific repository, so that you can install them into your computers without the need for an internet conection.
With APTonCD you be able to...

Backup
    Backup all downloaded packages (via apt-get, aptitude and synaptic) to restore later.
Transport
    Take with you all your favorite packages, in a removable repository where you can install then all on anytime, anytime.
Download
    Get an entire repository, or a specifc section. Simply point-and-click, and in few time you'll have an CD(s) or DVD(s) with entire main, restricted, universe, multiverse, contrib, etc.
Share
    Share your packages with your friends without Internet conection. Also, send a meta-package for him to install the same set of packages that you have.



---

### Post by rtoobtoo on 2007-10-31
wow thanks! im sure going to try this out.. !

---

