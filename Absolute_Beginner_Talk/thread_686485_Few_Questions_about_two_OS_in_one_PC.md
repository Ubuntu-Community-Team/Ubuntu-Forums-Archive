---
title: "Few Questions about two OS in one PC"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Nty on 2008-02-03
So,I'm sick of Windows,I've downloaded Ubuntu and burned it,I've booted it from the disc and it was allot faster than Windows,and I want to install it,BUT,I'm not the only one using this PC,and to the other users its difficult to use Ubuntu,and they want to stay with Windows.
my question is-How do i use two operating systems on one PC? The instructions in the disc don't show how,and everything can find is to technical.
And is it possible to make it so you dont have to shut down the computer each time you want to switch operating systems?
If it's necessary- i have one hard disk that have 149 Giga,98.1 Giga are used,and  50.8 Giga are free. (Am I going to need to delete files?)
Thank you,Nty.

---

### Post by jaytek13 on 2008-02-03
The installer takes care of the dual boot options for you. There really isn't much you would have to do as far as that's concerned. It would install something that will allow you to pick whether you want to boot into windows or ubuntu. 

But there isn't a way to switch OS's without rebooting, no.

And you wouldn't have to delete any files. Ubuntu takes up very little space and it will resize the windows partition for you to make room. Some recommend doing a disk defragment inside windows before doing that, though.

---

### Post by lswest on 2008-02-03
well, if you want to install Ubuntu, you'll need a minimum of 15GB, but probably not much more than that.  About being able to boot one while logged into the other is only possible if you run Ubuntu in a virtual machine (slow, probably not the best option) (virtual machine= a virtual computer running on fake hardware and takes considerable resources).  To install ubuntu on your XP computer you can follow [this guide]("http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu")

---

### Post by sumguy231 on 2008-02-03
You will need to set up a dual boot, which is a matter of getting a separate hard drive partition for Ubuntu. If your hard drive is one big partition, you'll need to resize it. Read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

The closes thing to changing operating systems without rebooting is using a virtualization program to run one operating system as a guest inside the other.

---

### Post by rob1101 on 2008-02-03
yes you can have two OS on the same computer. Its been a while so im not really sure of the steps during the install. you should be able to follow the on screen instructions. As far as i know its impossible to switch operating systems without restarting the systems.

---

### Post by bumanie on 2008-02-03
A dual boot system works fine and has all the computer resources available to it. Your other option is try a virtualization or emulation setup. Look at vmware, virtualbox or qemu for more information. With this system, when you have a 'guest OS' running, the resources of your computer need to be shared - if you have box with high specs, it's no problem, but if you only have 512mb ram (as an example) shared between two OSes, the OSes will be very slow when in virtualization mode.

---

### Post by Nty on 2008-02-03
Ok,so Switching OS without rebooting the machine is not an option anymore.
So,lets say i have Ubuntu installed,i turn on my computer,how do i choose what OS to open?

---

### Post by jaytek13 on 2008-02-03
> **Nty said:**
> Ok,so Switching OS without rebooting the machine is not an option anymore.
So,lets say i have Ubuntu installed,i turn on my computer,how do i choose what OS to open?

You would just choose from a list. You can also configure it so that it would automatically boot up this or that OS after a certain period of time.

---

### Post by lswest on 2008-02-03
ubuntu will install a bootloader called GRUB during the installation process, which will give you a menu to choose what OS to boot (3 entries for linux, ubuntu; ubuntu failsafe; memtest; then a seperator, and 1 or 2 entries for XP, depending if you have a recovery partition or not.)

---

### Post by Nty on 2008-02-03
Ok,and the two OS's share files? I mean,if i have song called "13.mp3",it will be shown on Ubuntu And Windows?

---

### Post by lswest on 2008-02-03
you will be able to see the file in ubuntu, but it will still be on the Windows section of the drive.  (I, for one, play all my music off my vista partition, just so i don't waste space by having songs twice).  This is true for anything on the windows drive, just be careful not to delete anything important, as windows isn't there to stop you from deleting important system files.

---

### Post by ajgreeny on 2008-02-03
No, it will not show in windows if it is on the ubuntu partition, but ubuntu will see your windows files without problem, and since 7.10 will be able to write to the ntfs partition as well.  Not safely the opposite way, I'm afraid.

Your best answer would be to have a shared partition in either fat32 or ntfs format, which both OSs will be able to read and write to.  This is certainly possible and not difficult, but if you are not even slightly au-fait with linux or ubuntu at the moment, I would suggest you just try it for a while and once you are better able to understand all the implications, then consider a shared partition.

If you do want a shared partition, when you get to the partitioning part of the install chose Manual and you can then manipulate your current partition(s) easily with the gparted that ubuntu uses by default.  If you want to do that come back again and we'll help as much as possible with partition sizes and other suggested details.

---

### Post by lswest on 2008-02-03
or install something like diskinternal's Linux Reader in windows, it's what i use to browse for something if it's on my linux drive.

---

### Post by aysiu on 2008-02-03
> **jaytek13 said:**
> 
But there isn't a way to switch OS's without rebooting, no.

And you wouldn't have to delete any files. Ubuntu takes up very little space and it will resize the windows partition for you to make room. Some recommend doing a disk defragment inside windows before doing that, though. > **lswest said:**
> well, if you want to install Ubuntu, you'll need a minimum of 15GB, but probably not much more than that.  About being able to boot one while logged into the other is only possible if you run Ubuntu in a virtual machine (slow, probably not the best option) (virtual machine= a virtual computer running on fake hardware and takes considerable resources). Ubuntu does not need 15 GB. At one point, I had Ubuntu, Kubuntu, and Xubuntu all installed on the same partition, and it took up less than 4 GB.

And, if you have more than 512 MB of RAM, a virtual machine may actually be your best choice. It has several advantages--not the least of which is there being no danger of you accidentally destroying or corrupting your Windows data during partitioning (a small chance, granted; but still a chance). The main advantage in your situation is the ability to switch quickly. Since you mentioned you are not the only one in your household using the computer, it'd be kind of annoying for your other family members to have to wait until you rebooted before they could use the Windows side of things. With a virtual machine, you can just press one key to switch back to Windows instantly.

You can read here a step-by-step guide to installing a virtual Ubuntu inside Windows:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by Nty on 2008-02-03
ok,i'll go over it again-i just install the Ubuntu from the live cd,and it do the dual-booting thingy alone (if i'm wrong,correct me).
now,i bumped into a new problem-connecting to internet-how? i'm using ADSL,but you have to manually connect to the internet,and i dont get how am i suppose to do it on Ubuntu.

---

### Post by aysiu on 2008-02-03
> **Nty said:**
> ok,i'll go over it again-i just install the Ubuntu from the live cd,and it do the dual-booting thingy alone (if i'm wrong,correct me).
now,i bumped into a new problem-connecting to internet-how? i'm using ADSL,but you have to manually connect to the internet,and i dont get how am i suppose to do it on Ubuntu.
If you do decide to go with a dual-boot (not necessarily the best option, given your situation), the absolute first step you **must** take is to back up your data.

"Back up" means to do whatever you have to do so that if you accidentally overwrite or corrupt your Windows partition that you can restore your computer to exactly the same state it was before you attempted to Ubuntu-ize it.

Then, you actually have to defragment the Windows partition.

The Ubuntu live CD should then allow you to resize the Windows partition to make room for a Ubuntu partition.

The fact that you're having trouble connecting to the internet is another indicator that you should consider starting off with a virtual machine, though. Please read the link I posted earlier.

Rushing too quickly into a dual-boot can mean a lot of frustration down the road. ADSL connection troubles are just the start.

---

### Post by Nty on 2008-02-03
Virtual machine is not an option,i'm running 128 mb of RAM,and my PC cant take too much,so virtual machine is not an option.

---

### Post by aysiu on 2008-02-03
> **Nty said:**
> Virtual machine is not an option,i'm running 128 mb of RAM,and my PC cant take too much,so virtual machine is not an option.
If you have only 128 MB of RAM, then the live CD (or Desktop CD) is also not an option.

If you want Ubuntu installed, you'll have to download the Alternate CD and [burn it as a disk image](http://www.psychocats.net/ubuntu/iso), back up everything in Windows and Windows itself, defragment Windows, and finally boot the Alternate CD and [set up a dual boot](http://users.bigpond.net.au/hermanzone).

P.S. The instructions I linked to for burning as a disk image use the Desktop CD as an example, but you really need the Alternate CD. The Desktop CD will **not** work in your situation.

---

### Post by Nty on 2008-02-03
Why not? it worked great when i booted it from the CD

---

### Post by aysiu on 2008-02-03
> **Nty said:**
> Why not? it worked great when i booted it from the CD
Because you can't run the live session *and* the live session's installer successfully at the same time with only 128 MB of RAM.

The live CD alone can run, but not along with the installer.

You're certainly welcome to try, though.

---

### Post by Nty on 2008-02-03
Oh,sorry,it IS 256,i just couldn't believe that my PC can run Unreal Tournament 2004 and Microsoft Flight simulator and not installing ubuntu,so i checked the detail's page of my PC,and i saw it's 256 MB of RAM,my bad...

---

### Post by Fechter on 2008-02-03
It depends, if you have made your win files acessible only on Win, as win administartor, no. If you have rights, it's ok.

---

### Post by Fechter on 2008-02-03
OK I am typing too slow. My post is old.

---

### Post by Nty on 2008-02-03
Ok,it's probably enabled,By The Way-the ADSL thing may not be a problem with my PC,it maybe my ISP that is too narrow-minded to do something that Ubuntu will automatically detect because of the mainstream in my country.

---

