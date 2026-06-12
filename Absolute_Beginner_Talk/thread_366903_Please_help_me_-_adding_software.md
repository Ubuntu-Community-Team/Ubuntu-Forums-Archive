---
title: "Please help me - adding software"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by the_alch3m1st on 2007-02-21
Hi 

I have ubuntu 6.06 installed on my notebook. I have an IBM t43 model 2668M , When i try to install something with add/remove it says:
-application name- is not available in any software channel

The application might not support your system architecture.

I looked in device manager and all the stuff at my procesor are unknown.My procesor is an intel centrino 750 1.86GHz

Please Help me

---

### Post by Obor on 2007-02-21
What are you trying to install? 
You can go to Synaptic (in System-Administration) and search for the package there. (also have a look in synaptic - settings - repositories that you have all the repos enabled.)

---

### Post by lyceum on 2007-02-21
Are you plugged into the internet?

---

### Post by mahy on 2007-02-21
Try giving some more information and please choose a better title next time. ;)

---

### Post by the_alch3m1st on 2007-02-21
I tryed to intall xmms to play mp3's.
I am conected to the internet i am writing this form ubuntu.

---

### Post by tgalati4 on 2007-02-21
Welcome to the Ubuntu community.  You might need to enable the extra repositories (servers where software packages are kept).  Xmms is not installed by default in the Ubuntu distribution.  It should be but that is another issue.  
Under add/remove programs:  search for xmms and click "show unsupported applications"

Click advanced and that takes you to the synaptic package manager--this is the program that is doing the work behind add/remove.  Go to settings-->repositories.  Click +ADD.  Click the four boxes:
Officially Supported, Restricted, Community, Non-Free

This will give you maximum exposure to available packages.

Search on xmms and hit apply.

Good luck and happy streaming (I like somafm.com)
Terry

---

### Post by lyceum on 2007-02-21
Click on the "Install Anything" link in my signature. If that does not help, or you want a faster way try [Automatix](http://www.getautomatix.com/).

---

### Post by Maestro23 on 2007-02-21
> **the_alch3m1st said:**
> I tryed to intall xmms to play mp3's.
I am conected to the internet i am writing this form ubuntu.

You will need mp3 plugins as well.  Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

---

