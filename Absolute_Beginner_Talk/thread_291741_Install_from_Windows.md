---
title: "Install from Windows"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by jabzwnein on 2006-11-02
I'm trying to install Ubuntu from windows.  I followed all the instructions here: [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
but when I get to the screen where I can choose to install Ubuntu or run Windows XP, choosing "install Ubuntu" leads the computer to say that the file "<windows root>\system32\hal.dll" is missing.  All the info I've read on how to fix this problem assumes you reinstall Windows or something, and just don't try to dual boot the system.  How can I fix this problem?

---

### Post by goatflyer on 2006-11-02
You can download a copy of hal.dll here:

[http://www.dll-files.com/dllindex/dll-files.shtml?hal](http://www.dll-files.com/dllindex/dll-files.shtml?hal)


You have to unzip it into your %WINDOWS%\system32 directory.

---

### Post by Sef on 2006-11-02
sounds like GRUB did not install or install correctly.  If you have a Ubuntu CD, then read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by jabzwnein on 2006-11-03
Thanks for your help, but adding the hal.dll file to windows made my computer, uh, not work anymore.  I think I have to reinstall windows now.  Any other suggestions?

---

### Post by Bartender on 2006-11-03
I don't know if [this]("http://www.kellys-korner-xp.com/xp_haldll_missing.htm") helps you any, but at least talks about what happened.

---

### Post by podunk on 2006-11-03
I've just read all your post. You've been on an epic journey here! I admire your perseverance, I bet your boss at work loves you. :)

I got 4 months of Linux under my belt, and I don't think I would try installing from the hard drive. The how to looks entirely to advanced for my skill level at this point.

Can I offer a suggestion? There is something basically wrong here. Either you have a hardware problem or for some reason or another the Ubuntu you have chosen simply won't work with some piece of your hardware.

You say you have a Dell -which kind? Some of the older Dells came with a boot virus/write protection feature that prevents acessing the MBR. You turned this off in BIOS. 

Will your Windows set up disk /Dell restore disks boot up? If no - open the case with the power off and wiggle stuff. Lose cables, sticks of RAM, all the PCI cards nice and tight? Will it boot your Windows set up disk? If not borrow a CD and cable and see if that will work.

If it *will* boot your Windows set up disk - did you verify the checksum of the Ubuntu ISO? There is a check utility also on the Ubuntu CD - did you run that? I know the CD will boot on another machine - but if there is some small flaw that will allow another machine to boot but prevent this one.

There is a Memtest 86 utility on the CD - I would suggest running that.

If all the above checks out I would suggest either getting in touch with Dell customer support to see if they have any suggestions or try a different flavor of Linux. Perhaps one of the more "commercial" versions like Red Hat or Suse would work for you. 

I love K/Ubuntu - but in the end Linux is Linux.

---

### Post by sktfeelsdapper on 2006-11-03
I use win2lin or whatever that program is that installs it for you and it worked fine (albiet the netboot took forever, the us site didn't work for me?) are you trying the easy way or the manual blood sweat and tears way?

---

### Post by jabzwnein on 2006-11-03
Thanks for all your help!  After trying to reinstall Windows and just coming up with so many problems (I spent a half hour trying to get the screen resolution right, a driver was missing or something), I ended up going to Barnes and Noble and getting "Moving to Ubuntu Linux" by Marcel Gagne.  Best thing I've ever done.  Worked perfectly, and I'm now Windows-free!

Thanks again!!!

---

### Post by livinginx on 2006-11-04
How much did the book cost and is it more then just the install process?

---

### Post by jabzwnein on 2006-11-04
The book cost $35 and came with an install DVD.  I chose it because it looked very user-friendly for someone like me who knows absolutely nothing about linux.  It has chapters on music and video and burning CDs and openoffice and everything, so I think it was a good investment.  There was another book, the official ubuntu book, for the same price.  Also, there was a huge book on everything possible in Ubuntu, but it was more than I needed and it cost $50.  I think the one I got is good.

---

