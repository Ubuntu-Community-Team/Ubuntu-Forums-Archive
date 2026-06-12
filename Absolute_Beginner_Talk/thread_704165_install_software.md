---
title: "install software"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by okkie on 2008-02-22
anybody please explain this to me ' 4.) from terminal cd dir to the downloaded file and type “tar zvxf'. i have the vmware .tar.gz file on my desktop but step 4 cd dir doesn't work or i am doing something wrong. thanks

---

### Post by TeoBigusGeekus on 2008-02-22
cd /home/<your user name>/Desktop

---

### Post by sayakb on 2008-02-22
> **okkie said:**
> anybody please explain this to me ' 4.) from terminal cd dir to the downloaded file and type “tar zvxf'. i have the vmware .tar.gz file on my desktop but step 4 cd dir doesn't work or i am doing something wrong. thanks

Suppose the archive vmware.tar.gz is in your Documents
type in the terminal

cd /home/your username/Documents

Then type
tar zvxf vmware.tar.gz (Or alternatively extract it using the GUI. Rightclick on the file and select Extract option)
A folder "vmware" would be created. Then make install there (as depicted in the tutorial you read :) )

---

### Post by macogw on 2008-02-22
they mean cd to whatever directory you put it in when you downloaded it

Does it need to be VMWare?  You could also install VirtualBox if what type of VM doesn't matter.  Virtualbox is in the repos as virtualbox-ose for the open source edition (no USB support) or [http://virtualbox.org](http://virtualbox.org) for the (free of cost) binary one.  If you set it to pre-allocate the hard drive space, it's extremely fast....puts VMWare to shame.

These directions: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) should help

---

### Post by kpkeerthi on 2008-02-22
Are you trying to install VMware?

You can use Synaptic to install vmware-server. See [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server) and scroll to the section titled **Ubuntu 7.10 (Gutsy) From Ubuntu packages**

---

### Post by sayakb on 2008-02-22
> **macogw said:**
> they mean cd to whatever directory you put it in when you downloaded it

Does it need to be VMWare?  You could also install VirtualBox if what type of VM doesn't matter.  Virtualbox is in the repos as virtualbox-ose for the open source edition (no USB support) or [http://virtualbox.org](http://virtualbox.org) for the (free of cost) binary one.  If you set it to pre-allocate the hard drive space, it's extremely fast....puts VMWare to shame.

These directions: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) should help

+1 to VirtualBox
Open a terminal and type:
```
sudo apt-get install virtualbox
```

---

