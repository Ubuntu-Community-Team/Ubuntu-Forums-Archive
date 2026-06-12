---
title: "Error when downloading software"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-02-23
Hi, I'm having an error message come up when downloading software;

E: vmware-server: subprocess post-installation script returned error exit status 1

As far as I'm aware the software is downloaded satisfactorily - similarly, installed - but I think this error has something to do with the virtual machine I run.  Indeed, VMware is the virtual machine I use, but not as a server! If indeed it is to do with using VMware on a single laptop, what does the error mean, and can I eradicate it somehow?  Thanks in anticipation of your help.

---

### Post by bwhite82 on 2008-02-23
Give the following command a try:

> sudo apt-get -f install

---

### Post by Berean on 2008-02-24
Thanks for your response.  Sorry mine's been delayed: ill son.  I've done as you've suggested and got the following;

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libarts1c2a libartsc0 libsword6 language-pack-kde-en
  liblualib50 language-pack-kde-en-base libavahi-qt3-1 libdbus-qt-1-1c2
  gtkhtml3.8 liblua50 libclucene0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-server (1.0.4-1gutsy2) ...
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-server, action "start" failed.
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm not running VMware at the moment, although it remains installed.  Any ideas?  Your help is appreciated, thanks.

---

