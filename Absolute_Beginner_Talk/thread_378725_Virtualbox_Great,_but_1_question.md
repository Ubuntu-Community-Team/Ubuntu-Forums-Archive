---
title: "Virtualbox: Great, but 1 question"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by kevmartin on 2007-03-07
Hi,

After experiencing trouble getting getting wine to work, I looked for another solution and saw Virtualbox getting heaps of compliments here, so I gave it a go.  So far, it seems great - not a single hitch (except for some learning problems on my end lol - I should concentrate on what I'm doing a little more sometimes instead of multitasking).

I did get stuck for a while trying to figure out how to get the mouse pointer out of the Windows box I now have running underneath Ubuntu. I was assuming "Control_R" (the magic key to get out of the virtual box) was "Control"+"R" keys - when actually is turns out it is the right-hand-control-key :-) ). But that's solved.

My problem now is I can't work out a way to get files to or from the Windows box/'partition' - other than via cd-rom or floppy (and the only floppy I have is external USB one anyway).  One of the major reasons for me to need Windows on my system is to run graphics apps, so naturally I need to save those back into my normal workspace, which I want to be Linux.

Any ideas on this?  Can I mount the linux system somehow in Windows, or vice versa, or failing that, I have a USB HDD - can I use that as a transfer medium somehow?

Oh - then theres the secondary issue that I need to phone Microsoft today and talk them into reactivating Windows for me as it failed the activation - a chore I've never needed to deal with before - should be "fun".

Thanks

---

### Post by FesterHead on 2007-03-07
Create a sharedfolder using VBoxManager then load it with the host OS.
VBoxManage sharedfolder add "VM name" -name "sharename" -hostpath "C:\test"

In a Windows guest, use the following command:
net use x: \\vboxsvr\sharename

In a Linux guest, use the following command:
mount -t vboxsf [-o OPTIONS] sharename mountpoint

See also the following section of the [User Manual PDF]("http://www.virtualbox.org/download/UserManual.pdf"):
5.4 Folder Sharing


For the mouse, install the Windows Guest Additions for seamless mouse integration.

---

### Post by Medieval_Creations on 2007-03-07
Your USB HD is an option, but only if FesterHead's suggestion doesn't work.

[QUOTE=FesterHead]Create a sharedfolder using VBoxManager then load it with the host OS.
VBoxManage sharedfolder add "VM name" -name "sharename" -hostpath "C:\test"

In a Windows guest, use the following command:
net use x: \\vboxsvr\sharename
[/QUOTE]

I use both USB & shared drive in VBox.  The network drive is probably the easiest.

But here's a thread that should help if you have to go the USB route.
[http://www.ubuntuforums.org/showthread.php?t=341740](http://www.ubuntuforums.org/showthread.php?t=341740)

---

### Post by kevmartin on 2007-03-07
Thanks for replies to you both - I'm sure the suggestions will work fine.

First I think I need to delete and start again on teh windows installation though.  I have lost access to my virtual windows due to a screen resolution change.  As I have not installed any apps etc yet, an hour's battling with it (and posts from others here with similar problems) has convinced me to scrap it and start again (and this time settle for the 1024 screen resolution I had working fine (it was only when I tried raising it to 1600 x 12 00  (my normal resolution in native windows) that it all went to hell :-)

We live and learn

Thanks again

---

### Post by dosmode on 2007-03-07
Okay... I did a lot of search on this virtualbox thingy but still could not get a solid idea to what it does exactly... I am thinking that it allows one to run windows and its programs in a "virtual" mode under a Linux platform... If this is the case then I can't wait to try it... in fact if this is the case and I can get it to run on my system then it is like practically having your cake and eating it, i.e. until I can fully get acclimatized to Linux... Question though... if this is the case will it do a virtualization of Windows if it is installed on the same system... actually, on the same harddrive... or does it work only if it is networked to a computer running windows....?

---

### Post by bob-aptllc on 2007-03-07
kevmartin,

Setting up the shared folder didn't work on my machine for some reason. I'm running Ubuntu 6.10 (Edgy) with virtual Windows 2000. To create a shared folder, I setup SAMBA to network within the single machine between the host and guest virtual machine. In this way, the two can share files using a FAT partition on the host. Here is a guide to setting up SAMBA: [http://www.ubuntuforums.org/showthread.php?t=76647](http://www.ubuntuforums.org/showthread.php?t=76647). 

After your guest is running, click on Devices / Install Guest Additions to install Guest Additions. Restart the host computer. Using Guest Additions, you will not have to work with capturing and releasing the mouse when changing between host and guest.

After Guest Additions is installed, start VirtualBox and your virtual machine. In the guest (via Control Panel if Windows is your guest) adjust display to the maximum colors. Do NOT change screen resolution in the Control Panel! Instead, save the new color settings in control panel and go to the Windows desktop. Resize the screen by clicking on VM / Auto re-size in the upper left. Your screen should now auto resize to fill your screen.

Bob

---

### Post by bob-aptllc on 2007-03-07
>  will it do a virtualization of Windows if it is installed on the same system... actually, on the same harddrive... or does it work only if it is networked to a computer running windows....?

VirtualBox will run Windows or other operating systems as a guest on the same physical machine as another host operating system. It does this by creating a virtual hard disk that can be stored on the same physical disk as that which the host operating system uses. You can learn more in the Ubuntu forums or see VirtualBox's site: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by dosmode on 2007-03-07
bob-aptllc said: > VirtualBox will run Windows or other operating systems as a guest on the same physical machine as another host operating system. It does this by creating a virtual hard disk that can be stored on the same physical disk as that which the host operating system uses. You can learn more in the Ubuntu forums or see VirtualBox's site: [http://www.virtualbox.org/](http://www.virtualbox.org/)
Thanks... that's all I needed to know.... I feel like I've won the jackpot and you bet I will give it a try...:) Boy... the learning never quits with Linux and that is what I love about it... keeps my neurons twitching...

---

### Post by kevmartin on 2007-03-07
Back up and running, but having trouble with the sharing still.  I wasn't really clear on what in the sample code given I was supposed to replace with what real information.

This is what I get from the VBoxManager:

```
kev@kev-desktop:~$ VBoxManage sharedfolder add "Windows" -name "kev" -hostpath "C:\Kev-Windows"
VirtualBox Command Line Management Interface Version 1.3.6
(C) 2005-2007 InnoTek Systemberatung GmbH
All rights reserved.

[!] FAILED calling machine->CreateSharedFolder(Bstr(name), Bstr(hostpath)) at line 5533!
[!] Primary RC  = 0x80070005
[!] Full error info present: true , basic error info present: true
[!] Result Code = 0x80070005
[!] Text        = The machine is not mutable
[!] Component   = Machine, Interface: IMachine, {fd443ec1-0009-4f5b-9282-d72760a66916}
[!] Callee      = IMachine, {fd443ec1-0009-4f5b-9282-d72760a66916}
[!] FAILED calling machine->SaveSettings() at line 5536!
[!] Primary RC  = 0x80070005
[!] Full error info present: true , basic error info present: true
[!] Result Code = 0x80070005
[!] Text        = The machine is not mutable
[!] Component   = Machine, Interface: IMachine, {fd443ec1-0009-4f5b-9282-d72760a66916}
[!] Callee      = IMachine, {fd443ec1-0009-4f5b-9282-d72760a66916}
```

I tried the Samba approach too.  No luck there either - probably also because I have no idea what I'm doing with replacing sample code with real information.  I set up the samba install OK and edited the conf file (hopefully correctly) - then tried to conenct from Windows in the Virtualbox, and couldn't find anythign (I had to create a network first or there is no MyNetwork Places to work from).  I've always found networking to be the one really confusing thing in life :-)

Any suggestions? If not I'll try the USB idea.

Thanks

---

### Post by FesterHead on 2007-03-08
For a Ubuntu host the hostpath needs to be a Ubuntu folder/mount.

For example I have an external hard-drive that gets auto-mounted as /media/sdb1 (ext3 filesystem) and I want to share that as Internal02 with a virtual box called "Windows XP Professional" I would use:
VBoxManage sharedfolder add "Windows XP Professional" -name "Internal02" -hostpath "/media/sdb1"

After starting up the Windows XP Professional host to get the share visible open a command prompt then to make drive X type in:
net use x: \\vboxsvr\Internal02

Now whenever I start the Windows XP Professional virtual box I get an X drive mapped to /media/sdb1

---

### Post by kevmartin on 2007-03-08
8-)  Thanks Festerhead - that's what I needed.  No problems at all - I now have my drives mapped into my virtual xp system.

I'm extremely impressed with Virtualbox all round - I dont know how but XP seems to do things faster than my native windows OS on the main partition, even though the virtual box is on a fraction of the RAM.  I guess it's a brand new OS install, maybe thats it.

Anyway I'm very happy, and a big step closer to getting rid of my main windows partition :-)

Thanks again

---

### Post by kevmartin on 2007-03-12
Now things are not looking so good any more :-(

Being one who never leaves well enough alone, always wanting to try something new, I upgraded from Dapper to Edgy.  Next time I tried to start Virtualbox, nothing happened.  After a few attempts, I downloaded and ran the installer for Edgy, hoping it would upgrade the Dapper packages.  It ran OK, and then Virtualbox would start again.  Unfortunately, the mapped shared drive connections are acting weird now.  Click on one and it will open, showing the contents, but try to open a file from it and it gives an error about the connection already being in use or whatever it is.

At the same time, my audio died, and after a lot of messing around, I found that if I start my PC using the boot menu option for the previous kernel (2.6.15 instead of 2.6.17, my audio is back, but the virtualbox won't start again.

Should I uninstall virtualbox completely and reinstall the Edgy version?  Or should I wait until the audio issue is solved properly (running an old kernel doesn't seem to be a solution, more of a workaround to me). Or is there a third alternative?

All advice most welcome.  Thanks.

---

### Post by Karbonik on 2007-03-20
I had no problems with the install, but I've been having a couple issues, and I'm not sure if it would be with the VBox tools or what.

I mounted the Vbox Network drive mapped to point at /media/

This works, and I get into my /media/  folder, and can view both the usbdisks (which is great because I don't have to lose the functionality of those disks in the main kubuntu area) but after a few seconds to a minute, I get a BSOD and everything resets. 

I tried doing a system restore ala windows to a point where I hadn't tried to install the bluetooth or integrated usb camera drivers, and I still get the same problem, which leads me to believe that it's something inherent with the network drive mapping and possibly a conflict with the drive as it is still being used in the main linux.

I didn't get the problem when I let the VBox take over my USB hub, but I run my email off the portable drive, and I'd prefer not to have to unplug and replug every time.  Additionally, it would be much easier to do what I really want to do with the VBox WinXP if I could simply transfer the configuration files from the mapped /media/sda1/ to the VBox C:\

Has anyone else had this issue?  I remember running across something about tweaking the VBox to not auto restart, so that I can read the XP BSOD message, but I don't recall where that was.

Another issue I have found is that after installing the drivers for the -real- hardware (Lenovo 3000N100 with integrated camera) I have not yet been able to get the camera to function correctly and capture an image - it seems to be caught in some kind of loop.

Lastly, the Bluetooth installed alright, but when I tried to sync with my Treo650 it ran into some kind of problem.  This would be much less of an issue, and it's probably just that I'm being lazy, but it would be nice.  I haven't quite figured out  yet how to get that sync going natively in Kubuntu, and if I could it would be a complete non-issue for the VBox.

Mainly, I just want the VBox around so that I can install all the programs like iTunes or whatever BS that my clients have on their machines so that I can help them when they call without having to physically reboot to XP or go to another machine.

Any assistance would be warmly welcomed.


-EDIT-

Ok, so now I can read the BSOD, and it says that there is a problem with VBoxSF.sys trying to write to read-only memory.  Anyone familiar enough with the way that InnoTek is doing things that can help me out with this?  I tried doing another system restore and mapped the network drive to 
net use e: \\vboxsvr\media
instead of 
net use e: \\vboxsvr\media\   (note - I took out the \ at the end, but it had no effect)

Could this be because /sda1 is NTFS and there are issues with the mount under linux that is keep it as read only for the VBox?

---

### Post by spynotebook on 2007-04-05
I have been having these same problems. I want to use VirtualBox to sync my itunes.  I have the ipod showing on there, but itunes is being a pain.

I mount a shared folder using the method described in this thread to /mnt/storage. This is where my music is. But, virtual Windows sees it as a read-only or locked disk, and crashes when itunes tries to access it.

If I connect through samba, it works, but is SOOOO slow.

Any ideas on the read-only status?

---

### Post by Bluecube on 2007-05-10
> **FesterHead said:**
> For a Ubuntu host the hostpath needs to be a Ubuntu folder/mount.

For example I have an external hard-drive that gets auto-mounted as /media/sdb1 (ext3 filesystem) and I want to share that as Internal02 with a virtual box called "Windows XP Professional" I would use:
VBoxManage sharedfolder add "Windows XP Professional" -name "Internal02" -hostpath "/media/sdb1"

After starting up the Windows XP Professional host to get the share visible open a command prompt then to make drive X type in:
net use x: \\vboxsvr\Internal02

Now whenever I start the Windows XP Professional virtual box I get an X drive mapped to /media/sdb1

I'm following the above instructions but I can't for the life of me get the new drive mapped in Windows. It keeps stating that the path can't be found. Any ideas? TIA

---

### Post by romprod on 2007-05-11
> **Bluecube said:**
> I'm following the above instructions but I can't for the life of me get the new drive mapped in Windows. It keeps stating that the path can't be found. Any ideas? TIA


Yeah me neither. Can't see the machine 'vboxsvr' on any of the network neighbourhood views but i can see the 'Virtual Box Shared Folders' icon but when i double click the icon is says unable to browse network.

---

### Post by Bluecube on 2007-05-12
I can't even see this Virtual Box SHared Folders icon! :( Have no idea what I'm doing wrong...

---

### Post by Eggnog on 2007-07-02
> **FesterHead said:**
> For a Ubuntu host the hostpath needs to be a Ubuntu folder/mount.

For example I have an external hard-drive that gets auto-mounted as /media/sdb1 (ext3 filesystem) and I want to share that as Internal02 with a virtual box called "Windows XP Professional" I would use:
VBoxManage sharedfolder add "Windows XP Professional" -name "Internal02" -hostpath "/media/sdb1"

After starting up the Windows XP Professional host to get the share visible open a command prompt then to make drive X type in:
net use x: \\vboxsvr\Internal02

Now whenever I start the Windows XP Professional virtual box I get an X drive mapped to /media/sdb1

I had been using VMware Server to run XP but I never could get it to map my real drives or share folders; I think it's possible but requires an exercise in gymnastics from what I could gather.   I tried Virtualbox because I read where you could easily map drives and folders from your other partitions.  It's true.

This worked out perfectly for me.  I now have my FAT32 drive that I share data with between Ubuntu and the "real" WinXP mapped to my Virtualbox XP installation.  This is exactly what I had been looking for.  This means no more having to boot into the "real" WinXP unless I have a major emergency or I want to play a game or two.  Once virtual machines can render 3D and recognize directx, Windows is gone from my machines.  

I tried another method from a blog but all I got there was error messages.  Now I'm going to map by "real" NTFS drive in to Virtualbox as well and I can move data around between all of them.  Thank you, FesterHead, for the information.

---

