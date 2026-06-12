---
title: "Vista (or Ubuntu) boot after install"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by mdoyle on 2007-03-13
Background. I have an HP Pentium D machine with two hard drives. The first hard drive originally just had my Vista install, the second was only used for storage of documents/images/videos.

I put the Live CD in and began the install. I resized the 1st hard drive (that holds my Vista install) and created the new partitions for Ubuntu. They were created fine, and so I continued the install.

After the install was done, it asked me to restart, so I did. During the restart I noticed that there was no option to choose between the two OS'. That bothered me (but not too much, figured there might be something more), but then Vista hung on loading.

I tried to run it in Safe Mode and it hung up. Tried booting from the Vista DVD, and it hangs up as well.

I'd like to get both working, but Vista is the priority right now. Any ideas?

---

### Post by mdoyle on 2007-03-13
I'm starting to agree.

I've been here for 5 hours trying to install Ubuntu in a dual boot with Vista with no luck. People were saying it's easier to install than Windows, but I don't remember a Windows installation being this complicated since 98.

---

### Post by slayerboy on 2007-03-13
I don't understand what's complicated about a point and click interface to installing Ubuntu?  It's the easiest it's ever been to install, and the quickest.  I'm not familiar with the OP or your problems, but is it just getting hardware configured AFTER you install?

Don't give up on Linux.  My suggestion is to try PCLinuxOS, which is a pretty good distro and very easy to use and install.  Some people have had good luck with getting it to work over ubuntu.

---

### Post by mrbungle on 2007-03-13
really what are you having problems with? im a linux newbie and found the install the fastest and easiest i have ever seen.

---

### Post by mdoyle on 2007-03-13
The fact that it rendered my Vista useless without finishing an install and being on a totally different hard drive for one. Or now that I can't even boot from the Vista DVD and now I have to pull a HDD from another computer, copy any files that Ubuntu somehow detroyed, and then boot into it.

I really want to get it running, but I suppose there is a reason why M gets that little symbol ($), it works.

---

### Post by tcpip4lyfe on 2007-03-13
Why cling to M$ in a dual boot setup?  What program do you need to run in windows?

---

### Post by yabbadabbadont on 2007-03-14
> **mdoyle said:**
> The fact that it rendered my Vista useless without finishing an install and being on a totally different hard drive for one. Or now that I can't even boot from the Vista DVD and now I have to pull a HDD from another computer, copy any files that Ubuntu somehow detroyed, and then boot into it.

I really want to get it running, but I suppose there is a reason why M gets that little symbol ($), it works.

If you can't boot the Vista DVD, then you have bigger problems than a failed Ubuntu install.  Booting from DVD is strictly a function of the BIOS in your machine and has nothing to do with Ubuntu.  Perhaps your machine failing to boot the Vista DVD is another symptom of the same problem that caused your failed Ubuntu install...

---

### Post by nalmeth on 2007-03-14
mdoyle, from what computer are you typing now?

I don't know anything about Vista, like if it needs defragging or not. Shrinking a fragmented NTFS partition is a common cause of this type of problem.

It also sounds like GRUB (Ubuntu's bootloader which should show Ubuntu + Vista) did not install. 

The following may be a way to get Ubuntu (if not both) to show up, from which you can recover your files. TAKE CARE NOT TO FORMAT ANYTHING! This guide simply takes you back into the install process, and will try to reinstall GRUB. 

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

EDIT: Before you go on, can you confirm that GRUB does not load? Only Vista's bootloader, which doesn't properly boot vista?
I read in this page: [http://www.pro-networks.org/forum/about78184.html](http://www.pro-networks.org/forum/about78184.html)
That with a change in NTFS in Vista, no partitioning program, windows or linux can properly resize Vista's NTFS. This may be what killed your Vista install

I suggest you read that article, and do some more research before advancing any further. Ask questions here when you run into something confusing. 
I may not be around to help the whole way, but I will try to check back on your thread when I can.

---

### Post by mdoyle on 2007-03-14
> **tcpip4lyfe said:**
> Why cling to M$ in a dual boot setup?  What program do you need to run in windows?

How about all my VPN software for work? Until I can find a Cisco VPN client for Linux, M has to stay.

> **yabbadabbadont said:**
> If you can't boot the Vista DVD, then you have bigger problems than a failed Ubuntu install.  Booting from DVD is strictly a function of the BIOS in your machine and has nothing to do with Ubuntu.  Perhaps your machine failing to boot the Vista DVD is another symptom of the same problem that caused your failed Ubuntu install...

Although I believed that too, I disconnected the HDD that Ubuntu was installed on and the DVD ran fine. I was able to get my Vista install back. 

But here's a kicker. I reconnect the HDD that Ubuntu is installed on, go to boot to Vista, and it doesn't boot, haha. Ubuntu *sigh*

---

### Post by mdoyle on 2007-03-14
Im posting from my laptop.

I disconnected the hdd that ubuntu is installed on and was able to get vista to boot. I also managed to get grub to work.

Now that vista was running from my single hdd, i reconnected the one that has ubuntu on it. chose vista from grub and vista doesnt boot.

when i boot to ubuntu i get video errors galore.

---

### Post by yabbadabbadont on 2007-03-14
> **mdoyle said:**
> How about all my VPN software for work? Until I can find a Cisco VPN client for Linux, M has to stay.



Although I believed that too, I disconnected the HDD that Ubuntu was installed on and the DVD ran fine. I was able to get my Vista install back. 

But here's a kicker. I reconnect the HDD that Ubuntu is installed on, go to boot to Vista, and it doesn't boot, haha. Ubuntu *sigh*

That is a sign of a problem with the way that Vista boots, not an issue with Ubuntu.  Vista must be trying to scan the partitions created by Ubuntu for some reason and it is causing it to hang.

---

### Post by nalmeth on 2007-03-14
I just saw your reply.

If you are dropped to a command line in Ubuntu, enter the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

When you get to selecting video driver, pick VESA

Depending on your video card, you may want to install the proprietary drivers from ATI or Nvidia, which is required to enable 3D

Make sure any instruction you are following is for Ubuntu.

---

### Post by tcpip4lyfe on 2007-03-14
[QUOTE=mdoyle;2295193]How about all my VPN software for work? Until I can find a Cisco VPN client for Linux, M has to stay.




Might not be as pretty as the windows client but a quick google turned up this among many others.

[http://www.math.dartmouth.edu/software/resources_Linux/vpn/cvpn.html](http://www.math.dartmouth.edu/software/resources_Linux/vpn/cvpn.html)

---

### Post by mdsmedia on 2007-03-14
> **yabbadabbadont said:**
> That is a sign of a problem with the way that Vista boots, not an issue with Ubuntu.  Vista must be trying to scan the partitions created by Ubuntu for some reason and it is causing it to hang.I installed Ubuntu Hoary, using some instructions I found on the web, without a flinch from XP. I upgraded to Breezy without a hitch....and installed Breezy on another machine...without a hitch.

I've since installed, and reinstalled Dapper, without a hitch, in dualboot with XP, I've upgraded the other machine to Edgy, all without problem. And I'm no expert.

It's so easy to blame the new OS (Linux) when the other (Vista) may well be the problem, or your installation of Ubuntu was a problem because you didn't follow instructions or did something wrong in the installation.

And to say that Windows just works is a joke in itself. If you had Ubuntu installed on its own, then installed Windows in dual-boot, see if your Ubuntu will boot. You trash the MBR and Ubuntu won't boot. If that's "just works" then give me Ubuntu anytime.

---

### Post by mdoyle on 2007-03-14
I'm not even able to make it to anything. My screen flickers like crazy, i've let it sit for 10 mins to see if anything else happens and it doesn't.

I'm still trying to figure out why Vista will load when the Ubuntu HDD isn't connected, but won't when it is. Doesn't seem to make much sense.

---

### Post by nalmeth on 2007-03-14
OK, when the screen is flickering like that, hit CNTL-ALT-F6, which will drop you to a virtual terminal. From there, enter this command:
```
sudo /etc/init.d/gdm stop
```
Then follow the directions in my previous post.
To restart the Xserver you can issue this command:
```
sudo /etc/init.d/gdm start
```
I can't explain the HDD - Ubuntu/Vista situation either :)
I've never dual-booted with Windows, so I can only sympathize with your situation.

---

### Post by mdoyle on 2007-03-14
A new problem. My keyboard isn't getting any power. It's an HP PS2 keyboard.

---

### Post by nalmeth on 2007-03-14
Wow.

OK, when you boot up, and you see GRUB loading, hit ESCAPE immediately, and if the keyboard works, go to recovery mode, and try the 
dpkg-reconfigure xserver-xorg
from there.

It's possible there is a problem with the XServer that causes your keyboard problem. 

If after this it still doesn't work, I will have reached the limit of my knowledge. 
I use a USB keyboard

---

### Post by mdoyle on 2007-03-14
Well thanks for your help. Ubuntu now loads and my keyboard works.

For anyone that is following along..

Windows remembers the partitioning of drives when you first install it, my problem is what may have at one time been Disk 1 might not be Disk 2 or 3 after creating the partitions for Ubuntu. All I have to do is figure out exactly what disk was changed, edit the Boot Manager (which now has it's own command line utility in vista) and that is *suppose* to fix it.

Now when I go to Networking under the System toolbar I get "The configuration could not be loaded. You are not alloed to access the system configuration", any ideas?

---

### Post by gus sett on 2007-03-14
**return visit**
found puccaso's reply #25 to Stevo0687 easy to follow. molly_001 had
a more extensive treatment I haven't delved into.  Both can be found
by searching on triple boot vista.

just found this thread so welcome aboard.  Glad you have the patience
to go bilingual.  I have an HP laptop with *one* drive of typical portable
size and Vista so far, so reliable boot loading between these pups is like a 
security blanket. Keep trucking, so to speak 8-) :arrow: 

> **mdoyle said:**
> Well thanks for your help. Ubuntu now loads and my keyboard works.

For anyone that is following along..

Windows remembers the partitioning of drives when you first install it, my problem is what may have at one time been Disk 1 might not be Disk 2 or 3 after creating the partitions for Ubuntu. All I have to do is figure out exactly what disk was changed, edit the Boot Manager (which now has it's own command line utility in vista) and that is *suppose* to fix it.

Now when I go to Networking under the System toolbar I get "The configuration could not be loaded. You are not alloed to access the system configuration", any ideas?

---

### Post by mdoyle on 2007-03-14
Update:

I did some more research, and when I shrank the partition that was on the hard drive that Ubuntu ended up being installed on the partitioner may have changed the partition numbers. Vista's new NTFS file system isn't compatible with this procedure, and so every time I would boot into Vista with the Ubuntu HDD plugged in, Vista looked at the partition it used  (only for storage) and would hang on start up, because it now had a Linux file system installed on it.

I put the HDD into an XP machine (that uses an older NTFS system), copied all my files from that particular partition to an external HDD, deleted the partition, put it in my main machine, booted into Vista, recreated the partition and copied my files over. I now have a fully functional dual boot computer with Ubuntu and Vista.

Now I can finally start testing Ubuntu and seeing why everyone raves over it.

---

