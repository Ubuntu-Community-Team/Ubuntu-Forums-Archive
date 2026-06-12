---
title: "Installing Windows"
date: 2011-09-10
forum: Any Other OS
---

### Post by SoloDolo on 2011-09-10
I'm currently running ubuntu 11.04. When installing it, I was dumb enough not to create another partition for it, so I erased windows and installed ubuntu over it. I really would like windows back, so can anybody tech me how to go back to factory settings?

---

### Post by CharlesA on 2011-09-10
Try to boot off your recovery partition (if it still exists)

---

### Post by philinux on 2011-09-10
> **SoloDolo said:**
> I'm currently running ubuntu 11.04. When installing it, I was dumb enough not to create another partition for it, so I erased windows and installed ubuntu over it. I really would like windows back, so can anybody tech me how to go back to factory settings?

Depends if there's a recovery partition still intact or if you have the windows install disks. However run this command and paste back the result. Use copy and then paste into the terminal.

```
sudo fdisk -l
```

---

### Post by haqking on 2011-09-10
> **SoloDolo said:**
> I'm currently running ubuntu 11.04. When installing it, I was dumb enough not to create another partition for it, so I erased windows and installed ubuntu over it. I really would like windows back, so can anybody tech me how to go back to factory settings?


What is your machine model ?

It can often be done with a key press on boot to access a given hidden partition for restore or you will need the restore disks, either supplied or that you made with an often buitl in restore disk application.

---

### Post by SoloDolo on 2011-09-10
Well now I have a bigger problem. When I try to boot my machine, grub doesn't show and I get a message saying "No boot signature in partition".  I have a Dell Inspiron 1525

---

### Post by haqking on 2011-09-10
> **SoloDolo said:**
> Well now I have a bigger problem. When I try to boot my machine, grub doesn't show and I get a message saying "No boot signature in partition".  I have a Dell Inspiron 1525

If not deleted the hidden partition then this should work.

    Turn on the computer.

2   As the computer starts, press <F8> on the keyboard until the Advanced Boot Options menu appears on the screen.
      
3    Press the <Down Arrow> on the keyboard to select Repair Your  Computer on the Advanced Boot Options menu, and then press  <Enter>.

4    Specify the language settings that you want, and then click Next.

5    Log in as a user who has administrative credentials, and then click OK.

6    Click Dell Factory Image Restore.

7    In the Dell Factory Image Restore window, click Next.

8    Click to select the Yes, reformat hard drive and restore system software to factory condition check box.

9    Click Next. 
The computer is restored to the default factory configuration.

10    When the restore operation is completed, click Finish to restart the computer.

NOTE: this will only work if the hidden restore partition still exists, if it doesnt then this wont work.  You would need the restors discs or an original Windows disc to boot from

Also see here at [DELL Factory Restore]("http://search.dell.com/results.aspx?c=us&l=en&s=gen&cat=cmu&k=restore+to+factory+settings+1525&rpp=12&p=1&rf=all&nk=f&ira=False&%7Esrd=False&ipsys=False&advsrch=False&%7Eck=tab") where you might find more applicable instructions.

Cheers

---

### Post by SoloDolo on 2011-09-10
F8 doesn't do anything :(

---

### Post by SoloDolo on 2011-09-15
When I installed linux a while back, I deleted my windows partition. I really want it back now, so how do I do it? I tried booting from the disk, but it won't work.

Any help?

---

### Post by magical2hobo on 2011-09-15
How did it not work? Did your computer not boot from the disk or did the install fail? Also do you want to keep your linux partition and run a dual-boot or completely wipe it and run a Windows only setup?

---

### Post by SoloDolo on 2011-09-15
> **magical2hobo said:**
> How did it not work? Did your computer not boot from the disk or did the install fail? Also do you want to keep your linux partition and run a dual-boot or completely wipe it and run a Windows only setup?

My computer didn't start the set-up. And yes I would like to keep my linux partition, but if it causes too much trouble, I'd rather just wipe it and re-install later.

---

### Post by magical2hobo on 2011-09-15
it could just be that you have to change your bios to boot from the CD drive first. if you want to want to save your whole system you could shrink your partition and clone it with clonezilla, or the easier route would be to copy your /home directory onto a external HD and do another install of linux, the system would have to be reconfigured but all your data would be saved

---

### Post by raja.genupula on 2011-09-15
actually the simplest i know way for dual booting is installing windows and then ubuntu 
if you install windows after ubuntu then your grub loader will be override by windows boot loader,

so you must need this 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

all the best

---

### Post by Mark Phelps on 2011-09-16
> **SoloDolo said:**
> When I installed linux a while back, I deleted my windows partition. I really want it back now, so how do I do it? I tried booting from the disk, but it won't work.

Any help?

Which version of Windows is it?  IF it's Win7, is the disk a CD or DVD? 

If it's a CD, and it came with the PC, it's probably just a Recovery disk -- and in that case, all it will do is erase the contents of your hard drive and reinstall Win7.  And, if you erased the Recovery partition, it won't be able to do that because the restore image it needs was stored in that partition.

If it's a DVD, what kind of problem are you experiencing?  Saying "it won't work" is not very helpful.

---

### Post by SoloDolo on 2011-09-24
I have a dell thats running ubuntu and I want to re-install windows on it. How should I go about doing this?

---

### Post by dino99 on 2011-09-24
the easiest way is to install virtualbox on your ubuntu, then install winbloz inside virtualbox.

or more easier: dont use it at all :) as ubuntu+wine (winehq) run quite everything smootly

---

### Post by Mark Phelps on 2011-09-24
> **SoloDolo said:**
> I have a dell thats running ubuntu and I want to re-install windows on it. How should I go about doing this?

If the Dell came with Windows on it, and what you want is THAT working again, and you did NOT remove the Recovery partition, you should be able to boot and press a special key (maybe F11) and have it do a full restore.

If that isn't possible, then you should boot using the Ubuntu CD, choose Try Ubuntu mode, and then using either the Disk Utility or the Gnome Partition Editor, remove all the partitions on the drive.  Then, boot with your Windows install CD or DVD and install it.

As to the claim that Wine runs "everything" -- this is about the most ridiculous thing I've heard in a long time!  Wine only runs SOME things, and quite a few things run poorly or not at all.

---

### Post by Elfy on 2011-09-24
Thread moved to Other OS/Distro Talk.

---

### Post by varunendra on 2011-09-25
> **SoloDolo said:**
> I have a dell thats running ubuntu and I want to re-install windows on it. How should I go about doing this?
I hope you mean "Dual boot" with Windows. If so, then you can:

[LIST]
[*]either proceed as what Mark suggested > then reinstall Ubuntu in a new partition (simpler but lengthy way, plus you will loose everything on current Ubuntu installation), or,
[/LIST]

[LIST]
[*]Just shrink/delete '**a few**' partitions (leaving the one on which Ubuntu itself is installed) to create space for a new partition for Windows (primary, if it is Win7 or Vista) > Install Windows on that partition > then just restore grub2 to let it boot both the existing Ubuntu and newly installed Windows ([simplest how to for restoring Grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2"))
[/LIST]
If you need help doing that, we'll be glad to.

---

### Post by Bucky Ball on 2011-09-25
As mentioned: Boot from LiveCD, Try Ubuntu, Gparted, delete all partitions, as you were. That simple.

---

### Post by haqking on 2011-09-25
> **SoloDolo said:**
> I have a dell thats running ubuntu and I want to re-install windows on it. How should I go about doing this?

Use the windows disc to boot to.

If you have a restore partition which alot of Dell do then when you see the Dell Logo upon boot press ctrl +f11 or press f8 and you should get a menu to restore to factory defaults.

Unless you mean you now want to dual boot with Ubuntu and Windows ?

---

### Post by coffeecat on 2011-09-25
@SoloDolo, your latest thread (OP now at #14 in this thread) was the third you had started in two weeks about the same issue. Others had given you relevant advice in the two earlier threads which you didn't seem to respond to. By starting a new thread without the information you provided in the earlier threads, you are causing unnecessary work for people trying to help you. I have merged all three threads and renamed it to the title of your latest.

Please do not start multiple threads on the same problem - it dilutes community effort. If you need to leave a thread for a week or so, you can always bump it to get it going again. That is OK.

---

### Post by varunendra on 2011-09-25
> **coffeecat said:**
> I have merged all three threads and renamed it to the title of your latest.
And I was surprised to see where all those previous posts (before dino) came from. [s]Am[/s] Was I so sleepy that i missed them ?? :D

[B]
_EDIT_:
[/B]> **haqking said:**
> They came because the threads were merged
Yeah, I know that. I meant that it was my 'first impression' on the second visit until I read coffeecat's post ;). Perhaps I should have used 'was' instead of 'Am'.. Alright .. did it!

---

### Post by haqking on 2011-09-25
> **varunendra said:**
> And I was surprised to see where all those previous posts (before dino) came from. Am I so sleepy that i missed them ?? :D

They came because the threads were merged

---

