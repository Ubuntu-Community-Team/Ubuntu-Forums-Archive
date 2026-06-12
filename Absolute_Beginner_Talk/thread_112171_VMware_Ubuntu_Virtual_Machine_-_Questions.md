---
title: "VMware Ubuntu Virtual Machine - Questions"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by Gates of Delirium on 2006-01-03
Hi,

I just tried out Ubuntu virtual Machine through VMware player... and 

1) was surprised to have it ask me for passwords at certain points. I was never given a choice to set a password, nor know which is the default. I'm able to get to the desktop and mess with some programs but, I got it trying to get to the Install applications. Can I install applications in a virtual machine?

2) How can I access all my drives and folders that I can with Windows? 

3) I inserted a data disk into my drive and tried to play music... but I couldn't play mp3 files, only wav. Why?


Thanks,

---

### Post by Fatjoint on 2006-01-03
Did you install the VM image from scratch or use an image that was already setup?  If you used an image already setup then that is where your passwords are coming from.

As far as MP3 and such, you need to get the Windows Plugins.  Do a search for Windows Plugins through the forums and you'll see some help on that.

---

### Post by Gates of Delirium on 2006-01-03
Thanks, I took a look in the configuration files and found it.

However, I can't install anything. Can one install anything in a Virtual Machine? I foudn the place to do this and once selecting the apps I want, I'm asked to insert a disk Ubuntu 5.10 _Breezy Badger...
but...but... I don't have a disk. Its a virtual machine.

---

### Post by mesocool on 2006-01-04
[QUOTE=Gates of Delirium]Thanks, I took a look in the configuration files and found it.

However, I can't install anything. Can one install anything in a Virtual Machine? I foudn the place to do this and once selecting the apps I want, I'm asked to insert a disk Ubuntu 5.10 _Breezy Badger...
but...but... I don't have a disk. Its a virtual machine.[/QUOTE]

Have you ever used virtual drive such as Alcohol 120%? If you have ubuntu image file, you can take advantage of virtual drive as one of your cdrom to install ubuntu.. :cool:

---

### Post by aragorn2909 on 2006-01-04
[QUOTE=Gates of Delirium]Thanks, I took a look in the configuration files and found it.

However, I can't install anything. Can one install anything in a Virtual Machine? I foudn the place to do this and once selecting the apps I want, I'm asked to insert a disk Ubuntu 5.10 _Breezy Badger...
but...but... I don't have a disk. Its a virtual machine.[/QUOTE]

Just comment out the line in /etc/apt/sources.list inside the virtual machine that is asking for for the disk.

---

### Post by loftx on 2006-01-04
As far as I can tell when asked for a password use "vmware" (without the quotes). This should let you use synaptic (System->Administration->Synaptic package manager from the menus) and install packages and work anywhere else you're prompted for a password. You can then install support for MP3.

Drives and folders I'm not sure about, these are normally accessed using shared folders in vmware, but these are configured by the guest OS (ubuntu) and I think are hidden in VMware player.

Another way is to set up a webserver on your Host OS (windows) and share the directories on it you want. I think it is possible to mount disks in VMWare (not sure about player) but not recommended as it can trash your data. 

You might want to look into using the ubuntu boot cd - it should let you access everything and let you configure more things than VMware player.

---

### Post by peteyp666 on 2006-01-13
the password for mine was "ubuntu" not "vmware", just in case anyone is having a similar issue with the password

---

### Post by ubuntuuser on 2006-01-13
[QUOTE=Gates of Delirium]Hi,

I just tried out Ubuntu virtual Machine through VMware player... and 

1) was surprised to have it ask me for passwords at certain points. I was never given a choice to set a password, nor know which is the default. I'm able to get to the desktop and mess with some programs but, I got it trying to get to the Install applications. Can I install applications in a virtual machine?

2) How can I access all my drives and folders that I can with Windows? 

3) I inserted a data disk into my drive and tried to play music... but I couldn't play mp3 files, only wav. Why?


Thanks,[/QUOTE]

1) This virtual machine is just that: another computer simulated by your actual PC. Think of it as a second PC right beside your real one. So you can install programs just like on a real PC. When you create a new VM you can specify how large that virtual HDD should be. Open the system monitor to see how much space you have available. The open synaptic and install what you want/need. Keep in mind that ubuntu will be much faster in real life. Your CPU has to simulate a nearly complete PC.

2) Without further preparation you can't share files between those two. I am only using VMware, where I can specify folders I want to make available to that machine. Maybe you want to search the help files on that problem. Look for "Shared folders". Maybe the player allows you to use host-only networking, then you may share files like on a network.

3) Look [here.]("https://wiki.ubuntu.com/RestrictedFormats")

---

