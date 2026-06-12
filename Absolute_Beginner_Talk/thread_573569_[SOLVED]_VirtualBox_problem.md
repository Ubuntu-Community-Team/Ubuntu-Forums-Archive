---
title: "[SOLVED] VirtualBox problem"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2007-10-11
I have installed VirtualBox and it works very well. The problem I have is trying to set up a shared folder. I used the instructions found on [http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/) to install and tried to follow the instructions on [http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/](http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/) but when I type in VBoxManage sharedfolder add WinXP -name “sharedfolder” -hostpath “/home/jason/Share” I get this in the terminal, any idea how I can fix this?:

 jason@jason-laptop:~$ VBoxManage sharedfolder add WinXP -name “sharedfolder” -hostpath “/home/jason/Share”
VirtualBox Command Line Management Interface Version 1.5.0
(C) 2005-2007 innotek GmbH
All rights reserved.

[!] FAILED calling machine->CreateSharedFolder(Bstr(name), Bstr(hostpath)) at line 6037!
[!] Primary RC  = 0x80070057
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80070057
[!] Text        = Shared folder path '“/home/jason/Share”' is not absolute
[!] Component   = SharedFolder, Interface: ISharedFolder, {8b0c5f70-9139-4f97-a421-64d5e9c335d5}
[!] Callee      = IMachine, {31f7169f-14da-4c55-8cb6-a3665186e35e}

---

### Post by pollywog on 2007-10-11
I'm assuming that we are talking about a Ubuntu host, and an XP guest, right? Well, honestly, those install instructions seemed a little difficult to follow. I would recommend that you follow the instructions that are in the user's manual (CHM) that should be located in opt/Virtualbox folder. It has fairly straightforward instructions on how to do this. Be sure to check out the instructions in 11.4.6 "USB not working" to properly configure your USB. I always set up my shared folders entirely through the disk manager inside virtualbox, as far as the ubuntu side goes. I only open a terminal (DOS prompt) inside XP. By the way, you did install "guest additions" didn't you? that is needed for file sharing/ mouse integration/ shared clipboard.

---

### Post by slughappy1 on 2007-10-12
Well following the guide  I said earlier, I was able to get my USB working perfectly and I already installed the guest packets. But I will check out the manual that you said to get the shared folders to work. Thanks

---

### Post by Orbital75 on 2007-10-12
I'll go ahead and warn you, don't bother going to the Virtual Box Forum unless you want
your question to go unanswered. I honestly don't know why they have a forum, it's just
wasting Bandwidth. 

That said, I'll see if I can find you an answer on your issue.

---

