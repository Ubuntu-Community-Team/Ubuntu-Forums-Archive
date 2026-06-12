---
title: "Ubuntu Preseed disk partitioning questiosn."
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Icefx3k on 2008-02-12
I am currently working with Ubuntu 7.10 and after going through a number of documents:

[http://www.debian.org/releases/etch/example-preseed.txt](http://www.debian.org/releases/etch/example-preseed.txt)
[http://wiki.debian.org/DebianInstaller/Preseed](http://wiki.debian.org/DebianInstaller/Preseed)
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/preseed-contents.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/preseed-contents.html)

I'm still a bit at a loss for what I want to do. I know how to do it with kickstart but I Can't seem to get it to work with preseed. Below is an chunk of the kickstart that works for my redhat installs. 
How would I go about formatting this in a way that preseed /partman-auto will understand? 
Where can I find the partmant-auto documentation? (Could not locate this on my system or ubuntu cd: "The recipe format is documented in the file devel/partman-auto-recipe.txt") 

#part /boot --fstype ext3 --size=100
#part pv.3 --size=100 --grow
#volgroup VolGroup00 --noformat --pesize=32768 pv.3
#logvol /usr --fstype ext3 --name=LogVol02 --vgname=VolGroup00 --size=8064
#logvol swap --fstype swap --name=LogVol00 --vgname=VolGroup00 --size=2048
#logvol /var --fstype ext3 --name=LogVol03 --vgname=VolGroup00 --size=8064
#logvol /home --fstype ext3 --name=LogVol04 --vgname=VolGroup00 --size=8064
#logvol / --fstype ext3 --name=LogVol01 --vgname=VolGroup00 --size=2048

-D

---

### Post by PCFascist on 2008-02-13
I'm not quite sure if I understand, but why don't you try the commands from lvm2?

[http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)

---

