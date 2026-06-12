---
title: "Ubuntu installation should not mean that it messes up all your system!"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by icett on 2007-08-02
I was very optimistic about Ubuntu when I thought it would give me a chance to test Linux and to slowly switch over to Linux entirely. Though now technically illiterate, I hoped to get used to Linux someday becoming skilled enough to contribute to this OS because I don't like monopolies, I like competition and thus I do not like just one OS having 90% hold over the PC market. Thus I took the courage to install Ubuntu into one of my three partitioned hard drives. The other two had Windows 98 se and Windows XP Pro. I was confident that the installation would go on smoothly thus giving me a PC with Win 98, XP and Ubuntu neatly installed in it. Also I thought that if something went wrong I can count on the huge Ubuntu community and somehow I would be able to solve my problem. But I could not get any concrete help from the community when I posted a thread "Help me Please!". Being in the dark entirely, I tried to fix the problems myself trying to reinstall Windows which was corrupted by Ununtu installation and then installing Ubuntu to properly install it but and this went on several times until my system is completely messed up. In my opinion installing Ubuntu should not mean that it would render your other OSs corrupt unable to operate at all and you are stuck up with Ubuntu only and can not remove Ubuntu at all to restore the system! Also the community should be supportive and provide easy step by step help and guidance instead of just posting few lines not understandable for newbies. I request the entire community to help me restore my computer by informing me the way to uninstall all Linux related stuff from my PC, format my complete hard drive with all partitions, recreate 3 partitions and install into them Windows 98 SE, Windows XP Pro, and Ubuntu Linux. As informed earlier, I am technically unaware and would need your guidance in terms of commands and other things. I wish that I get the support of this community putting me on the Linux road to proceed ahead. So your help would be much appreciated. Best regards.:(

---

### Post by Ek0nomik on 2007-08-02
> **icett said:**
> I was very optimistic about Ubuntu when I thought it would give me a chance to test Linux and to slowly switch over to Linux entirely. Though now technically illiterate, I hoped to get used to Linux someday becoming skilled enough to contribute to this OS because I don't like monopolies, I like competition and thus I do not like just one OS having 90% hold over the PC market. Thus I took the courage to install Ubuntu into one of my three partitioned hard drives. The other two had Windows 98 se and Windows XP Pro. I was confident that the installation would go on smoothly thus giving me a PC with Win 98, XP and Ubuntu neatly installed in it. Also I thought that if something went wrong I can count on the huge Ubuntu community and somehow I would be able to solve my problem. But I could not get any concrete help from the community when I posted a thread "Help me Please!". Being in the dark entirely, I tried to fix the problems myself trying to reinstall Windows which was corrupted by Ununtu installation and then installing Ubuntu to properly install it but and this went on several times until my system is completely messed up. In my opinion installing Ubuntu should not mean that it would render your other OSs corrupt unable to operate at all and you are stuck up with Ubuntu only and can not remove Ubuntu at all to restore the system! Also the community should be supportive and provide easy step by step help and guidance instead of just posting few lines not understandable for newbies. I request the entire community to help me restore my computer by informing me the way to uninstall all Linux related stuff from my PC, format my complete hard drive with all partitions, recreate 3 partitions and install into them Windows 98 SE, Windows XP Pro, and Ubuntu Linux. As informed earlier, I am technically unaware and would need your guidance in terms of commands and other things. I wish that I get the support of this community putting me on the Linux road to proceed ahead. So your help would be much appreciated. Best regards.:(

Paragraphs make things much easier to read...

Anyways, do you have multiple hard drives or just one hard drive split into three partitions?

You state:  "format my complete hard drive with all partitions", I presume this means you have no hesitation towards data loss at this point?

---

### Post by Tyggna on 2007-08-02
No, the Ubuntu install shouldn't do that, but it does give a few warnings before it changes your harddrive.  Windows partitions can have errors in them.  Ubuntu will warn you about this too, and tell you to run a "chkdsk /f" from the windows command prompt.  If you didn't do that, then, yes, ANY reformatting of your hard drive could be very dangerous.

---

### Post by philinux on 2007-08-02
I've found the best way to have windoze and ubuntu is to have two hard drives. I got a 120gig drive given but they are so cheap to buy anyway. The advantage is that the two never meet. I've got ubuntu on my primary drive and my existing windows as the slave. Best way to install I found is to disable the windows drive one drive bios so ubuntu only sees one drive and then install from live cd. that way it does not interfer with your windows set up.

---

### Post by overdrank on 2007-08-02
Hi I can understand you frustration, but ubuntu cannot corrupt your windows os or any other for that matter. I have installed ubuntu several times with windows xp and vista. It is my opinion that you dont rely on the community but to rely on yourself to research and understand what you are trying to do before doing it. You can use the live cd and this forum to research and learn linux before you install. Now with that being said state your problem briefly and as best you can and I am sure this community will help as best they can. :)

---

### Post by icett on 2007-08-02
> **Ek0nomik said:**
> Paragraphs make things much easier to read...

Anyways, do you have multiple hard drives or just one hard drive split into three partitions?

You state:  "format my complete hard drive with all partitions", I presume this means you have no hesitation towards data loss at this point?





Thanks all for the support. Ek0nomik, yes I have one hard drive and if it is easier I would like to save my data but if its too complicated I would wish to format everything and reinstall again. Because I am too stressed and tired now. 



Also I would think of adding another hard drive sometime in future but I think I should have a second cup of Ubuntu first. 


I hope you guys would help me.:)

---

### Post by Ek0nomik on 2007-08-02
> **icett said:**
> Thanks all for the support. Ek0nomik, yes I have one hard drive and if it is easier I would like to save my data but if its too complicated I would wish to format everything and reinstall again. Because I am too stressed and tired now. 



Also I would think of adding another hard drive sometime in future but I think I should have a second cup of Ubuntu first. 


I hope you guys would help me.:)

Well, if you want to save all your data, your best bet would be to get it *off* this hard drive.  Do you have a USB external hard drive or USB thumbstick?  If not, it's going to be hard to keep all your data if you want to reformat the whole hard drive.  You could also burn your data to a CD or DVD to keep it for when you get this situation all sorted out.

There is one solution if you don't have any USB devices or CDs/DVDs.  You would have to create a fourth partition, and throw all your data onto that partition.  Then, once you got Windows 98 and XP installed, you could throw the data onto those partitions, and then delete this "backup" (fourth) partition you made and give it to Ubuntu.  By the sounds of it, you don't want to do that, but it is an option.  If you do decide to do it, reply and myself or someone else will help.

Now if you want to get Windows 98 and XP and Ubuntu running, your best bet would be to start by installing the Microsoft products first.  It sounds like you know how to partition your hard drive since you had XP and 98 running previously, so you will want to do the exact same thing.  Follow Tyggna's advice for partitioning.  :)

Once you get that far, reply and someone will guide you through the Ubuntu work.  It's really easy.  :)  (Keep in mind Ubuntu requires about 2.5GB for a fresh install, and you will want to give it more for program installation and just regular use.)

[http://ubuntuguide.org/](http://ubuntuguide.org/)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by wolfen69 on 2007-08-02
if you want to triple boot, first make 3 partitions using gparted or other software. then install in this order: win98/xp/ubuntu.

---

### Post by Tyggna on 2007-08-02
Step by step, how I would do it:
**Note, this will take a long time--no matter how fast your computer**

First off, Windows is ego-centric.  It would like to be on your harddrive first.  I would install older versions first, then the newer ones.  

Your best starting point would be a live CD of Ubuntu, just to set the stage.  In Ubuntu 7.07 on the live CD click on the "system" at the top of the screen, select the administration, and click on GNOME partition editor.

***Note:  You are about to wipe your harddrive and lose any data on it***

Delete all of the exsisting partitions.  Simply click on the partition and press the delete key (or right click and select delete).   Click on apply and wait for it to finish.

Once GNOME partition editor is showing all gray, make your first partition at the beginning of the drive.  As you are running Windows 98, you'll want to partition this in FAT32.  Select the size, and then apply.  Once that's safely made, make another NTFS partition right after it.  When you're done with that, make an ext3 partition and a linux-swap partition in any order you want to.  (You don't need to make the swap partition more than 1000 megabytes).  

Once all these partitions are put on your hard drive, shutdown the live CD and go through the windows 98 install.  Put 98 on your FAT32 partition.  When 98 is up and running, go to "run" on your start menu, and type cmd.  When the black command prompt comes up, type either

chkdsk /r (preferred the first time you run this command, as this will fix any damaged sectors on your harddrive, but take a long time)

OR

chkdsk /f (the minimum requirement before a new install.

It might say that it can't preform a chkdsk at this time and if you'd like to do it on the next restart.  Say yes, and then reboot.  Let it run, and when it's done, reboot your computer twice before doing anything else.

After you've gone through two solid reboots, repeat this process for XP.  Same commands, same procedure.  XP should take control of your MBR (master boot record, it's used to tell the computer where to find your OS), and allow you to dual boot.  As you don't really need to dual boot using the windows uitility, I would NOT select any dual boot options that windows gives you, as this can screw up the linux dual boot utility (which is, sad to say, much better than windows'). 

Do your best to not let XP see 98.  When XP is done installing, run the command prompt again. ("Run" then type cmd)

From the command prompt:
Switch to the drive that XP is installed on (usually C:\, you just have to type CD [DRIVE LETTER]:\)
chkdsk /f

It will ask you if it can do this on reboot.  Say yes, then reboot.
Let it run, then reboot twice.

Now you're ready to install Linux.

Linux should see the partitions you made for it when you install.  From a feisty fawn live CD, select your region options and all that jazz.  When you get to the partitioning area, select your ext3 partition and right click.  Click on "edit" and then in the mount point option, type a single /

This tells Linux that you want it to run from that drive.  Linux should then be like, Okay!  Great, I know where to go, and I see everything else that's on this drive.

When the partition is made, it should ask you if you want to install GRUB.  say yes.  Grub should see XP and 98.  If you have any problems, then post again asking "how do I dual boot two windows os's with Grub," as I'm sure someone knows.

Once linux is installed, it'll be set as your default.  When you boot up, you'll see the grub menu, which will list two Ubuntus to start, and then have an "Other OS" section that should show both windows.

I hope that was helpful.

---

### Post by bernied on 2007-08-02
Reinstalling everything is madness and will take you days of sitting watching windows progress bars tick across your screen, and clicking your mouse once every two hours. 

You could spend that time learning about what has actually gone wrong here, and fixing it. Your two windows installs are probably just fine, and waiting for you to boot them. Unless you (not ubuntu) wiped them when you installed ubuntu.

And 'Help me please!' is a really poor title for a help request.

try-
learn, learn, learn

not-
moan, moan moan

---

### Post by icett on 2007-08-02
> **Ek0nomik said:**
> Well, if you want to save all your data, your best bet would be to get it *off* this hard drive.  Do you have a USB external hard drive or USB thumbstick?  If not, it's going to be hard to keep all your data if you want to reformat the whole hard drive.  You could also burn your data to a CD or DVD to keep it for when you get this situation all sorted out.

There is one solution if you don't have any USB devices or CDs/DVDs.  You would have to create a fourth partition, and throw all your data onto that partition.  Then, once you got Windows 98 and XP installed, you could throw the data onto those partitions, and then delete this "backup" (fourth) partition you made and give it to Ubuntu.  By the sounds of it, you don't want to do that, but it is an option.  If you do decide to do it, reply and myself or someone else will help.

Now if you want to get Windows 98 and XP and Ubuntu running, your best bet would be to start by installing the Microsoft products first.  It sounds like you know how to partition your hard drive since you had XP and 98 running previously, so you will want to do the exact same thing.  Follow Tyggna's advice for partitioning.  :)

Once you get that far, reply and someone will guide you through the Ubuntu work.  It's really easy.  :)  (Keep in mind Ubuntu requires about 2.5GB for a fresh install, and you will want to give it more for program installation and just regular use.)

[http://ubuntuguide.org/](http://ubuntuguide.org/)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)





Ek0nomik,


The data I have on that PC is not so important now that I have all the same data on the computer with which I am in contact with you. Also before installing Ubuntu, I wrote down all the important information in a book so formatting would be a good option for me. The PC has games only which I would install later on. I tried to install Windows 98 and XP but that failed. After so many installs there are too many ubuntu shortcuts in Grub. And I can only log into ubuntu. There are many partitions created by Ubuntu. Also the three partitions which were earlier on my pc were created by a friend of mine and is out of country now. So for me to install Win 98, XP and Ubuntu, first I have to format everything on the hard drive including linux and its created partitions, thereafter recreate three equal partitions, install win98, xp and ubuntu again this time with prior guidance from my fellow ubuntu community. I hope I would get the necessary help. 



Wolfen69,


I had fat 32 partitions. Is gparted more stable or suitable for Linux? Please let me know.

---

### Post by Tyggna on 2007-08-02
> 
try-
learn, learn, learn

not-
moan, moan moan


He's right, but for us, who know computers and Linux, we should be saying:

Help, help, help


not:

Condemn, Criticize, Mock

And we never have any reason to come off with an attitude like the later--even if we do mean well.

---

### Post by Ek0nomik on 2007-08-02
> **icett said:**
> Ek0nomik,


The data I have on that PC is not so important now that I have all the same data on the computer with which I am in contact with you. Also before installing Ubuntu, I wrote down all the important information in a book so formatting would be a good option for me. The PC has games only which I would install later on. I tried to install Windows 98 and XP but that failed. After so many installs there are too many ubuntu shortcuts in Grub. And I can only log into ubuntu. There are many partitions created by Ubuntu. Also the three partitions which were earlier on my pc were created by a friend of mine and is out of country now. So for me to install Win 98, XP and Ubuntu, first I have to format everything on the hard drive including linux and its created partitions, thereafter recreate three equal partitions, install win98, xp and ubuntu again this time with prior guidance from my fellow ubuntu community. I hope I would get the necessary help. 



Wolfen69,


I had fat 32 partitions. Is gparted more stable or suitable for Linux? Please let me know.

GParted is on the Ubuntu Live CD.  You can run the Live CD (which, by the way, won't change **anything** on your hard drive(s) unless you click the "Install" button the Desktop.  The Live CD *won't* screw anything up, so don't be worried about using it) and run GParted Partition Editor and format your hard drive to the needed filesystems and size(s).

---

### Post by icett on 2007-08-02
> **Tyggna said:**
> Step by step, how I would do it:
**Note, this will take a long time--no matter how fast your computer**

First off, Windows is ego-centric.  It would like to be on your harddrive first.  I would install older versions first, then the newer ones.  

Your best starting point would be a live CD of Ubuntu, just to set the stage.  In Ubuntu 7.07 on the live CD click on the "system" at the top of the screen, select the administration, and click on GNOME partition editor.

***Note:  You are about to wipe your harddrive and lose any data on it***

Delete all of the exsisting partitions.  Simply click on the partition and press the delete key (or right click and select delete).   Click on apply and wait for it to finish.

Once GNOME partition editor is showing all gray, make your first partition at the beginning of the drive.  As you are running Windows 98, you'll want to partition this in FAT32.  Select the size, and then apply.  Once that's safely made, make another NTFS partition right after it.  When you're done with that, make an ext3 partition and a linux-swap partition in any order you want to.  (You don't need to make the swap partition more than 1000 megabytes).  

Once all these partitions are put on your hard drive, shutdown the live CD and go through the windows 98 install.  Put 98 on your FAT32 partition.  When 98 is up and running, go to "run" on your start menu, and type cmd.  When the black command prompt comes up, type either

chkdsk /r (preferred the first time you run this command, as this will fix any damaged sectors on your harddrive, but take a long time)

OR

chkdsk /f (the minimum requirement before a new install.

It might say that it can't preform a chkdsk at this time and if you'd like to do it on the next restart.  Say yes, and then reboot.  Let it run, and when it's done, reboot your computer twice before doing anything else.

After you've gone through two solid reboots, repeat this process for XP.  Same commands, same procedure.  XP should take control of your MBR (master boot record, it's used to tell the computer where to find your OS), and allow you to dual boot.  As you don't really need to dual boot using the windows uitility, I would NOT select any dual boot options that windows gives you, as this can screw up the linux dual boot utility (which is, sad to say, much better than windows'). 

Do your best to not let XP see 98.  When XP is done installing, run the command prompt again. ("Run" then type cmd)

From the command prompt:
Switch to the drive that XP is installed on (usually C:\, you just have to type CD [DRIVE LETTER]:\)
chkdsk /f

It will ask you if it can do this on reboot.  Say yes, then reboot.
Let it run, then reboot twice.

Now you're ready to install Linux.

Linux should see the partitions you made for it when you install.  From a feisty fawn live CD, select your region options and all that jazz.  When you get to the partitioning area, select your ext3 partition and right click.  Click on "edit" and then in the mount point option, type a single /

This tells Linux that you want it to run from that drive.  Linux should then be like, Okay!  Great, I know where to go, and I see everything else that's on this drive.

When the partition is made, it should ask you if you want to install GRUB.  say yes.  Grub should see XP and 98.  If you have any problems, then post again asking "how do I dual boot two windows os's with Grub," as I'm sure someone knows.

Once linux is installed, it'll be set as your default.  When you boot up, you'll see the grub menu, which will list two Ubuntus to start, and then have an "Other OS" section that should show both windows.

I hope that was helpful.




Tyggna,



Great step by step guide from you. Really I am very grateful to you for giving so much attention and time for my problem. I just saw your post as this thread went on to the next page and I could not view it before. Now I am going to do whatever you told me. I hope that I would be successful. Really it is because of people like you that humanity is still present on this planet!:KS

---

### Post by icett on 2007-08-03
I have finally managed to create two fat 32 partitions for both the windows and installed them successfully. But for the two partitions I have created for Linux, I am not able to format them even with GNOME Partition Editor. With my live CD still in the CD Rom still there are two files I can see:


1- Filesystem

2-Lost+Found (Because of this I can not create partition for Linux.)


Please let me know how I can remove all the Linux data from the two Linux partitions. Are there some hidden files also? I wish to completely format them before I install Ubuntu again. Also I would like to scan my two partitions where I installed windows to see if there remains any hidden file or something relating to Linux. Please inform me how to. Thanks for your guidance before and I remain thankful to you. Best regards!:)

---

