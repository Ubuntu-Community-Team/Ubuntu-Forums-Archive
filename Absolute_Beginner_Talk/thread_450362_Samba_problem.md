---
title: "Samba problem"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by dondad on 2007-05-21
Samba was working fine, in that I could access a Windows computer that I have on my home network. I did two things, the latest update that was recommended in the update manager, and installed Crossover office(did this before the update). When the update was completed, it came back and said that Samba was giving an error level 1 and would not start. I did some searching on the forums, uninstalled Samba, then reinstalled it, but get the same error and it will not start. When I try to start it in the terminal, it fails, and also in the install, it comes back with a failure to start. Not sure where to go from here. I don't have access to the Ubuntu box right now, but can post any output that would help when I get home tonight. Thanks for the assistance.

---

### Post by dondad on 2007-05-23
I have been searching the forums and tried everything that I can think of , but no matter what I do, Samba won't start. Every time I install anything, at the end I get a message that Samba has generated an error level 1 and did not start. Can anyone give me someplace to look, or how to troubleshoot it?

I uninstalled it, then reinstalled and got this:
family@main:~$ sudo apt-get autoremove samba smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not installed, so not removed
Package smbfs is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
family@main:~$ sudo apt-get install samba smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  smbldap-tools
The following NEW packages will be installed:
  samba smbfs
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/3431kB of archives.
After unpacking 8516kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 
dpkg: serious warning: files list file for package `crossover-standard' missing, assuming package has no files currently installed.
128422 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.22-1ubuntu4.2_i386.deb) ...
Selecting previously deselected package smbfs.
Unpacking smbfs (from .../smbfs_3.0.22-1ubuntu4.2_i386.deb) ...
Setting up samba (3.0.22-1ubuntu4.2) ...
Generating /etc/default/samba...
 * Starting Samba daemons...                                             [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Setting up smbfs (3.0.22-1ubuntu4.2) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

I got it working, perhaps not in the recommended way, but it did fix it. I tried a lot of things, but it seemed that there was something that was sticking when I uninstalled samba and then reinstalled. I finally found a reference to the status file in dpkg, so I opend it and went through it. There was a reference to a particlly installed version of Samba there, so I backed up the file and deleted that section, then reinstalled Samba. That time, it insatlled without the errors and so far, seems to be working.

I still have to play a bit because I can see and get to my Windows box from the ubuntu one, but, although I can see the shared folder I set up on the main box from Windows, I haven't figured out the permissions or method to be able to access it yet.

Maybe this will be of use to someone.

---

### Post by dondad on 2007-05-25
*bump*

---

