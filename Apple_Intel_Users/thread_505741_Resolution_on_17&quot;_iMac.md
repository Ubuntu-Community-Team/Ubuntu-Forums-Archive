---
title: "Resolution on 17&quot; iMac?"
date: 2007-07-20
forum: Apple Intel Users
---

### Post by tigerplug on 2007-07-20
Just set up ubuntu on my 17" Intel iMac using vmware fusion.

I can't get ubuntu to fill the screen in fullscreen mode. I have tried all the resolutions but having no luck.

Can anyone tell me what I have to do?


By the way, I have also checked the settings of the vm.

---

### Post by cyberdork33 on 2007-07-20
have you installed vmware tools?

---

### Post by tigerplug on 2007-07-21
Hi Cyber Dork. I followed a guide to install them that I found somewhere out there in cyberspace.

I'm not sure if they are installed though.

By any chance could you point me to a guide that will show me how to do so?

---

### Post by Quillz on 2007-07-22
> **tigerplug said:**
> Just set up ubuntu on my 17" Intel iMac using vmware fusion.

I can't get ubuntu to fill the screen in fullscreen mode. I have tried all the resolutions but having no luck.

Can anyone tell me what I have to do?


By the way, I have also checked the settings of the vm.
Both Parallels Desktop (which is what I use) and VMWare Fusion require you to install their set of tools. This will give you optimal screen resolution, as well as greatly improved mouse and overall system performance. I haven't used VMWare Fusion, but if it's anything like Parallels, it will automatically mount a CD containing the necessary drivers on your Ubuntu installation. I generally copy those files to my desktop, open the Terminal and move there, then run the file(s), in Parallels, I simply run ~/Desktop/parallels-tools.sh and it does the rest. You can then log out and/or reboot your virtual machine and it's all set up. (Oddly enough, you don't get any confirmation message that it's been installed, something I think should be added.)

---

### Post by tigerplug on 2007-07-23
Thanks for the reply.

I understand how VMware tools works.
I can mount the CD (which is a disk image provided by VMware on the desktop).

I double click on the CD and then extract the TAR file to the desktop.
However, from here I am lost. I can't seem to get it to do anything that I want it to.

Can anyone step me through the exact process of installing vmware tools from here?
:(

---

### Post by cyberdork33 on 2007-07-23
There are instructions in the File named 'INSTALL'

Basically you just need to open a terminal and navigate to the directory where you extracted the files and execute the installer script:

```
./vware-install.pl
```

---

### Post by tigerplug on 2007-07-23
Thanks for that. I'll be home in under and hour and I'll give it a go.

As far as I remember though, the last time that I tried that I got an error.
When I try it I'll post the result here, if I get an error I'll post that in detail too.

Excuse the ignorance, I appreciate the help!

---

### Post by tigerplug on 2007-07-23
Thats done the trick... no error message. I don't know what I was doing wrong.

Such an improvement!

---

