---
title: "I need to format my hard-drive"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by jazmo14 on 2008-03-15
I can't seem to find out how to format my hard drive anywhere, for Ubuntu 7.10. So if anyone could please tell me how to format my hard drive on Ubuntu 7.10. Any help is greatly appreciated.

This may be confusing as it may be in the wrong section, I don't need help installing Ubuntu, I need help uninstalling it from my hard drive.

---

### Post by taurus on 2008-03-15
Is that an extra harddrive that you want to format?  You can try using gparted in System -> Administration to do that.  And if you don't have one, install it with

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

---

### Post by mikewhatever on 2008-03-15
Check out this page [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm). If there is another OS, restore its bootloader first.

---

### Post by TeoBigusGeekus on 2008-03-15
Provided you have a dual boot system (window$-ubuntu):

You are gonna need the window$ installation cd. Boot with it and enter recovery mode. In the console type
```
fixmbr
```
This will get rid of the grub loader.

Next, boot up with the Ubuntu live cd. Once in, load gnome partition editor (System->Administration->Partition Editor). Let it recognise your volumes, choose the Ubuntu one, format it and then choose the window$ one and resize it.

---

### Post by Funky91 on 2008-03-15
is the problem that you want to get rid of ubuntu or that you want to format another hard disk IN ubuntu?

---

### Post by vikasmk on 2008-03-15
try gparted, its there in the kubuntu live cd. 
 else install gparted ( a little ironic , that you have to install something to remove ubuntu):popcorn:

---

### Post by TeoBigusGeekus on 2008-03-15
He must boot up with a live cd in order to use gparted on his ubuntu volume. Partition editor can't do anything unless the volume is unmounted -impossible if the os is already running.

---

### Post by jazmo14 on 2008-03-15
@taurus that does'nt work because whenever I run a command in the terminal, if the command has to connect to a website, then it can't. I don't know why, but ti just does'nt connect to the internet, it just stops. Even though I can use FireFox fine with the internet.

@mikewhatever I've tryed what you said but Gparted does'nt do anything for me, I have written it to a disc, and try to run it on my ubuntu machine, and it just starts up the OS as normal.

@TeoBigusGeekus I don't want to dual-boot, I'm trying to get rid of Ubuntu

@Funky91 Yes, I want to get rid of Ubuntu, not format another HD in Ubuntu.

@vikasmk Tryed Gparted already :( Was'nt much help.

Thanks for your responses guys, dunno if it's just me being stupid, but I can't seem to get ubuntu off my  machine.

---

### Post by sandysandy on 2008-03-15
> @mikewhatever I've tryed what you said but Gparted does'nt do anything for me, I have written it to a disc, and try to run it on my ubuntu machine, and it just starts up the OS as normal. 

u will have to change the booting order in BIOS to CD-ROM followed by hard disk.

that way the machine will boot into gparted CD and not ur GRUB /OS.

regards

---

### Post by TeoBigusGeekus on 2008-03-15
Ok, let's take it slow.
Is Ubuntu the only OS on your pc?

---

### Post by jazmo14 on 2008-03-15
> **TeoBigusGeekus said:**
> Ok, let's take it slow.
Is Ubuntu the only OS on your pc?

Yes, it is.

---

### Post by TeoBigusGeekus on 2008-03-15
After getting rid of ubuntu, what os do you want to install?

---

### Post by sandysandy on 2008-03-15
> **jazmo14 said:**
> Yes, it is.

its simple then

as i explained in earlier post

u will have to change the booting order in BIOS to CD-ROM (first) followed by hard disk.

that way the machine will boot into gparted CD and not ur GRUB /OS.

after u boot into gparted u can format ur hard drive with no problem.

regards

---

### Post by jazmo14 on 2008-03-15
> **TeoBigusGeekus said:**
> After getting rid of ubuntu, what os do you want to install?

Windows Vista Home Basic 32-Bit

---

### Post by forrestcupp on 2008-03-15
> **jazmo14 said:**
> Windows Vista Home Basic 32-Bit

If you just try to install Vista with the CD, it's installer should format the drive for you and set up it's boot loader.  But you are going to have to change your BIOS settings to boot to CD 1st.

---

### Post by jazmo14 on 2008-03-15
> **sandysandy said:**
> its simple then

as i explained in earlier post

u will have to change the booting order in BIOS to CD-ROM (first) followed by hard disk.

that way the machine will boot into gparted CD and not ur GRUB /OS.

after u boot into gparted u can format ur hard drive with no problem.

regards

I've booted into the Gparted disk now, but have another problem. My Screen says "Cannot Display This Video Mode" and nothing is happening...

---

### Post by TeoBigusGeekus on 2008-03-15
Then just throw in your Vista dvd, change boot sequence in bios, as sandysandy explained, and install Vista!!!

---

### Post by jazmo14 on 2008-03-15
> **forrestcupp said:**
> If you just try to install Vista with the CD, it's installer should format the drive for you and set up it's boot loader.  But you are going to have to change your BIOS settings to boot to CD 1st.

It can't though, it gives me an error when I try that. I believe the error is caused because the current hard drive is in ext3 format and not NTFS, so the windows disk can't format it.

---

### Post by TeoBigusGeekus on 2008-03-15
Share the error with us.

---

### Post by sandysandy on 2008-03-15
here are some links to dual booting vista and ubuntu

[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

---

### Post by jazmo14 on 2008-03-15
> **TeoBigusGeekus said:**
> Share the error with us.

"Failed to format the selected partition [Error:0x80004005]"

The error above is the one I get when trying to format my hard drive from the Windows Vista Installer.

---

### Post by sandysandy on 2008-03-15
here is  a link to gparted tutorial

[http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted)

regards

---

### Post by forrestcupp on 2008-03-15
> **jazmo14 said:**
> I've booted into the Gparted disk now, but have another problem. My Screen says "Cannot Display This Video Mode" and nothing is happening...

When you get to the boot menu for GParted LiveCD, choose the force vesa option.  That should get you there.

---

### Post by TeoBigusGeekus on 2008-03-15
[http://www.vistax64.com/vista-installation-setup/9419-failed-format-selected-partition-error-0x80004005.html]("http://www.vistax64.com/vista-installation-setup/9419-failed-format-selected-partition-error-0x80004005.html")
[http://forums.techarena.in/showthread.php?t=842081]("http://forums.techarena.in/showthread.php?t=842081")
[http://forum.soft32.com/win4/install-Vista-RC1-5600-Error-code-0x80004005-ftopict157053.html]("http://forum.soft32.com/win4/install-Vista-RC1-5600-Error-code-0x80004005-ftopict157053.html")
[http://thevistaforums.com/lofiversion/index.php/t25835.html]("http://thevistaforums.com/lofiversion/index.php/t25835.html")

---

### Post by jazmo14 on 2008-03-15
> **forrestcupp said:**
> When you get to the boot menu for GParted LiveCD, choose the force vesa option.  That should get you there.

That seemed to do the trick, now installing Windows Vista.

Thanks for all your other help guys :)

---

### Post by forrestcupp on 2008-03-15
Sorry you didn't like Ubuntu.  If you ever want to try it out again in the future, just dual boot with Vista, so you'll have a choice.

---

### Post by ik ben Slade on 2008-03-24
> **jazmo14 said:**
> "Failed to format the selected partition [Error:0x80004005]"

The error above is the one I get when trying to format my hard drive from the Windows Vista Installer.



Well, I had the same issue. The Vista install listed my hard drive. I have a 230gig drive in my laptop. It had 2 partitions listed. 1 partition was 224.2 gig (approx) and the other was 5.8gig. So i clicked on the 5.8gig partition and clicked 'delete', then clicked on the 224.2gig partition and also clicked 'delete'. The I clicked 'New'. Then I just clicked 'Next' and the Vista installation started.

This was on a HP Pavilion dv6000 laptop which has a SATA hard drive.

Hope this helps!

---

### Post by mrfraser89 on 2008-03-24
Definitely come back and try dualboot sometime in the future :(

Ubuntu is only getting better and better as time goes by!

---

### Post by d3vlabs on 2008-07-19
I'd loved to dual boot vista with ubuntu. but i currently in the same situation as the guy who started this thread. How can I dual boot? I currently have Ubuntu installed and WIndows Vista cd ready.

---

### Post by bigonegotaway on 2008-07-22
Here is where you need to go for help:


[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

---

