---
title: "Dual Boot question Windows XP and Ubuntu 6.10"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by chivaago on 2006-11-30
I've had this Dimension 3000 with WindowsXPHome on it for a little over a year now. That is my total experience with computers. I had installed 5.10 but was somewhat overwhelmed with the learning curve. But I'm just drawn to
the ideas and ideals behind Linux and I've stepped off into the deep end.

By that I mean I installed 6.10 and can't seem to get the dual boot thing-a-ma-jig to work and I don't even know what question to ask to solve
the problem.

Here's the poop: Acronis True Image 10 and Disk Director Suite installed which has a mechanism call OS Selector. When I powered on the computer first screen would be Dell's  then Acronis' OS Selector screen would materialize with 3 choices XP, XP(1), and Acronis Secure Zone 
(which houses the image of my C:drive). 
Now when I power on it goes directly to Ubuntu with no other choices.
Oh, and I tried to install Ubuntu on my slave. I do not know if I accomplished it. 


I've read through the documentation about dual booting Windows (once)
and I'm sure given a couple of months I could figure it out, but I was 
 hoping someone point me in the right direction (maybe even guide me through the steps?), just this once. I know i should have done my homework
first:rolleyes: 

I know how to copy and paste.

---

### Post by nickburns on 2006-11-30
I am a new user too, the best way to get into Ubuntu is by jumping in with both feet.  I found it easier to understand as my main OS, but your opion may be different.  

Either way I would recommend that you either:

1.  Install Ubuntu as you main OS, and user vmware for windows
(vmware here -- [http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209))

2.  Install vmware on you windows machine and load up Ubuntu on vmware.


Option 1 will be a big commitment to switch to Ubuntu, but you'll love it.

Option 2 will allow you to ditch Ubuntu without worries about the windows partion.

---

### Post by chivaago on 2006-11-30
>I agree, jumping in with both feet is the best way for me to learn.
> But I have all of this "windows stuff" apps, programs, and 
>there are others that depend on me (unfortunate for them sometimes)
>for answers to their windows questions and I need some of the stuff 
>that I can't get to without being able to -say-for the next week 
>totally immersing myself in Linux,
>(you know the time thing). 

>I just ordered from Amazon the Linux Cookbook 2nd ed., 
>but that won't get here before the beginning of the week. 

>If I had the time to do nothing but Linux for the next 24/8,
> I'm pretty sure I could figure out exactly 
>what happened to cause the Master Boot Record to only see Ubuntu - 
>and then I could be on the wrong trail anyway. 
>That's why I would be very interested in what a dual boot artist 
>would have to say about my predicament.
                                    
>Oh and the reason I didn't post this in another forum,
>I know absolutely nothing about command line, scripts, 
>grubs Master Boot Records. I can't believe how little I learned 
>in this past year letting Microsoft do all my thinking.

---

### Post by joshuapurcell on 2006-11-30
Hopefully you haven't done any customization in any of the OS environments up to this point, so that reinstalling won't cause any data loss. The instructions I give below will erase *everything* on your hard drive and leave you with two brand new operating systems. If this isn't what you want to do then stop reading now.

Do you need to keep the Acronis Boot Manager? I would personally get rid of that since Grub (Linux's boot loader) can handle getting into any OS you install. I would reinstall everything by putting your Windows CD in the computer, and choose to delete all partitions when it comes to that section, then press c to create a new partition. Make this partition only as big as you need it for Windows... somewhere between 10GB and half of your total hard drive space. Once Windows is installed on this partition, then you can boot into Windows to ensure functionality, then pop out the Windows CD and restart with the Ubuntu CD in the drive.

If you are using the alternate CD (which may be easiest in this scenario), then choose the first option on the boot menu that appears which will take you directly into the hard drive installation. Once you get to the point where it ask where to install Ubuntu, you can choose the largest continuous unused region (which will be everything Windows didn't use). Answer the rest of the questions how you like and finish the install. One of the last questions that come up is about Grub. A question will ask something along the lines of "Are all other operating systems listed above?" If you see Windows listed on this screen, then Grub can safely be installed to the master boot record and you will get a boot menu with both Linux and Windows listed as options. Finish the install, and ask any other questions here if you have any.

---

### Post by chivaago on 2006-12-01
> **joshuapurcell said:**
> 

Do you need to keep the Acronis Boot Manager? I would personally get rid of that since Grub (Linux's boot loader) can handle getting into any OS you install. I would reinstall everything by putting your Windows CD in the computer, and choose to delete all partitions when it comes to that section, then press c to create a new partition. Make this partition only as big as you need it for Windows... somewhere between 10GB and half of your total hard drive space. Once Windows is installed on this partition, then you can boot into Windows to ensure functionality, then pop out the Windows CD and restart with the Ubuntu CD in the drive.

If you are using the alternate CD (which may be easiest in this scenario), then choose the first option on the boot menu that appears which will take you directly into the hard drive installation. Once you get to the point where it ask where to install Ubuntu, you can choose the largest continuous unused region (which will be everything Windows didn't use). Answer the rest of the questions how you like and finish the install. One of the last questions that come up is about Grub. A question will ask something along the lines of "Are all other operating systems listed above?" If you see Windows listed on this screen, then Grub can safely be installed to the master boot record and you will get a boot menu with both Linux and Windows listed as options. Finish the install, and ask any other questions here if you have any.




No I don't need to keep Acronis. Like a hot potatoe.

I don't have the alternate cd so I'm going to follow your first suggestion.
I'll post how it goes.

Thanks

---

### Post by chivaago on 2006-12-02
joshuapurcell,

Hey!

I followed your instructions and I now have both Windows XP and Ubuntu on drv/0. When I power on I get a screen that asks me which OS I would like
to boot.  When I boot into Windows, all goes well (except for the fact I don't have 10/100 drivers and cannot access the net) but, when I try to boot into Ubuntu (at this moment running in CD mode) I get:

May lie only with the primary block group descriptors, and backup may 
be okay

dev/hdb1: Inode bitmap forgroup 384 is not in a group

dev/hdb1: Unecpected Inconsistancy: run fsck manually i.e., without -a or
-p options

fsck died with exit status 4

filesystem check failed *

A log is being saved var/log/fsck/checkfs 

Please repair the file manually
* A maintenance shel will now be started
Control D will terminate this shell and resume system boot

bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: dircolors: command not found

root@ chivaago desktop:~#[17179591 and the screen started scrolling here.

can this be fixed (is it possible for me to fix this)? or do I have to un/
reinstall? 

I'm farther along following your instructs than before. What is really great (and kind of unnerving at the same time) is that I can run Live CD
and access all of my files without using my password.

---

### Post by nickburns on 2006-12-02
Confused by the 'Running on CD mode'  did you install Ubuntu to the HD or are you running on the live CD?

---

### Post by Chinkostu on 2006-12-03
his HDD install hangs. he's typing this in the live cd as he's lost ethernet in windows :(

---

### Post by chivaago on 2006-12-03
what he said.

---

### Post by gitano1 on 2006-12-03
I am currently running Ubuntu 6.10 on my machine in a dual boot conformation with two hard drives. The main drive is running WinXPHome. The system runs impeccably. I am on Ubuntu most of the time. I use Windows only when I am doing DVD backups since the decrypting software is really the hegemony of Windows. I am tech supervisor in my school building, so I have experimented with installing Ubuntu on a number of machines, mostly Dells. I have probably done 8 successful installations so far.
What I have found is that Windows doesn't like sharing a hard drive with anything. 1-All attempts to put Ubuntu on a Windows drive have met with failure. 2- Using a second, slave drive, for Ubuntu works best. 3- Installing Edgy Eft 6.10 is much harder than installing Dapper Drake. 4- The best procedure is to install Dapper Drake first and then upgrade to 6.10. 
I am sure that there are ways of making Ubuntu function on the same drive with Windows, but it is an installation fraught with pitfalls and problems that a newby who just wants to learn how to use Linux does not need to experience. I am also sure that installing 6.10 from the CD is possible, but it also is more likely to be problematic than using the proven earlier edition to set up Grub and other parts of the installation which are a problem with 6.10. 
Anyway, my recommendation to anyone just starting out is to install 6.06 first, then upgrade to 6.10 which is really a lovely upgrade. If you are going to do a dual boot system use a second, slave drive for Ubuntu. And, finally, if there isn't any driving need to use Windows once you have gotten your Ubuntu up and running make your life simple by reformatting your Windows hard drive and install Linux on it. To my way of thinking there is simply no reason to support the bloated, corrupt, dysfunctional Microsoft empire. The longer I use OSX and Ubuntu the less I tolerance I find for the incompetence of Microsoft engineers and their overweaning desire to dominate a market in which they will always be a distant third.:biggrin:

---

### Post by flash2lightning on 2006-12-03
I have a Dimension 3000 running both winXP and 6.10 (recently upgraded from 6.06) running both on the same hd, but partioned, and everything works fine. I set everything up with no experience with partioning but i got it to work.

---

### Post by chivaago on 2006-12-04
gitano1

>Thankyou for this information. For other reasons than what you gave
 
>I wanted to install Ubuntu on the secondary drive but what I wrote earlier
 
>is what happened to that installaton effort.  I have just finished

>reinstalling XP and Ubuntu on the primary drive after reformatting the 

>primary to look something like this:

XP------|NTFS-|____________________FAT32_________________|-|-UBUNTU-----|

>This time it gave me a choice of which operating system I wanted to boot 

>into and it worked. BUT that's not to say that everything is working a-ok. 

>As I work through this a post and try to be as clear as I can

>(seems like when I finally have some information to post;

>I'm so dead tired I can't see straight). 

>I do have a copy of dapper and tomorrow I'm going to try to install it on

>the second drive.

>Again, I appreciate your insight on this. 

>Now I have to figure out how to download ethernet drivers with Ubuntu and 

>get them loaded into XP.

---

### Post by Atomic Dog on 2006-12-04
I have a HP laptop that has not only a recovery partition (ick) but also this useless dvdplayer boot (which is nothing more than a stripped xp install with a full screened player -only 1 gig though).  Grub allows me to boot into any of these along with Ubuntu.  It's a wonderful thing.

I used hirens boot cd (google it) to fire up partition magic and shrank my partitions way down to size to make room for a big fat ubuntu install.

---

### Post by lucky_chouhan on 2006-12-04
first i am installed windows xp C:\
second i am installed windows 2003 d:\
then i install Ubuntu 6 with Ubuntu Grub

i have this menu by Ubuntu Grub)

Ubuntu
Ubuntu Recovery
Windows OS - Windows Xp
             Windows 2003

---

