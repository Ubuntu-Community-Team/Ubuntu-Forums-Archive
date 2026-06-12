---
title: "great opportunity to meet a new NooB"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by googlebytes on 2007-04-21
So I loaded up some programs from the repository, and got back the following errors:

E: clamav-base: subprocess post-installation script returned error exit status 1
E: clamav-freshclam: dependency problems - leaving unconfigured
E: clamav: dependency problems - leaving unconfigured
E: clamav-getfiles: dependency problems - leaving unconfigured


About that opportunity....

Thanks Brent

---

### Post by jiminycricket on 2007-04-21
Does sudo apt-get -f install do anything?


Also try: sudo apt-get check

Maybe clamav wants to use bash, as well.  If nothing else works and no one else responds, do
sudo mv /bin/sh /bin/sh.old
sudo ln -s /bin/bash /bin/sh

---

### Post by heimo on 2007-04-21
Open a terminal and run:
```
sudo mv /var/lib/dpkg/info/clamav.* /var/lib/dpkg/info/clamav-* /tmp
sudo aptitude --purge remove clamav clamav-base clamav-getfiles clamav-freshclam
sudo aptitude install clamav clamav-base clamav-getfiles clamav-freshclam

```

---

### Post by googlebytes on 2007-04-21
Thanks heimo - you really seem to know your stuff.
Ran it - clamav seemed to uninstall and re-install. But I don't know if it made it all the way. I hadn't closed my old error window, and I had another underneath. I tried to find a prompt somewhere on the system indicating clamav was ready to go, but couldn't find any. Found the prompt for  Firestarter under System> Administration.

thanks for all in advance who are trying to help. Try running it (heimo's code) again, and see what happens?

---

### Post by singedwings on 2007-04-21
You need **clamtk** installed as well to provide you with a gui. You can then access it in **Applications - Accessories**

---

### Post by googlebytes on 2007-04-22
When I tried again here is what I got:

owner@owner-desktop:~$ sudo mv /var/lib/dpkg/info/clamav.* /var/lib/dpkg/info/clamav-* /tmp
mv: cannot stat `/var/lib/dpkg/info/clamav.*': No such file or directory
mv: cannot stat `/var/lib/dpkg/info/clamav-*': No such file or directory
owner@owner-desktop:~$ sudo aptitude --purge remove clamav clamav-base clamav-getfiles clamav-freshclam
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
owner@owner-desktop:~$ sudo aptitude install clamav clamav-base clamav-getfiles clamav-freshclam
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
owner@owner-desktop:~$

---

### Post by heimo on 2007-04-22
> **googlebytes said:**
> 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Close any other package manager that is running (Synaptic / Add Remove programs). If those are not running and you still get this message, check System->Administration->System Monitor that those are really not running and end/kill processes if necessary. Retry. If you still get the message, reboot and retry.

---

### Post by mac.ryan on 2007-04-22
Googlebytes, I had your initial problem (dependencies, not file lock) yesterday night (I am running on Feisty64bit). Today I re-tried the installation (I wanted to google up for the error message) but...

...**magic!** the error was not anymore there! :confused:

The only significant operation I did between yesterday night and this morning have been:[LIST]
[*]removing the restricted manager (sadly enough... it is more of an hassle than of an help, in my configuration)
[*]I installed a number of 32 bit libs basically (ia32*) because I needed them for Skype.[/LIST]I am not sure this is what "fixed" the problem, yet if anything else fails you might wish to give it a try... (?)

---

### Post by googlebytes on 2007-04-22
thanks alot again!

so I rebboted and ran the three commands in a terminal window and here were the results:
owner@owner-desktop:~$ sudo mv /var/lib/dpkg/info/clamav.* /var/lib/dpkg/info/clamav-* /tmp
Password:
mv: cannot stat `/var/lib/dpkg/info/clamav.*': No such file or directory
mv: cannot stat `/var/lib/dpkg/info/clamav-*': No such file or directory
owner@owner-desktop:~$ sudo aptitude --purge remove clamav clamav-base clamav-getfiles clamav-freshclam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  unzoo{p} 
The following packages have been kept back:
  tzdata 
The following packages will be REMOVED:
  clamav clamav-base clamav-freshclam clamav-getfiles 
0 packages upgraded, 0 newly installed, 5 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 7045kB will be freed.
Do you want to continue? [Y/n/?] y

Size changes will be shown.

The following packages are unused and will be REMOVED:
  unzoo{p} <-77.8kB> 
The following packages have been kept back:
  tzdata 
The following packages will be REMOVED:
  clamav <-213kB> clamav-base <-401kB> clamav-freshclam <-6197kB> clamav-getfiles <-156kB> 
0 packages upgraded, 0 newly installed, 5 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 7045kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 
dpkg: serious warning: files list file for package `clamav-dbg' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `clamav' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `clamav-getfiles' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `clamav-testfiles' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `clamav-docs' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `clamav-freshclam' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `clamav-base' missing, assuming package has no files currently installed.
107669 files and directories currently installed.)
Removing clamav-getfiles ...
Removing clamav ...
Removing clamav-freshclam ...
Removing clamav-base ...
(Reading database ... 
dpkg: serious warning: files list file for package `clamav-dbg' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `clamav-testfiles' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `clamav-docs' missing, assuming package has no files currently installed.
107669 files and directories currently installed.)
Removing unzoo ...
owner@owner-desktop:~$ sudo aptitude install clamav clamav-base clamav-getfiles clamav-freshclam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  unzoo 
The following packages have been kept back:
  tzdata 
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam clamav-getfiles unzoo 
0 packages upgraded, 5 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/6200kB of archives. After unpacking 7045kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package clamav-base.
(Reading database ... 
[B]dpkg: serious warning: files list file for package `clamav-dbg' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `clamav-testfiles' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `clamav-docs' missing, assuming package has no files currently installed.[/B]
107664 files and directories currently installed.)
Unpacking clamav-base (from .../clamav-base_0.88.4-1ubuntu2.1_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.88.4-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.88.4-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package clamav-getfiles.
Unpacking clamav-getfiles (from .../clamav-getfiles_0.6-1_all.deb) ...
Selecting previously deselected package unzoo.
Unpacking unzoo (from .../archives/unzoo_4.4-4_i386.deb) ...
Setting up clamav-base (0.88.4-1ubuntu2.1) ...

Setting up clamav-freshclam (0.88.4-1ubuntu2.1) ...
 * Starting ClamAV virus database updater freshclam                                                                                                   [ ok ] 

Setting up clamav (0.88.4-1ubuntu2.1) ...
Setting up clamav-getfiles (0.6-1) ...
EICAR Anti-Virus Test File downloaded and installed.

Setting up unzoo (4.4-4) ...
owner@owner-desktop:~$ 

so it seemed to work this time but now this NooB can't find a prompt to run clamav. System monitor doesn't show any clamav process running. Don't see anything under >Applications.
Also do I need any of the highlighted files, esp clamav dbg?

Thanks again - seems at least we are making progress.

---

### Post by googlebytes on 2007-04-22
Also, I had Edgy Eft 6.10 inittially, so one of the first things I did was to update. Downloaded about 122 files I think. Was Informed that the updates were for Edgy Nautilus, but when I open Firefox, I am still greeted with Welcome to Edgy Eft. I assume this means nothing.

---

### Post by heimo on 2007-04-22
You may want to still run:
```
sudo aptitude --purge remove clamav-docs clamav-testfiles clamav-dbg
```

And
```
sudo aptitude install clamtk clamav-testfiles clamav-docs
```

Then you should have a frontend for clamav in Applications->Accessories->Virus Scanner.

---

### Post by googlebytes on 2007-04-22
Thank you so much heimo - I really appreciate it. It all seems so involved - you obviously already know your way around these files.

Now second question - If I wanted to install a second antivirus - Avast - will it cause conflicts? Can I choose one or the other from the accessories line? how would I go about it? Is it not recommended for any reason you know of? I have already downloaded the tar.gz file.

---

### Post by heimo on 2007-04-22
> **googlebytes said:**
> Now second question - If I wanted to install a second antivirus - Avast - will it cause conflicts? Can I choose one or the other from the accessories line? how would I go about it? Is it not recommended for any reason you know of? I have already downloaded the tar.gz file.

I don't use anti-virus software - except on my email server. There's just no need for it unless you interact with Windows users and want to make them a favour (by warning them) in case they send you an Office file with a virus on it. So, I don't know anything about these anti-virus softwares in desktop use.

---

### Post by googlebytes on 2007-04-23
Well thanks once again - my experiences with Windows has made me paranoid of spyware and viruses I guess. This is one of the main reasons I want to use Ubuntu - esp for internet use. 

How is spring coming along in Finland - any flowers yet? I like this time of year. 
It sounds like you are a webmaster or  you administrate websites. i suppose they are all linux machines? I know really nothing of linux, as you have seen, but I do know something of spiritual things.

---

### Post by heimo on 2007-04-23
> **googlebytes said:**
> How is spring coming along in Finland - any flowers yet? I like this time of year. 

Thanks for asking! Currently about 8 degrees in celsius (46 fahrenheit), so it's quite warm. ;) Nature is definitely coming back to life.

> **googlebytes said:**
> It sounds like you are a webmaster or  you administrate websites. i suppose they are all linux machines?

As a hobby, yes. And they're all running Linux based operating systems.

---

### Post by googlebytes on 2007-04-23
Did you have any problems upgrading to Fiesty? I was a little concerned about upgrading from Edgy to Fiesty based upon the posts I read about hardware configuration problems, so i just decided to update my Edgy to "Nautilus." 

Do you use only Ubuntu for desktop? have you ever tried Suse linux? From the sounds of it you use a different linux in server applications. 

Spring here is very nice but has been a little dry. I have been meaning to create a photo gallery of my best Utah pictures for one of my websites, but I haven't done that yet - seems like I just haven't had the time this year for stuff like this. I moved from two different hosts to 1and1, which has a free photo gallery, which I haven't tried yet. If I don't like theirs, I have a linux based script for a photo gallery I am planning to use.  Do you host your websites yourself/ On my old windows machine I wouldn't dream of doing this, but now it may become a consideration if I learn enough linux.

Gotta go to work now -
Brent

---

