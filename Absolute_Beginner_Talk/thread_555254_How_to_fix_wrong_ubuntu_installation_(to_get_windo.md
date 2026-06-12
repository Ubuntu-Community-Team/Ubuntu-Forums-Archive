---
title: "How to fix wrong ubuntu installation (to get windows working)?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by mr. paperbox on 2007-09-19
HI!

I made terrible mistake, I installed Ubuntu with wrong settings, and now I can't get to windows!
I used "Guided - use entire disk"-setting to my external hard drive, when I still have windows in my main drive. Now when starting computer without my external drive, it gives me "GRUB error 21".
 I really have no idea what to do, cause this is my first time with linux and this kind of stuff.

Now what can I do to get windows working normally?

---

### Post by mr. paperbox on 2007-09-19
I Found this tutorial, but I wonder if thats the right thing to do on my situation? [https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

Plz I need quick help, so I can get some sleep,,,

---

### Post by rsambuca on 2007-09-19
If you aren't going to have the external drive connected all of the time then you need to use your XP installation discs to run the "fixmbr" command.  If you boot with the external drive connected, you should be fine until then.

---

### Post by mr. paperbox on 2007-09-19
well, the problem is that I dont have cd with me right now, so I need to do something else...
But could that link work? Or is there some else way?

And nope, I will not use this external drive with this comp anymore..

---

### Post by rsambuca on 2007-09-19
Doesn't it work when the external drive is connected?

---

### Post by mr. paperbox on 2007-09-19
When external drive is connected, it automatically boots ubuntu, so I can't go windows anymore.

---

### Post by rsambuca on 2007-09-19
Is this actually your computer?

In any event, if you follow the instructions at the top of [this thread]("http://ubuntuforums.org/showpost.php?p=3075438&postcount=1"), you should be fine.

---

### Post by mr. paperbox on 2007-09-19
thx, i'll try,... and no, this is not my computer,. What I tried, was to install ubuntu just to the external drive so I could use it where-ever. But I got permission to try this :p

---

### Post by mr. paperbox on 2007-09-19
I tried that second part of that link as it says. I tried this one, beacause I couldn't try that first part, of that tuto, because I can't go to windows.


------------------------------------------------------starts--------------------------------------------------
Re: HowTo: Remove Ubuntu (& Restore Windows)

--------------------------------------------------------------------------------

If you delete the ubuntu partitions without running mbrfix then you can use the ubuntu LiveCD to restore the master boot record by:

1. Booting from the ubuntu LiveCD
2. Enabling universe repositories - launch System->Administation->Software Sources and check the "Community maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click Applications->Accessories->Terminal and type "sudo apt-get update" and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose Windows master boot record you want to restore. You can find out which this is by launching gparted (System->Administration->GNOME Partition Editor) and cycling through the available drives until you find your Windows partition

- - - - -

Hope this helps, and please let me know if anyone finds any errors. Also, for anyone using this post, "we" really hope you will come back to Ubuntu someday! Linux, and Ubuntu, will be waiting!

============================

Trouble shooting:

If, after following this guide, you can not boot to Windows you may need to boot a live CD and manually delete the Ubuntu partition (making it unpartitioned space, adding it to the Windows partition, or formatting it to FAT/NTFS). Additionally you need to be sure the MBR is set for Windows. You will need to search the forums for more help on that. In addition, the following Microsoft articles may be of help:

-------------------------------------------------------ends--------------------------------------------------------


But, when I then boot my comp, it still needs my external drive to be connected. Then when I connected it, there came up that I could choose what I wanted to boot, but when I chose Windows xp, it gave me an error and said "wrong disk" or something like that? If that means to put in windows cd, thats problam cause I don't have it...

Should I delete my ubuntu partitions from my external drive or what?

Plz help me... It still needs external drive, if its not on, it gives me that GRUB-error...

Any Ideas anyone?

---

