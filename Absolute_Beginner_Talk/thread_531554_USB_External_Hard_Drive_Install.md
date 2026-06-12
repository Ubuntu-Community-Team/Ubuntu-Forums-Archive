---
title: "USB External Hard Drive Install"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-08-21
Hello,

Ive seen lots of posts here about installing on external HDs but I was wondering if you could simply use the installer on the Live CD (of either 7.04 or 6.10) to install to external. Do you also have to pre partition the drive or will the installation tool perform that for you?

thanks in advance

---

### Post by MQMike on 2007-08-21
I just did this.

Used the regular Desktop Live CD installer, the manual partitioning option, in Step 6, see the Advanced button at lower right, behind that specify to put GRUB into the MBR of the  USB drive, set your BIOS to boot from USB, and so on.

I wrote it up as a How To at:

How To Make GRUB Thumb Drive
[http://kubuntuforums.net/forums/index.php?topic=3081748.0](http://kubuntuforums.net/forums/index.php?topic=3081748.0)
How to install K/Ubuntu 7.04 to an external USB hard disk drive (HDD). 
(Scroll to the second post, August 14, 2007.)

*** Your BIOS must support USB booting. ***

I’m not the expert, but read it, try it, and write back if you have problems – I or someone can help.

(Also see the GRUB references under the first post there.)

---

### Post by MQMike on 2007-08-21
Oh, yes, and I pre-patitioned with GParted Live, but you might get away with using the partitioner with the installer.  I feel better and more relaxed if I do it ahead of time in GParted; easier to delete and repeat if I make mistakes or change my plan.  I explain it in my How-To.

---

### Post by Ek0nomik on 2007-08-21
> **JasonBourneLinux said:**
> Hello,

Ive seen lots of posts here about installing on external HDs but I was wondering if you could simply use the installer on the Live CD (of either 7.04 or 6.10) to install to external. Do you also have to pre partition the drive or will the installation tool perform that for you?

thanks in advance

When you open the partition editor (GParted) in the Live CD you can format the external hard disk.

---

### Post by JasonBourneLinux on 2007-08-21
thanks for the advice!

---

### Post by Ek0nomik on 2007-08-21
> **JasonBourneLinux said:**
> thanks for the advice!

No problem.  If you run into any problems just reply to this thread and I will check back.

---

### Post by Deived on 2007-08-21
Ive been running on an external for a while now (before I leave WinXP behind).  You can easily install to an external drive from the Live CD.  2 things to note though....

1- When you get near the end, there is an 'ADVANCED' button.  Click this and there is an area where you specify where to install GRUB.  Don't install GRUB on your main drive which it defaults to (hd0,0).  Change this to your external which is probably hd1,0 if you have no other drives.  Otherwise if you boot with the external not plugged in, it wont let you get into Windows (at least that's what I've experienced).

2- When you boot the the external and get to GRUB, Ubuntu may not launch if GRUB is still pointing to the external at hd1,0.  You'll get some destination error.  Edit the line (press 'e' to edit) and change it from hd1,0 to hd0,0 (since your booted to the external, it now sees this drive as hd0,0).  Once your in Ubuntu you'll want to change your GRUB menu to have Ubuntu pointed to hd0,0.  I believe it's at /boot/grub/menu.lst.  You'll need to be root or use sudo to edit it.

Hope I made sense.  I'm at work so needed to be quick.

---

### Post by MQMike on 2007-08-21
Exactly as Deived says.  My experience, too.  See that How-To for the verbosity.

---

### Post by ArtF10 on 2007-08-21
Why would one want to boot from an external USB drive?  I;m not trying to be rude or arrogant but if you only plan on using Ubuntu on your desktop/laptop computer, why not just use the system's hard disk?

Or is this a way to install multiple Linux distros on the same system?

---

### Post by JasonBourneLinux on 2007-08-21
well, Im using Ubuntu as a backup tool- my windows is getting unstable so I want to slip Ubuntu on something external with my files on it so if Windows corrupts over, I simply plug in my external and keep working (its pretty busy during school year)- plus I can use it on multiple computers and give it to buds if Windows decides to take a vacation ^_^

---

### Post by ArtF10 on 2007-08-21
What's the speed like when runing off the USB drive?  And how do you handle graphics cards on different computers?  Do you have to install different drivers for the razmahtaz effects..."desktop effects"?

---

### Post by Ek0nomik on 2007-08-21
> **ArtF10 said:**
> What's the speed like when runing off the USB drive?  And how do you handle graphics cards on different computers?  Do you have to install different drivers for the razmahtaz effects..."desktop effects"?

If you boot Ubuntu under another video card you will probably have to reconfigure your xorg.conf file from the command line.

---

### Post by Rajan Varadarajan on 2007-08-22
I have a Toshiba Satellite M45-S331 laptop (centrino mobile processor, wireless enabled, built-in video, 512 MB RAM, 80 gb hard drive). It has XP Pro installed and I do database development work. Checked the BIOS of this laptop and it does NOT have an option to boot from USB but only an option to boot from external devices possibly a bios relic from floppy drive days. All the thread discussions here assume USB BIOS booting option.

I would like to run ubuntu on this laptop from an external USB hard drive - something like a western digital passport drive (one of those pocket sized portable drives - now they have gone up to 250 gb!). I DO NOT want to touch the XP Pro at all and want to run ubuntu completely from outside and thank you all in advance for your help and suggestions. I already run ubuntu on a dedicated e-machines pentium 1.5GHz desktop without any problems.

1. My preferred option is to run from a USB hard drive.
2. If this is not possible, is there a scenario where I could burn a bootable CD and run ubuntu from it and using the pocket USB drive for both data files as well as all other utilities?

Rajan Varadarajan
[email]rajanv1@msn.com[/email]
Still a ubuntu newbie!!

+++++ March 26, 2008 update ++++++++++++++
Finally, I got a nice Western Digital 250GB Passport External USB Drive. This gadget is amazing. Anyway, for two straight days I have tried to install ubuntu on this external drive. I started ubuntu 7.04 with a Live CD and then selected Install. The partition screen did offer me the chance of partitioning the external hard drive; the drive was identified as "sdb" (may be because it was Live CD). Two more screens forward - GRUB install screen came up. I chose Advanced and selected bootloaded to be installed on the external drive as well. Boom! ubuntu went in circles going back to partition screen many times. Finally, I quit out of frustration.

Any ideas would be appreciated. I hope 8.04 will have better installers. It is important to note that my BIOS doesn't have USB boot option. I have read through all the workarounds mentioned in the forums. All of them are quite complex and you make one little typing mistake somewhere and you are back at the beginning:-) I am not a novice (database applications developer on Windows), but still the rigamarole is daunting!!

---

### Post by MQMike on 2007-08-22
Hi Rajan,

I haven’t tried it, but ran into two references re USB booting on BIOSs that don’t support such.

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
The opening paragraph:
“If you want to install Ubuntu onto a USB drive, such as a large "USB stick" or an external hard drive it is often impossible to boot this system on slightly older computers. This guide explains how to create a bootable CD which will load the USB system.”
Their solution:  To build a bootable CD that boots the USB drive.
Here’s a recent case:
Case:  [http://ubuntuforums.org/showthread.php?t=506179](http://ubuntuforums.org/showthread.php?t=506179)
[http://ubuntuforums.org/showthread.php?t=80811&highlight=Success+breezy+booted+from+USB+grub](http://ubuntuforums.org/showthread.php?t=80811&highlight=Success+breezy+booted+from+USB+grub)


And another, where the author puts Ubuntu of a UFD (USB flash drive):
USB UFD booting, Feisty on:
[http://ubuntuforums.org/showthread.php?t=80811&highlight=Success+breezy+booted+from+USB+grubFirefoxHTML\Shell\Open\Command](http://ubuntuforums.org/showthread.php?t=80811&highlight=Success+breezy+booted+from+USB+grubFirefoxHTML\Shell\Open\Command)


And, you also said:
“2. If this is not possible, is there a scenario where I could burn a bootable CD and run ubuntu from it and using the pocket USB drive for both data files as well as all other utilities?”

When the Ubuntu is running from the Live Ubuntu CD, you would have to mount the USB drive (or make sure it is mounted automatically by Ubuntu), and then write your data to it.  So your Live CD is running and your USB drive connected to a USB port on your PC.  Now, the question is, will your laptop detect the attached USB drive?  I don’t see why not, right?  People do use their UFDs and external USB HDDs all the time, even when their BIOSs might not have the capability of USB booting.
Also, when running from a Live CD, it is a common task to access other storage media (like HDDs) on the machine and write to them or modify files, so, again, I don’t see why your second option would not work.

As you might surmise, I am not the expert – only an expert at what actually worked for me on my system (see the UFD link on page 1)  :)

If you do this successfully, either way, I think lots of people would like to hear about your experience with it.

--Mike

---

