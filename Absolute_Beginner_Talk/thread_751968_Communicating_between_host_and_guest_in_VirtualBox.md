---
title: "Communicating between host and guest in VirtualBox"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by RobHK on 2008-04-11
I have been playing with Ubuntu for about six months fairly regularly, but am still using XP Home as my main system. Yesterday I decided to try Mint, which, as I am sure most people on here are aware, is really Ubuntu with a different skin.

I have my main XP installation multi-booting with a Mint and an Ubuntu installation, but the Ubuntu is corrupt and I am waiting for the Heron before I reinstall it, so for the moment I'm going with the Mint installation. (Mint can see all the drives/folders on my main XP installation.)  I installed VirtualBox on the Mint system and XP on VirtualBox as the guest system. My main issue is that the XP guest doesn't see any of the folders/drives that my Mint or main XP systems see, with the sole exception of a CD drive. I can't for example see my USB external hard drives

I have Googled and find that it is possible to see USB drives and to share folders, but the explanations I found were too complicated for me. If someone could explain in Linux newbie terms how to go about this I'd be most grateful. Don't worry about the Mint thing. Once under the skin it appears to be pure Ubuntu.

If there is a better place to ask this question, I'd welcome advice on that too.

---

### Post by kpkeerthi on 2008-04-11
I find [this]("http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/") to be simple, step-by-step and easy to understand. You may want to give a try.

---

### Post by RobHK on 2008-04-11
Thanks very much for the reply. The instructions are certainly clear and straightforward, but unfortunately they don't seem to work for me.

I entered 2 folders (by browsing), my Desktop and my Documents, in the shared folders in Settings. I then launched the guest XP and followed the instructions to the letter but VirtualBox shared folders was not present in the Entire Network folder. Neither was the VBOXSVR xfer folder present.

---

### Post by mister_pink on 2008-04-11
Have you installed the guest additions? You mount them in one of the menus when the guest is booted, and then it comes up as a cd.

---

### Post by lswest on 2008-04-11
did you install the virtualbox guest additions before trying to share files?

*EDIT* damn, beaten to it :P

---

### Post by RobHK on 2008-04-11
> **mister_pink said:**
> Have you installed the guest additions? You mount them in one of the menus when the guest is booted, and then it comes up as a cd.

I'm sure I haven't, but I don't really understand either. Could you tell me step by step what to do? What menus are you referring to? And how do I mount them?

When the guest is booted I don't appear to have any access to the  host.

---

### Post by lswest on 2008-04-11
when you start the vm, it should be in Devices-->install guest additions.  It should then mount a CD for you to install the additions from.

---

### Post by RobHK on 2008-04-11
> **lswest said:**
> when you start the vm, it should be in Devices-->install guest additions.  It should then mount a CD for you to install the additions from.

I'm sorry. I really do appreciate that you are trying to help me, but I just don't understand. Where is this Devices menu? In VB? In Ubuntu? In Windows? I'm assuming it's in VB, but I can't find it.

---

### Post by hyper_ch on 2008-04-11
well, you could also do port forwarding from your host to your guest... that way you could access it with all kinds of software...

---

### Post by RobHK on 2008-04-11
> **hyper_ch said:**
> well, you could also do port forwarding from your host to your guest... that way you could access it with all kinds of software...

Sorry, but this completely over my head. I haven't a clue what port forwarding is.

---

### Post by drsox1899 on 2008-04-12
Here's how to do Guest Additions .

1. Run your virtual WinXp.
2. Top of the Screen is a row of Menus : Machine, Devices, Help. Select Devices.
3. Drop down to Mount CD/DVD-ROM>CD/DVD-ROM Image.
4. You should then see VBoxGuestAdditions_1.5.(depends on your version).iso
5. Click Select.
6. This will then mount the .iso image as if it were a CDROM in your CD drive..  Have a look at the CDROM icon in the virtual WinXp just as if it was a normal machine.  Sometimes it will auto start.  If not, then select Explore and click the Install/Start exe programme.
7.  This will trick WinXp into installing VBoxGuestAdditions as if it were just another Windows install. 

This will give you much better access and usability (mouse etc etc).

Hope this helps.

):P

---

### Post by RobHK on 2008-04-13
Thanks a lot for the reply. I have to go out today and tomorrow, but I'll give it a try on Tuesday and report back what success I have. :)

---

### Post by RobHK on 2008-04-15
> **drsox1899 said:**
> Here's how to do Guest Additions .

1. Run your virtual WinXp.
2. Top of the Screen is a row of Menus : Machine, Devices, Help. Select Devices.
3. Drop down to Mount CD/DVD-ROM>CD/DVD-ROM Image.
4. You should then see VBoxGuestAdditions_1.5.(depends on your version).iso
5. Click Select.
6. This will then mount the .iso image as if it were a CDROM in your CD drive..  Have a look at the CDROM icon in the virtual WinXp just as if it was a normal machine.  Sometimes it will auto start.  If not, then select Explore and click the Install/Start exe programme.
7.  This will trick WinXp into installing VBoxGuestAdditions as if it were just another Windows install. 

This will give you much better access and usability (mouse etc etc).

Hope this helps.

):P

Sorry I couldn't deal with this earlier, though I did post to let you know.

I did as you suggested but I can't see VBoxGuestAdditions. From what other posters wrote earlier I can see that I need to install this at some point, but I'm afraid I don't know where or how I should have done it. Do you think you could offer me some guidance on this please?

Much appreciated.

---

### Post by mister_pink on 2008-04-15
How far into his instructions did you get stuck?

---

### Post by AClark on 2008-04-15
VBoxGuestAdditions.iso  should have been part of your original VirtualBox installation. 

 In my Fiesty setup it  was put in /usr/share/virtualbox  and will show up in the "Devices>CD/DVD-ROM>CD/DVD-ROM Image" menu just as drsox1899 says.

You may want to check just to see if the .iso file is in that location.  If it's not that could explain why you can't see it in the Devices menu of your XP VM.

I did my installation from synaptic package manager.  I suppose if you used a different method that "might" explain it.    Or maybe there is something different about Mint.  Just a wild quess I have no knowledge of Mint.

Right clicking on the VirtualBox entry in Synaptics and choosing properties will give you a list of installed files and their locations

Good Luck !

---

### Post by shillizzle on 2008-04-15
when you start the guest os it starts in a seperate window, and in the top left corner of the new window (guest os) is where you will find the device menu. hope this helps.

---

### Post by dondad on 2008-04-16
> **RobHK said:**
> I have been playing with Ubuntu for about six months fairly regularly, but am still using XP Home as my main system. Yesterday I decided to try Mint, which, as I am sure most people on here are aware, is really Ubuntu with a different skin.

I have my main XP installation multi-booting with a Mint and an Ubuntu installation, but the Ubuntu is corrupt and I am waiting for the Heron before I reinstall it, so for the moment I'm going with the Mint installation. (Mint can see all the drives/folders on my main XP installation.)  I installed VirtualBox on the Mint system and XP on VirtualBox as the guest system. My main issue is that the XP guest doesn't see any of the folders/drives that my Mint or main XP systems see, with the sole exception of a CD drive. I can't for example see my USB external hard drives

I have Googled and find that it is possible to see USB drives and to share folders, but the explanations I found were too complicated for me. If someone could explain in Linux newbie terms how to go about this I'd be most grateful. Don't worry about the Mint thing. Once under the skin it appears to be pure Ubuntu.

If there is a better place to ask this question, I'd welcome advice on that too.

Which version of virtual box did you install? The one in the repos is the open source version that does not have support for usb. If you need usb, you need to go to the virtualBox website and install the proprietary version. It is still free, but not open source.

---

### Post by drsox1899 on 2008-04-16
> **RobHK said:**
> Sorry I couldn't deal with this earlier, though I did post to let you know.

I did as you suggested but I can't see VBoxGuestAdditions. From what other posters wrote earlier I can see that I need to install this at some point, but I'm afraid I don't know where or how I should have done it. Do you think you could offer me some guidance on this please?

Much appreciated.

To repeat another forum poster - how far did you get in the list ?

Perhaps you can list your progress as follows :

Step 1.  OK (or not)
Step 2.  OK (or not)

etc

---

### Post by RobHK on 2008-04-16
> **dondad said:**
> Which version of virtual box did you install? The one in the repos is the open source version that does not have support for usb. If you need usb, you need to go to the virtualBox website and install the proprietary version. It is still free, but not open source.

Several people to thank at once, so thanks all of you. 

I am indeed using the repository version. I'll check the proprietary version out tonight. For the moment I'm working, and I have to work in my normal XP installation, for the moment at least.

I'll report back on my success. This really is a helpful group. Thanks again to all of you. :)

---

### Post by quinnten83 on 2008-04-16
I actually have the reverse problem.
i have windows XP host and linux guest.
I don't know how to setup the share folder.
I've tried using nautilus to browse to shared folders on the "network" and see if i can see the shared folder, but i couldn't. Guest additions is allready installed.
can anybody direct me to a howto with pretty pictures please?

---

### Post by RobHK on 2008-04-17
> **RobHK said:**
> Several people to thank at once, so thanks all of you. 

I am indeed using the repository version. I'll check the proprietary version out tonight. For the moment I'm working, and I have to work in my normal XP installation, for the moment at least.

I'll report back on my success. This really is a helpful group. Thanks again to all of you. :)

Well, I uninstalled the repository version and installed the one from the site, and everything is now working fine.

Thanks again to everyone who helped :)

---

### Post by RobHK on 2008-04-23
> **dondad said:**
> Which version of virtual box did you install? The one in the repos is the open source version that does not have support for usb. If you need usb, you need to go to the virtualBox website and install the proprietary version. It is still free, but not open source.

Got the proprietary version and it's running very nicely. I have CD access and have set up two partitions from shared folders as network drives. 

But  I can't see anything connecting via USB. Neither printer nor external HDD. This HDD has 3 partitions all visible and mounted in Linux. (The printer has no driver for Linux. Nice one Lexmark.) I don't get the Windows USB clunk when I connect, nor the "Safely remove" icon in the system tray. I've looked around but can't find any setting. Any pointers would be most appreciated.

---

### Post by mister_pink on 2008-04-23
In the virtual box program, before you start up the virtual machine, go on settings for your machine, then usb. tick the enable usb box. Then when its started up its in the devices menu, you have to tell it which usb devices to pass to the machine. Make sure you dont select your usb keyboard or mouse by accident if you have one!! It goes very wrong.

If things dont work, then you have to enable the usb fs thing. Check here for the best instructions I could find: [http://forum.notebookreview.com/showthread.php?t=242936](http://forum.notebookreview.com/showthread.php?t=242936)

---

### Post by RobHK on 2008-04-24
> **mister_pink said:**
> In the virtual box program, before you start up the virtual machine, go on settings for your machine, then usb. tick the enable usb box. Then when its started up its in the devices menu, you have to tell it which usb devices to pass to the machine. Make sure you dont select your usb keyboard or mouse by accident if you have one!! It goes very wrong.

If things dont work, then you have to enable the usb fs thing. Check here for the best instructions I could find: [http://forum.notebookreview.com/showthread.php?t=242936](http://forum.notebookreview.com/showthread.php?t=242936)

Thanks very much for the reply. Problem is I don't see any USB option in my Settings dialog. I don't know what the usb fs thing is but I'll take a look this evening when I have a little more time, and then report back here.

---

### Post by RobHK on 2008-04-28
> **RobHK said:**
> Thanks very much for the reply. Problem is I don't see any USB option in my Settings dialog. I don't know what the usb fs thing is but I'll take a look this evening when I have a little more time, and then report back here.

Pleased to say USB now functioning, after a certain amount of hassle. :). Thanks very much.

---

