---
title: "Cannot get GRUB working"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Mr_Threepwood on 2007-10-22
Hello, I know that problems with GRUB are common, and I have searched around to try and solve this but I can't seem to get it working right.

Hard drives:

Drive 1 
( 2x raid 0 array), is labelled drive C from windows xp and has the OS installed on it

Drive 2
Single hard drive that has been partitioned into 3, drive D used by windows, an ext3 Linux partition, and a Linux swap partition

So I originally had Windows as the sole OS, and repartitioned the second drive as mentioned above so that I could install Ubuntu.  I got through the Ubuntu install fairly painlessly, and it did grub onto the default (hd0).

Upon rebooting it gave me a Grub error 21, so I googled that and it looks like that means it couldn't find any OS's.  So then I just put in the XP disc and restored my MBR, this obviously isn't ideal since I can't get into Linux.

After more googling and trying semi random steps I came across:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I followed the directions there up to where catlett said "setup (hd0)", and at this point I tried putting in the same thing as what was returned to me from doing "find /boot/grub/stage1", since I figured that it originally had problems installing on hd0, so I should try something else.  This was wrong since I guess it means I installed grub onto a partition, so it doesn't get checked or something.


My questions are:

1.  Is it possible that the process of me doing the grub reinstall with something other than (hd0) messed up stuff?  (I think I tried "setup (hd0,2)")

2.  How do I actually tell what the numbering of hard drives refers to, I'm relatively new to linux and other than navigation and the basics I'm totally lost.  I have no idea which hard drive hd0 or hd1 refers to.

3.  Is the only way to get GRUB working right to install it to the MBR?

4.  Does using the windows MBR repair mess up anything with the Linux install, or am I still ok if I can figure out how to get GRUB working right?

---

### Post by mikeyphi on 2007-10-22
> **Mr_Threepwood said:**
> 

My questions are:

1.  Is it possible that the process of me doing the grub reinstall with something other than (hd0) messed up stuff?  (I think I tried "setup (hd0,2)")

2.  How do I actually tell what the numbering of hard drives refers to, I'm relatively new to linux and other than navigation and the basics I'm totally lost.  I have no idea which hard drive hd0 or hd1 refers to.

3.  Is the only way to get GRUB working right to install it to the MBR?

4.  Does using the windows MBR repair mess up anything with the Linux install, or am I still ok if I can figure out how to get GRUB working right?

1. Yes!

2. This can be confusing since Grub uses the drive called hd1 as (hd0). If interested read more here: [http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/) 

3. Probably not BUT the MBR is generally where the BIOS looks for startup info; In Ubuntu  the MBR points to where Grub info is to be found. (usually /boot/grub/menu.lst)

4. If you use a Windows disc to 'repair' the MBR you will not be able to see Grub and therefore will not be able to boot into Ubuntu!

I know that there are some issues with RAID - you probably need to look into that first: [https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)  - but you should be able to get Grub installed and working. You will have to use the LiveCD and reinstall Grub - again!!

---

### Post by Mr_Threepwood on 2007-10-22
OK so I've tried doing that setup stuff again using hd0, and it does absolutely nothing (still causes me to boot into windows).  So now I'm thinking that the HD i should be putting in there is 1.

When I do the command to find the root it returns hd0,2 which I'm guessing is the second (or third, but second would make more sense with the setup that I have) partition of my secondary hard drive.  I've done the commands like "setup" and "root" several times though with different paramaters, I really hope that doesn't mess stuff up (hopefully each time you type it with new parameters it resets it, rather than adding a new one or something).

The RAID that I have is a hardware raid (controlled by the motherboard) so hopefully it's treated as a regular drive (hd1 I hope), because if it's treating the raided drives as two seperate ones then I'm sure that will cause lots of problems.

---

### Post by Mr_Threepwood on 2007-10-22
OK so now I'm even more confused.

I was just trying stuff so eventually I ended up having done setup hd0 and hd1  (hd1 has windows on it as far as I know).

Now if I try to boot off of hd0 it goes directly into ubuntu.  If I try to boot off hd1 I get the grub list, but it doesn't have windows on it and if I try to boot into any of the options I get error 22.

Anyone know what to do, I really want to be able to get into Windows as well as Ubuntu (I know I can use windows recovery CD, but that will make getting into ubuntu impossible).

---

