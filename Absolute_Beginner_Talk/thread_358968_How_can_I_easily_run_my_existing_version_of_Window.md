---
title: "How can I easily run my existing version of Windows within Ubuntu?"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by TR3GO on 2007-02-11
Hello,
        
          I was wondering if anyone had an easy solution to **"...Running an existing partition of Windows within Ubuntu using vmplayer, vmware, etc."** I have looked at this tutorial: [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo) ... But it seems too technical for my newbie understanding of Unix/Linux right now. So if anyone has a detailed solution of doing this, I would greatly appreciate it!

Thanks! :) 
-Stefan

---

### Post by nickoli_02 on 2007-02-11
You can't actually run your "existing" version of windows on ubuntu, because your windows is on another partition. What that howto is talking about is virtualizing windows: installing a virtual machine in ubuntu. This allows you to use windows apps and such, without having to boot up the windows partition. If you want to try VMware player you can install it easily using automatix, then you can install XP using the install CD.

---

### Post by TR3GO on 2007-02-11
Oh I know what that tutrial is talking about, installing a fresh copy of Windows XP. I've seen tutorials which show you that you can run your exsiting copy of Windows XP on Ubuntu and running it as like a parallel so you can multi task. But I will try the VMPlayer app and give that a try. 

But if anyone actually knows of a simple how-to for running your original copy of Windows XP within Ubuntu, I would like to see.

Thanks

---

### Post by Crakie on 2007-02-11
I looked into this a while ago. It was too difficult for my taste to transfer an existing XP install to a virtual machine running in Ubuntu. The problem is that the drivers of the 'real' XP are not appropriate for the hardware emulated by the virtual machine. You *can* work around that, but I preferred just doing a fresh install on the VM.

If you really want to look into it anyway: you're looking for 'physical to virtual' (p2v). This is the best tutorial I could find: [p2v]("http://www.rtfm-ed.co.uk/?page_id=174").

---

### Post by nickoli_02 on 2007-02-11
ohh I understand now, sorry I don't have much experience with virtual machines. I wasn't aware you could virtualize your windows partition :)

---

### Post by DARKGuy on 2007-02-11
Um, excuse my intrusion but I have a small question about that wiki article... if I mount my physical C drive as -hda, and install the seamless rdp zip file in my pyhisical windows partition, will that work too? would I need to have qemu running my physical windows partition or in this case I wouldn't need qemu, but just seamless rdp installed in my windows partition and off I go?

---

### Post by veloce on 2007-02-11
I've seen some discussion on this forum for  running a *physical* windows installation within vmware server under Ubuntu. That is, you don't convert your windows at all, just run it.

Do a search for vmware and I'm sure you'll find it.

Last I looked the person had it running but windows wanted to be re-authenticated - "Your hardware has changed significantly".  (Hmmm, precisely the reason I moved to Ubuntu!)

---

### Post by aforonda on 2007-02-11
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

---

### Post by jmvbxx on 2007-02-11
I followed your advice and installed vmware thru automatix but it seems to be just a player and is looking for a vmware file.

Did I install the correct program?  Do I need to install the server version first?

Thanks!

---

### Post by TR3GO on 2007-02-11
Yea I know, thats what I'm trying to do as well... Install it in VMWare player... Anyone know whats further?

---

### Post by DARKGuy on 2007-02-12
[www.easyvmx.com](www.easyvmx.com)

VMWare Player needs a vmx file to "play" (which is basically a file with a virtual machine specifications). I've tested VMWare Server and is basically the same VMWare Workstation for Windows (or at least, it works like it) so it's WAY better for grabbing. Go for that one :)

---

### Post by aktiwers on 2007-02-12
I have used Peturr's guide (search the forum for "vmware windows xp") and its not really hard.

Its like installing XP, just the beginning of the guide is how to install Vmware, which is basically downloading a compressed file, uncompress it (drag and drop) and run the install script. I agree the guide looks hard, but if you read its, its pretty easy actually.

---

### Post by DARKGuy on 2007-02-14
Well, following the guide the author of this thread posted, it is possible to run ANY Windows app under Linux almost natively. You can use a physical PC or you can install WinXP/2000 Server in VMWare Server/Player, QEMU or Bochs. After installing, you just have to enable in the server machine to other users to connect to your PC (Control Panel -> System -> Remote -> Allow other users to connect to this PC). Make sure you have an user with a password set, else it won't work.

After that, there is a guide somewhere here (I can't find the link, but googling for "rdesktop 1.5 edgy" shall do) to install rdesktop 1.5, so all you have to do is build it (fairly easy) and there, follow the same instructions in the guide.

Only thing you'll have to change is localhost:3389 if you're not using QEMU, and if you're using a physical PC, just change it by the computer's IP (no :3389, just the IP) and you're set.

Meh, it's late but maybe I'll make a HowTo later :D

I wasn't able to run my existing Windows partition though :( so I had to do a clean XP install (933Mhz/256Mb RAM, you can imagine how long it took xD) because QEMU boots and before going to the boot logo screen, it "crashes" and shows some random color squares on the screen. VMWare loads but after the boot screen it throws a BSOD. Anybody got a workaround for these two?

Here's a living proof that you can do such :)

[img]http://img458.imageshack.us/img458/4788/omg2zo0.jpg[/img]

---

### Post by ramjet_1953 on 2007-02-14
Try VirtualBox.

It is Open Source and works ike a dream.

Regards,
Roger 8-)

---

### Post by aktiwers on 2007-02-14
Darkguy, you should make that HOWTO..  that looks cool, and I havent see it before!

---

### Post by DARKGuy on 2007-02-14
> **aktiwers said:**
> Darkguy, you should make that HOWTO..  that looks cool, and I havent see it before!

There :)

[http://ubuntuforums.org/showthread.php?p=2156057](http://ubuntuforums.org/showthread.php?p=2156057)

YAY my first HowTo, I'm HAPPY xD

---

### Post by aktiwers on 2007-02-14
Looks awesome! Gonna try it when I have some more time!
Thanks!! :)

---

### Post by Drakkor on 2007-02-14
I second ramjet; VirtualBox  :D  But be sure to have at least 512mb ram, a gig would be better.

---

### Post by DARKGuy on 2007-02-14
*shrugs* I'm gonna give VirtualBox a try and see if RDP can be done with it too, yay! - damn, I have 256Mb T_T *tries anyways*

---

### Post by mjpatey on 2007-02-19
Try this tutorial:

[http://www.howtoforge.com/vmware_converter_windows_linux](http://www.howtoforge.com/vmware_converter_windows_linux)

Step-by-step instructions, with screenshots at every turn!

-Mark

---

### Post by netgineer on 2007-06-30
> **TR3GO said:**
> Hello,
        
          I was wondering if anyone had an easy solution to **"...Running an existing partition of Windows within Ubuntu using vmplayer, vmware, etc."** I have looked at this tutorial: [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo) ... But it seems too technical for my newbie understanding of Unix/Linux right now. So if anyone has a detailed solution of doing this, I would greatly appreciate it!

Thanks! :) 
-Stefan

Try looking at this:

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)


This will allow you to run an existing XP installation as a VM in VMWare Server. You install it on your current Windows machine and point VMWare to the Windows partition.

I am  looking at doing this for my home machine. At work, I'm running Feisty and using VMWare Server 1.03 to run XP and Suse 10.1 in VMs  - both scratch installs, not pre-existing ones - and loving it.  :)


(tagline not made yet)

---

### Post by lbriner on 2007-06-30
I have just installed vmware. It was very easy and ran like a dream. First, I downloaded and ran the vmware converter on my Windows system and saved the files it created to my external hard disk. I then installed Linux on my laptop overwriting the whole disk. I copied the Windows VMWare files from my external harddisk onto my Linux disk (into my home directory) installed vmware-player (not the server) onto my laptop. Ran up the player, picked the VMWare file that I had just copied from the hard disk and it ran up fine. It took a while because it was reconfiguring drivers and IMPORTANT it will ask you to re-activate XP because the hardware is seen to change in Windows. Note you will need at least 1Gb of memory to get decent performance in VMWare player. Alternatively you can use Wine to run Windows apps inside Linux but this will not run XP itself, just the apps and probably not all of them either!!

---

### Post by curtis on 2007-06-30
Try creating a fresh hardware profile, that might fix the bsod issue. Some information at [http://support.microsoft.com/kb/225810/](http://support.microsoft.com/kb/225810/)

---

