---
title: "Mounting the OS X installation in VMware Fusion Beta"
date: 2007-05-14
forum: Apple Intel Users
---

### Post by galvatron1983 on 2007-05-14
Ive got Kubuntu installed on my MacBook and its working really great, with the VMware tools installed I can drag and drop files between os x and kubuntu instantly and dynamically resize screen resolution to suit full screen or windowed mode. Wireless works flawlessly, and I basically have all the functionality I wouldnt have have if I partitioned the HD and did it the normal way. 

But Id like to be able to mount the OS X installation in Kubuntu. At the moment if I want to watch a movie in Kubuntu I have to drag and drop the file into the kubuntu window which is pretty impractical for frequent use. Does anybody know how you can do this?

---

### Post by dmitrijledkov on 2007-05-15
One option would be to activate file sharing on mac and access it via "local network" between emulation and real mac.

But then again you will have to share the whole mac partion which is to really save =(

---

### Post by galvatron1983 on 2007-05-16
Ive just enabled file sharing for the Kubuntu virtual machine, but I dont know how to access the shared folder in Kubuntu. The shared folder is at /Users/myaccount. Do I need to use a terminal command to access it?

---

### Post by arijarot on 2007-05-29
How much of your ram have you allocated to you vm, galvatron? the default?

---

### Post by thully on 2007-05-29
From my past use of VMware Fusion it seems like shared folders are located in /mnt/hgfs or /media/hgfs (or something similar) on Ubuntu.

---

### Post by galvatron1983 on 2007-05-30
> **arijarot said:**
> How much of your ram have you allocated to you vm, galvatron? the default?

I have 512MB allocated to the VM, it runs perfectly, I just need to locate the shared folder where I can access my OS X files within the VM.

---

### Post by ivesjd on 2007-05-31
I wish I could remember how to do it. I know its in the vmware options somewhere, and it tells you where the file is.... sorry i cant help more

---

### Post by galvatron1983 on 2007-06-02
Yes its in /mnt/hgfs. I just pasted that location into the Konqueror file browser and there was my OS X shared folder. I created the shared folder by specifying it in the VMWare shared folder settings. 

All of the folder items were locked initially but I just changed the permissions in the OS X Finder, allowing everybody access and now it works perfectly.

---

### Post by kzm. on 2007-06-02
excuse my stupid question.. do you have kubuntu running virtual in osx or osx in (k)ubuntu?
i ask because i saw some video of last one and was wondering if you know some how-to sites for this.

thanx

---

### Post by arijarot on 2007-06-08
since I have a core duo, do I have to select 2 processors in the vm's preferences or does one include the duo? I currently have one selected...do I need two to get the full power?

---

