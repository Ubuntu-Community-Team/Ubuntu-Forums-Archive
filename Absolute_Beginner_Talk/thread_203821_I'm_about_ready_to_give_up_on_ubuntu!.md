---
title: "I'm about ready to give up on ubuntu!"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Ed B on 2006-06-26
I have downloaded various ubuntu i386 iso images. I have been able to run the 'live' cds and am impressed with what I see. I have tried to install ubuntu (twice), kubuntu (twice), ubuntu alternate (once - so far), but have never been able to boot an installed OS.

I am always left at the 'grub' prompt on the command line interface with not a clue about how to get past it. I have always used LILO and dual booted with it.

I have learned that pressing 'tab' at the grub prompt brings up all the acceptable entries for the first word - once I type one of those words pressing tab brings up entries that are acceptable as the second word/string.

I have searched this forum and have read posts until my eyes have almost crossed and have yet to find anything that I have been able to use - not saying it is useless - just that I can't use it. I have read some of the 'sticky' messages at the head of this thread but haven't profited much from them. Probably because of my limited knowledge and not because they are not well written or any such thing (kind of like giving a kindergarten student a book on Quantum Physics) it just hasn't been what I need.

I have found many others who seem to have had the same problem. When I find one of these threads - I begin reading with high hopes of finding an answer that I can use. I found one such thread in which the instruction was given that was supposed to get to a gui - so I thought 'finally here is the answer!' So I logged off, switched HD's and booted to the grub prompt and entered 'start x', 'start-x', 'start X', and then 'start-X' - all produced an error message and put up a fresh 'grub >' prompt (and I suspect that, somewhere in the bowels of this computer, an uproar of laughter arose mocking me and my very evident ignorance) - but I digress. This happened **before** I learned about the tab thing so I didn't yet know that 'start' was not an acceptable first word to a grub prompt.

I realize that I have left out information concerning my computer - but I'm not having any hardware compatibility problems, I just need some instruction in how to boot up from the grub prompt. I hasten to add that the instruction needs to be at the primary level or lower. Up to now, the instructions I have found presume a certain level of familiarity with Linux/Unix which I lack.

If and when I have learned to boot from a grub prompt I will try to use that knowledge by writing something to help others who need what I haven't been able to find. :) 

Best regards,  Ed B

---

### Post by bobby19 on 2006-06-26
It seems like you might have a video card issue. Try, at the command prompt, typing:
sudo dpkg-reconfigure xserver-xorg

this will bring up the xserver configuration tool. When the tool asks you the type of chipset select vesa. Then if you don't know the answers to the other questions just press enter to all of them. After that reboot and you should be greeted with the gdm login screen and you'll be able to use ubuntu to your heart's content. 

I had the same exact issue and this seemed to work for me. Try it and post back what happened. 
 Good Luck!

---

### Post by rai4shu2 on 2006-06-26
How many systems are you trying to run there?

---

### Post by falcon15500 on 2006-06-26
Sounds like GRUB is not finding it's later stages.  It's not even getting to the point of reading your menu.lst file.  How is your setup installed?  Are you dual booting?  How many HDD's have you got?  What OS is installed where?

falc

---

### Post by Ed B on 2006-06-27
Thank you for your replies - I appreciate your interest in helping me.

**bobby19**
I'll try your suggestion tonight and will post the result.

**rai4shu2**
   *"How many systems are you trying to run there?"*
On that particular HDD I have two - Win95 and hopefully Kubuntu 6.06.

**falcon15500**
I think you are right about GRUB not finding the latter stages, and I've never seen a menu displayed.
I am uncertain about where I put the boot files, I know where I meant to install them but may have put them elsewhere.
I plan to delete all the current partitions and do another install - I'll make certain of the location then.
I actually have five HDD's in all, but I have had only one connected when trying to install Ubuntu - with Win95 on (hd0.0) and Ubuntu on (hd0,1) and I do plan on dual booting.

**To all:**
Things are looking extremely more promising than when I began this thread - I have found some help at four other web sites - I'll not post the URL's just yet but I will after I've had time to fully evaluate the information. For the time being I'll say that I seem to have found some basic instructions about GRUB with enough explanation to help me understand each step in the boot process. I will be doing some trial applications of those instructions tonight so that I can learn what is needed (and why) to dual boot a system from the CLI. 

Best regards,  Ed B

---

### Post by shoot2kill on 2006-06-27
[QUOTE=Ed B]Thank you for your replies - I appreciate your interest in helping me.

**bobby19**
I'll try your suggestion tonight and will post the result.

**rai4shu2**
   *"How many systems are you trying to run there?"*
On that particular HDD I have two - Win95 and hopefully Kubuntu 6.06.

**falcon15500**
I think you are right about GRUB not finding the latter stages, and I've never seen a menu displayed.
I am uncertain about where I put the boot files, I know where I meant to install them but may have put them elsewhere.
I plan to delete all the current partitions and do another install - I'll make certain of the location then.
I actually have five HDD's in all, but I have had only one connected when trying to install Ubuntu - with Win95 on (hd0.0) and Ubuntu on (hd0,1) and I do plan on dual booting.

**To all:**
Things are looking extremely more promising than when I began this thread - I have found some help at four other web sites - I'll not post the URL's just yet but I will after I've had time to fully evaluate the information. For the time being I'll say that I seem to have found some basic instructions about GRUB with enough explanation to help me understand each step in the boot process. I will be doing some trial applications of those instructions tonight so that I can learn what is needed (and why) to dual boot a system from the CLI. 

Best regards,  Ed B[/QUOTE]

is win95 and ubuntu on same partition on the HDD, or different partitions...?

---

### Post by drtvasudevan on 2006-06-27
better to read up a little more before reinstalation.
one can put the grub in the mbr (always in the first hard disk) or in the partition where you install ubuntu, if you are using alternate cd.
in which case you should install a third party boot loader to boot.
if you are doing anything other than the default settings offered remember to note them down. like where you put the boot files.

tv

---

### Post by Ed B on 2006-06-27
[QUOTE=shoot2kill]is win95 and ubuntu on same partition on the HDD, or different partitions...?[/QUOTE]

They are on separate partitions - with Win95 on (hd0.0) and Ubuntu on (hd0,1)

---

### Post by Apple 101 on 2006-06-27
Windows 95? Is that release 2?  Anyway, someone pleae confirm this, but wouldn't you need to use LILO for Windows 95?

---

### Post by Ed B on 2006-06-27
[QUOTE=drtvasudevan]better to read up a little more before reinstalation.
one can put the grub in the mbr (always in the first hard disk) or in the partition where you install ubuntu, if you are using alternate cd.
in which case you should install a third party boot loader to boot.
if you are doing anything other than the default settings offered remember to note them down. like where you put the boot files.

tv[/QUOTE]

I agree and have been reading more. The more I read the more the fog lifts and other bits of information are revealed.

I think I will put grub in the MBR - might have to use fdisk to write a clean MBR and then install grub in it.

Ed B

---

### Post by shoot2kill on 2006-06-27
just a quick n00b question

what is MBR?

---

### Post by Apple 101 on 2006-06-27
MBR stands for Master Boot Record.  It is the part of the bootup process that contains information on which operating system to activate.

---

### Post by erniewinner on 2006-06-27
its worth it when you get it booted especially if you only have windows 95... i have one computer that doesn't like ubuntu. i just decided not to use it on that one. it's nice to have a range just incase... what kind of spec have you got on that machine? you need around 128mb ram you know. anyway good luck.

---

### Post by Ed B on 2006-09-08
I have redirected my efforts from dual booting Kubuntu 6.06 and Windows 95. I have installed a different HD and have installed Kubuntu on it as the only system on that disk.  I did this thinking that it should simpler to get it to boot with only one OS.

Sad to say, but I'm still stuck at the grub> prompt.  :cry: 

I have learned a little more since my last post. Tonight I found the thread at [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) , and based upon those instructions I booted the live CD and opened a terminal and entered 'sudo grub' to learn the following:
     Each of the following queries returned (hd0,0)
     > find /boot/grub/stage1
     > find /boot/grub/stage2 
     > find /boot/grub/menu.lst
     > find /vmlinuz
     > find /boot/vmlinuz-2.6.15-26-386 
     > find /boot/initrd.img-2.6.15-26-386

Based on that information, I closed the live session and rebooted to the grub> prompt and entered the following before trying to boot from the grub> prompt.
     > root (hd0,0)
     > setup (hd0)  [This installed grub on the MBR]

I still don't know what to do with the information I've gained :? , but I'm hoping that someone will be able to use it and provide me with the answer  I need to get this system to boot.

I'll greatly appreciate any help you can give.

---

### Post by jimmygoon on 2006-09-08
> **Ed B said:**
> I have redirected my efforts from dual booting Kubuntu 6.06 and Windows 95. I have installed a different HD and have installed Kubuntu on it as the only system on that disk.  I did this thinking that it should simpler to get it to boot with only one OS.

Sad to say, but I'm still stuck at the grub> prompt.  :cry: 

I have learned a little more since my last post. Tonight I found the thread at [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) , and based upon those instructions I booted the live CD and opened a terminal and entered 'sudo grub' to learn the following:
     Each of the following queries returned (hd0,0)
     > find /boot/grub/stage1
     > find /boot/grub/stage2 
     > find /boot/grub/menu.lst
     > find /vmlinuz
     > find /boot/vmlinuz-2.6.15-26-386 
     > find /boot/initrd.img-2.6.15-26-386

Based on that information, I closed the live session and rebooted to the grub> prompt and entered the following before exiting the terminal.
     > root (hd0,0)
     > setup (hd0)  [This installed grub on the MBR]

I still don't know what to do with the information I've gained :? , but I'm hoping that someone will be able to use it and provide me with the answer  I need to get this system to boot.

I'll greatly appreciate any help you can give.


Is it possible that your BIOS is preventing it from being written or read? Does it have a "MBR - Virus Protection" feature? DISABLE IT if it does...

Thats the only thing I can think of to be honest tho...

---

### Post by Ed B on 2006-09-08
Thanks, but I don't know if the BIOS is preventing being written to or read, and I do not have a MBR-Virus Protection feature.

But, I have learned a little more at [http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli) 

I opened a terminal in a live session and entered 'sudo grub' to get a grub prompt.

Then I entered the following commands, the response is under the command:
grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub> kernel /vmlinuz root=(/dev/hd0,0)
   [Linux-bzImage, setup=0x1c00, size=0x15787d]

grub> initrd /boot/initrd.img-2.6.15-26-386

Error 16: Inconsistent filesystem structure

I think I am within one or two steps of getting this OS to boot - - -
OH, if I only knew what they are!

I'm going to sleep on this til tomorrow - maybe the missing elements will be more obvious then.

---

### Post by bodhi.zazen on 2006-09-08
Not sure if I am following this thread, perhaps I can help.

At the grup prompt:

```
root=(hd0,0)
setup hd0
```

Should set up grub to boot from hd, you may have to edit /boot/grub/menu.lst since you moved the hd. To do this, boot from grub prompt and edit from Ubuntu or boot from cd and edit.

If you want to boot from the grub prompt:
```
root=(hd0,0)
kernel=/boot/vmlinuz root=/dev/hda1 ro
initrd=/boot/initrd.img-2.6.15-26-386
boot
```

Also grub uses tab completin. Use the tab key to show options and complete the #'s

ie type kernel=/boot/vml <Tab Key> and grub will fill in vmlinux-x.y.z

---

### Post by Cynical on 2006-09-08
Why is your root partition formatted as ext2? 

I think you should reinstall the os with this partitioning scheme.

Create 3 partitions, one 512mb linux-swap partition, one 8GB jfs partition (mounted to /), and a final jfs partition with all of the free space you have left (mounted to /home)

I think this is a configuration issue, following the above scheme and installing grub to the MBR will fix it.

---

### Post by Ed B on 2006-09-08
> **Cynical said:**
> Why is your root partition formatted as ext2? 

I think you should reinstall the os with this partitioning scheme.

Create 3 partitions, one 512mb linux-swap partition, one 8GB jfs partition (mounted to /), and a final jfs partition with all of the free space you have left (mounted to /home)

I think this is a configuration issue, following the above scheme and installing grub to the MBR will fix it.

I may have missed an opportunity to choose another format, but I believe there was no other. My system is Pentium 2, 266, 256 MB RAM, with Win-95-b as the previous OS.

What determines which fs I should/can use?

I'm not opposed to installing again using the options you suggest - just trying to understand a little more.

---

### Post by rahelvey on 2006-09-08
Just a thought here.
Try xubuntu.
I could not get ubuntu on my laptop 233 p11. 
Try to use the older system at first run on the cd.
Just food for thought.

---

### Post by Ed B on 2006-09-08
> **rahelvey said:**
> Just a thought here.
Try xubuntu.
I could not get ubuntu on my laptop 233 p11. 
Try to use the older system at first run on the cd.
Just food for thought.

I might as well, it and edubuntu are the only ones I haven't tried. [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

The live cds run on my system without a hitch. Even so, I guess it is still possible that they might not when they are installed.

I think I will try LILO before I replace the entire system. Can't lose much except the time to install & configure it.

---

### Post by Ed B on 2006-09-10
> **rahelvey said:**
> Just a thought here.
Try xubuntu.


Success at last!!!  :D 
Thank you rahelvy!!!   =D>

Xubuntu installed without a hitch and gave me the option to save the session and it rebooted in the Grub graphic menu. When I entered my user name and password - the boot process finished and I was working with an installed xubuntu OS.  :-\" 

With the working OS I can now add KDE and other components I want.  :-D

---

### Post by YeahBuntu on 2006-09-10
You may want to try and grab a copy of Gwscan... check the drive for errors and then write zeros to the drive if you want to do a true clean install.

---

