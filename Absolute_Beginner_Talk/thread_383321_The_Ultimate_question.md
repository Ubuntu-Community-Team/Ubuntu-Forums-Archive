---
title: "The Ultimate question"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Damo1976 on 2007-03-13
Dear Ubuntu users,
I am hoping some of you out there can help me and many others in my position.

I would class myself as an advanced non-technical computer user. I.e. I know my way around windows and can cope with a bit of CLI if instructed, but don't have the knowledge to start delving deep into operating systems to get a PC working.  I explain this to begin with as I want anyone who helps me to understand my ability (or lack thereof) before asking me to adjust the whatsit config file and assuming I'll understand.

Here (finally) is what I want.

I have a modern laptop with a dual core processor, and twin 100GB hard drives with raid.  I am sick to death of Windows and Microsoft, and desperately wish to use an alternative.  I couldn't afford the xtra £1,000 for a PowerMac, so I'm hoping ubuntu is the answer.  
I would like to be given the option of doing one of three things on startup:
1. Run Ubuntu
2. Run Windows
3. Run both - in the same way Mac users with Dual Core processors can run Mac OS and Windows.

I'm not ready for the big jump over to Ubuntu 100% as there are still many programmes I rely on that are Windows based, so this would be ideal for me.

Also, from reading these forums, I am concerned that I'll probably have all sorts of problems getting various pieces of hardware to work with Ubuntu.  Is easy ubuntu the answer, or is this still just a problem?

I honestly think that if these questions could be tackled (or if they have been already - then the answers need to be more obviously available) it would open Ubuntu up to so many more users. 

Kind regards,

Damian

---

### Post by xyz on 2007-03-13
Hi Damian,
I'd download the Ubuntu Live Desktop CD, burn the iso and boot on it. And see how your computer responds.
Dual boot is no problem.

---

### Post by hyper_ch on 2007-03-13
And you can running ubuntu within windows through VmWare or Micrsofot Virtual Machine (it's called different now I think)... or you can run windows within Ubuntu with VmWare, Virtualbox or Xen...
I guess there are more virtualization programs out there but those are the few I know.

---

### Post by xyz on 2007-03-13
There's even an install.exe....
[run Ubuntu within Windows]("https://wiki.ubuntu.com/install.exe/Prototype")

PS: Hi there...hyper_ch...from xyz_ch!

---

### Post by nalmeth on 2007-03-13
Remember, you are reading posts on a support forum. People post here when they have problems, those who don't have problems don't often come and report it (until they do :) ), and those that do don't spur all too much discussion.

The amount of hardware problems on THIS SUPPORT FORUM does not necessarily reflect Ubuntu's performance with an average PC's hardware. 

Dual-booting will be setup automatically if you have Windows installed. Before you install, defrag windows +1 times.

RAID is an issue I'm not familiar with, as I don't have RAID. Apparently software-raid is how it functions in ubuntu (sometimes less appropriately called fake-raid), you may want to do some reading about that before you dive in.

EDIT: As enticing as it looks, and as useful as it will be, the ubuntu.exe is not a way to realistically and functionally use Ubuntu. Yet. 
I have my own thoughts about it, which I will keep to myself, I simply recommend you do it the right way first.

---

### Post by Damo1976 on 2007-03-13
Wow, can' believe the quick responses!
Thanks for all your help.

So just to clarify this.

I should install Edgy on my laptop, using the normal iso download- burnt to a cd.
Ths will AUTOMATICALLY give me a choice of operating system to boot into on powering up.

I can then run VM machine, so that if I have booted into Ubuntu, I can flick into Windows when necessary, and when I have begun in Windows I can flick into Ubuntu.  - Howevr if I understand correctly, the OS that is selected first will be the only one that will really run properly?

Thanks again.

Damian

---

### Post by 3rdalbum on 2007-03-13
> **Damo1976 said:**
> 
I should install Edgy on my laptop, using the normal iso download- burnt to a cd.
Ths will AUTOMATICALLY give me a choice of operating system to boot into on powering up.

Yes, as long as you tell it to resize your existing partition. It gives you that option during the install.

> I can then run VM machine, so that if I have booted into Ubuntu, I can flick into Windows when necessary, and when I have begun in Windows I can flick into Ubuntu.  - Howevr if I understand correctly, the OS that is selected first will be the only one that will really run properly?

True. The virtual machine software does not come with Ubuntu, but it's possible to add it. I wouldn't recommend trying to get it working immediately - it requires quite a few steps, and getting to grips with your new operating system should be your first priority.

---

### Post by nalmeth on 2007-03-13
A clarification

You can't flick into Ubuntu/Windows installed on the other partition. You will have to reboot.

A virtual machine installs the OS on a virtual drive on the current install, be it Windows/Ubuntu. When you start the virtual machine, you are running both OS's at the same time, which can hog a lot of CPU. You pointed out a capable system though, and you should be able to handle it. 

Of course I may be misunderstanding _you_! I understand that since Mac's have intel processors they can now run windows aswell, but from what I gather, you really mean simultaneously.

---

### Post by Damo1976 on 2007-03-14
I have installed feisty from the exe installer, but it hasn't worked.
I see others have the same problem when installing it from the cd too.

Also, it never gave me an option of sizing the partition.

Any help out there?

---

